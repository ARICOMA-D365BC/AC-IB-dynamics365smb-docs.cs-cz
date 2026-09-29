---
title: EDI Connector
description: EDI Connector
author: kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, EDI Connector, additional functions
ms.author: v-jurxova
---
# EDI konektor základ

Add-on modul **EDI konektor základ** přidává do systému Microsoft Dynamics 365 Business Central rámec pro elektronickou výměnu dokladů (EDI) s obchodními partnery – zákazníky, dodavateli a přepravci. Modul sám o sobě neobsahuje konkrétní formát zprávy; je to obecný rámec, který pro každou kombinaci *partner – doklad – směr komunikace* spustí přiřazený objekt (report, codeunit nebo XMLport), který vytvoří nebo načte datovou zprávu v podobě požadované daným EDI providerem.

Modul zajišťuje zejména:

- evidenci EDI partnerů a jejich EAN (GLN) identifikátorů,
- nastavení karet EDI komunikace, které říká, co, komu, jakým objektem a kam se posílá,
- sledování stavu zpracování dokladu prostřednictvím **Položek EDI** a **Detailních položek EDI**, včetně archivace vlastní zprávy,
- napojení na modul **Spooler**, který obstarává vlastní přenos zpráv k providerovi (HTTP, webová služba, API, e-mail).

EDI konektor základ je především o správném nastavení. Bez vyplněné karty **Nastavení EDI** se zaškrtnutým polem **Povoleno** funkce modulu nelze spustit – systém ohlásí, že funkčnost EDI konektoru není povolena.

## Jaké doklady EDI podporuje

Modul pracuje s těmito zdrojovými doklady (pole **Typ zdroje dokladu** na kartě EDI komunikace):

| Tabulka | Doklad | Typ zdroje | Obvyklý směr |
|---|---|---|---|
| 36 | Prodejní hlavička (nabídka, objednávka, faktura, dobropis, hromadná objednávka, objednávka vratky) | Zákazník | Import |
| 38 | Nákupní hlavička (nabídka, objednávka, faktura, dobropis, hromadná objednávka, objednávka vratky) | Dodavatel | Export |
| 110 | Prodejní dodávka (účtovaná) | Zákazník | Export |
| 112 | Prodejní faktura (účtovaná) | Zákazník | Export |
| 114 | Prodejní dobropis (účtovaný) | Zákazník | Export |
| 5740 | Hlavička transferu | Přepravce | Export |

Směr komunikace se při volbě typu zdroje dokladu předvyplní automaticky: prodejní hlavička (36) se nastaví jako **Import**, ostatní doklady jako **Export**. Hodnotu lze následně změnit na **Export**, **Potvrzený export** nebo **Import**.

> [!NOTE]
> Volba **Potvrzený export** znamená, že se do exportu zahrnou pouze doklady, u nichž je zaškrtnuto pole **Potvrzeno pro EDI export**. Při volbě **Export** se filtr na toto pole nepoužije.

## Jaké vznikají zprávy týkající se komunikace

Stav zpracování dokladu v EDI je veden v poli **Stav** na položkách EDI a odpovídá typu zprávy, která byla vyměněna:

| Stav | Význam |
|---|---|
| ORDERS | Objednávka (přijatá od zákazníka nebo odeslaná dodavateli) |
| DESADV | Avízo o odeslání (dodací list) |
| Dodáno/Přijato | Doklad byl expedován, resp. přijat |
| RECADV | Avízo o příjmu od partnera |
| DESADV stornováno | Storno avíza o odeslání (vzniká při odúčtování prodejní dodávky) |
| INVOIC | Faktura |
| COMDIS3 | Obchodní spor – podmínečně přijato |
| COMDIS1 | Obchodní spor – v pořádku |
| COMDIS8 | Obchodní spor – odmítnuto |
| INVOIC stornováno | Storno faktury |

Kromě stavu se u položek sleduje pole **Potvrzen příjem** s hodnotami *EDI prostředník* a *Obchod*, které rozlišuje, na jaké úrovni byla zpráva protistranou převzata.

Vlastní text vyměněné zprávy je uložen jako příloha podrobné položky EDI a lze jej kdykoli stáhnout akcí **Export dokument** na stránce **Detailní položky EDI**.

Chyby vzniklé při komunikaci se podle zvoleného způsobu přenosu zapisují:

- do **Protokolu EDI fakturace** – u fakturačních zpráv jsou zde texty chyb celé zprávy, číslo chybného řádku, kód a popis akce, číslo COMDIS zprávy a stav zprávy,
- do **Položek protokolu Spooleru** – u zpráv přenášených Spoolerem (chyby spojení, autentizace, odpovědi providera).

## Položky EDI a Detailní položky EDI

**Položka EDI** existuje právě jedna pro každou kombinaci zdrojové tabulky, podtypu a čísla dokladu a nese vždy aktuální (poslední) stav. **Detailní položka EDI** vzniká pro každou jednotlivou komunikaci a tvoří tak historii dokladu. Detailní položka navíc obsahuje číslo verze, počet výskytů čísla dokladu, číslo účtování, externí číslo dokladu, příznak stornování, směr, číslo záznamu v bufferu, jméno souboru a přílohu se zprávou.

Položky jsou provázané polem **Č. hlavní položky EDI**, takže lze zobrazit jak historii jednoho dokladu, tak historii celého řetězce navázaných dokladů (objednávka → dodávka → faktura).

## Použití EDI v prodeji

Prodejní strana je typicky obousměrná a probíhá v tomto sledu:

1. **Příjem objednávky (ORDERS).** Report **Importovat EDI doklady** projde aktivní karty EDI komunikace se směrem *Import* a pro každou z nich spustí přiřazený objekt, který vytvoří prodejní objednávku. Zboží se dohledává podle EAN z přijaté zprávy, EAN se zapíše do pole **EDI EAN** na prodejním řádku. Vznikne položka EDI se stavem *ORDERS*.
2. **Kontrola a zpracování objednávky.** Přehled všech EDI objednávek nabízí stránka **Přehled EDI - prodej**, kde jsou vedle standardních polí vidět i pole **Stav EDI**, **Potvrzen příjem EDI**, **Námitka s chybou**, **Potvrzeno k exportu EDI**, **Číslo faktury**, **Číslo dodávky EDI** a **Datum dodávky EDI**.
3. **Expedice a avízo o odeslání (DESADV).** Zaúčtováním dodávky se doklad automaticky označí jako potvrzený pro EDI export a vznikne položka EDI pro prodejní dodávku. Vlastní zprávu vytvoří report **Exportovat EDI doklady - dodávky**. Odúčtováním řádku prodejní dodávky se dodávka označí příznakem **EDI stornováno** a vznikne položka se stavem *DESADV stornováno*; pokud se odúčtovává jen část dodávky, systém na to upozorní dotazem.
4. **Fakturace (INVOIC).** Zaúčtováním faktury (resp. dobropisu) vznikne položka EDI pro účtovanou fakturu a zprávu vytvoří report **Exportovat EDI doklady faktury** (resp. **Exportovat EDI doklady dobropisy**).
5. **Storno faktury.** Funkce **Stornovat EDI fakturu** označí dosavadní detailní položky se stavem *INVOIC* jako stornované, založí položku se stavem *INVOIC stornováno*, zruší příznaky **Potvrzeno pro EDI export** a **Avízo s chybou** a uvolní případný zámek dokladu.

Před potvrzením dokladu pro EDI export systém kontroluje, že jsou vyplněna pole **Č. dodávky EDI** a **Datum dodávky EDI** a že všechny řádky typu *Zboží* mají expedované množství shodné s množstvím objednaným. Kontrolu stavu EDI a přijetí dat lze dále zpřísnit kontrolními řádky na kartě EDI komunikace.

Funkci potvrzení lze spustit i hromadně z **Přehled EDI - prodej** akcí **Potvrdit export faktury**, která doklad nejprve vydá a poté zaškrtne **Potvrzeno k exportu EDI**.

## Použití EDI v nákupu

Nákupní strana je typicky jednosměrná – odesílá se objednávka dodavateli:

1. Nákupní objednávku je nutné nejprve **vydat**.
2. Na kartě nákupní objednávky se spustí akce **EDI doklad**. Funkce ověří, že dodavatel má vyplněné **GLN** nebo **EAN pro EDI**, dohledá odpovídající kartu EDI komunikace (podle dodavatele a kódu adresy objednávky) a založí položku EDI se stavem *ORDERS*.
3. Vlastní zprávu vytvoří report **Exportovat EDI nákupní doklady**, který zpracuje pouze vydané objednávky, jejichž položka EDI je ve stavu prázdném nebo *ORDERS*.
4. Na kartě nákupní objednávky je stav komunikace vidět v poli **Stav EDI**.

Na nákupních řádcích je k dispozici pole **EDI EAN** a na hlavičce pole **Sloučit řádky podle EDI EAN**, které umožní shrnout více řádků se stejným EAN do jedné položky odesílané zprávy.

## Objednávky transferu

Pro přepravce (typ původu *Přepravce*) je určena Objednávka transferu (tabulka 5740) s polem **Potvrzeno pro EDI export** a report **Exportovat EDI doklady transferů**.

## Protokol EDI fakturace

Stránka **Protokol EDI fakturace** slouží jako kniha historie fakturačních zpráv. U každého záznamu je vidět číslo objednávky, číslo zákazníka, číslo plátce, číslo faktury - EDI, datum a čas, stav faktury, ID uživatele a příznak, zda šlo o ruční změnu stavu. Záznamy protokolu nelze na stránce upravovat.

## Položky zámku tabulky EDI

Aby uživatel nemohl měnit doklad, který právě prochází EDI zpracováním, modul si vede vlastní **Položky zámku tabulky EDI**. Pokus o změnu uzamčeného záznamu skončí hláškou, že záznam nelze změnit, protože je uzamčen jiným uživatelem. Kontrola se uplatňuje i na řádky navázaných dokladů (prodejní a nákupní řádky, řádky servisu, převodu, skladových příjemek a dodávek, deníky).

## Komunikace s providerem EDI

Vlastní přenos zpráv k providerovi nezajišťuje EDI konektor sám, ale modul **Spooler**, který je součástí stejné aplikace (IB-EConnect360). Na kartě EDI komunikace se komunikace přes Spooler zapne polem **Komunikovat pomocí Spooleru** a naváže se na **ID úlohy Spooleru** a **ID cílového systému**. Příchozí zprávy se ukládají do **IN bufferu**, odchozí do **OUT bufferu**.

Spooler podporuje tyto způsoby interakce: **HTTP**, **E‑Mail** (včetně Exchange schránky), **webová služba**, **Spooler API**, **Spooler SOAP WS** a **Spooler OData WS**, s autentizací přes OAuth 2.0.

> [!NOTE]
> Modul EDI konektor základ sám o sobě neobsahuje žádný objekt vázaný na konkrétního providera. Provider se do řešení doplňuje vždy samostatnou aplikací nebo sadou konverzních objektů, které se v nastavení propojí polem **ID objektu**.

## Viz také

[EDI konektor základ - nastavení](edi-connector-basic-setup.md)  
[Productivity Pack](productivity-pack.md)
