---
title: SK Fiscal Printers Integration - Setup
description: SK Fiscal Printers Integration - Setup
author: RobertJelen
date: 07/31/2025
reviewer: janousek
ms.service: dynamics-365-business-central
ms.search.keywords: Czech, Slovak, SK Fiscal Printers Integration, Streamline Tools
---

# Integrace s SK fiskálními tiskárnami pro Dynamics 365 Business Central

> Aktualizace 31.07.2025

**Integrace s SK fiskálními tiskárnami** je rozšířením pro informační systém Microsoft Dynamics 365 Business Central, které poskytuje přímé propojení s fiskálními tiskárnami od firmy VAROS řady [eKASA FT5000](http://www.varos.sk/vyrobky-FT5000). Toto řešení je navrženo tak, aby plně splňovalo slovenské legislativní požadavky dle zákona 289/2008 Z.z., který upravuje evidenci tržeb z prodeje zboží a služeb v hotovosti či jinými způsoby (např. platební kartou, stravenkami nebo šeky).

## Hlavní přínosy modulu

- **Plná legislativní shoda** – Umožňuje tisk a elektronickou registraci daňových dokladů dle aktuální slovenské legislativy, včetně úhrady zálohových faktur, což zajišťuje, že vaše firma bude vždy v souladu s právními předpisy.
- **Zefektivnění správy dokladů** – Modul umožňuje automatické zpracování dokladů o úhradě faktur a poskytuje možnost dodatečného tisku kopií. Zákazníci mají také možnost ručně registrovat doklady a označit je jako zaregistrované, což přináší vyšší flexibilitu při práci s doklady.
- **Přístup k historii dokladů** – Uživatelé mohou snadno zobrazit kompletní historii fiskálních dokladů přímo v Dynamics 365 Business Central, což zlepšuje přehlednost a správu finančních záznamů.
- **Jednoduché a spolehlivé API propojení** – Modul využívá API rozhraní od firmy VAROS pro bezproblémovou komunikaci i Business Central Online s fiskálními tiskárnami. Pro jednodušší správu je poplatek za API zahrnut v ceně modulu (cena podle počtu zařízení).

Technické informace firmy VAROS viz [Manuály](http://www.varos.sk/manualy.php).

> [!IMPORTANT]
> Modul vyžaduje **Core Localization Pack for Czech**, pro naplnění ostatních požadavků Slovenské legislativy zvolte [SK legislativní balíček](https://appsource.microsoft.com/en-us/product/dynamics-365-business-central/PUBID.autocontas%7CAID.pas_2021_3%7CPAPPID.6faf8513-1781-444c-8c20-032a6f1efe06?tab=Overview) a [SK jazykový balíček](https://appsource.microsoft.com/en-us/product/project-madeira/PUBID.autocontas%7CAID.pas_2021_5%7CPAPPID.a90b83b0-d99d-4156-9c65-526b37fe3497) od Aricoma.

## Použití

V následujícím textu je popsány scénáře podporované modulem Integrace s fiskálními tiskárnami.

> [!NOTE]
> Lepší uživatelské zkušenosti lze dosáhnout v kombinaci s modulem [Více způsobů plateb](../Solutions/multiple-payment-methods.md).

### Vytvoření daňového dokladu na fiskální tiskárně

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Prodejní faktury** a poté vyberte související odkaz.
2. Na stránce **Prodejní faktury** klikněte na funkci *Nový* a vytvořte novou prodejní fakturu.
3. Doplňte řádky dokladu dle potřeby.

> [!IMPORTANT]
> Na prodejním dokladu musí být nastaveno **Ceny vč. DPH** na Ano. Systém na to uživatele upozorní při zadání Kódu způsobu platby s nastaveným příznakem **Fiskální daňový doklad**.

4. V poli **Kód způsobu platby** vyberte způsob platby propojený s fiskální tiskárnou (viz [Nastavení způsobů plateb](SK-FiscalPrinters-Integration-setup.md#nastavení-způsobů-plateb) se zapnutým příznakem **Fiskální daňový doklad**).
5. Zaúčtujte doklad.

Pokud je vše správně nastaveno, spolu s jinými vznikla Fiskální položka (viz akce *Najít položky*) a na fiskální tiskárně je vytištěn daňový doklad obsahující jednotlivé řádky zaúčtované prodejní faktury.

> [!NOTE]
> Ve fiskálních položkách je možné zjistit, zda-li je bloček daňovým dokladem dle hodnoty v poli **Daňový doklad**.

### Úhrada zaúčtované faktury na fiskální tiskárně

Tento scénář popisuje hotovostní úhradu zaúčtované faktury v případě, že je fiskální tiskárna v BC připojena k entitě Bankovní účet. V případě připojení k entitě Pokladna, stačí vytvořit pokladní doklad běžným způsobem (obdobně jako dále v [Úhrada zálohové faktury na fiskální tiskárně](#úhrada-zálohové-faktury-na-fiskální-tiskárně)).

> [!NOTE]
> Více v [Propojení fiskálních tiskáren na Bankovní účty / Pokladny](./SK-FiscalPrinters-Integration-setup.md#propojení-fiskálních-tiskáren-na-bankovní-účty--pokladny).

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Deníky plateb** a poté vyberte související odkaz.
2. Na stránce **Deníky plateb** vytvořte nový řádek.
3. Doplňte informace pro zaúčtování platby faktury (Typ řádku = Platba, Typ účtu = Zákazník, Číslo účtu = číslo zákazníka z faktury)
4. Přes pole Číslo vyrovnání dokladu vyberte požadovaný doklad k úhradě a potvrďte výběr
5. V poli **Typ protiúčtu** zadejte Bankovní účet, v poli **Číslo protiúčtu** pak bankovní účet s nastavenou fiskální tiskárnou.
6. Před zaúčtováním dokladu upravte ručně částku, aby byla zaokrouhlena na 5 centů. Pokud není částka platby ručně v deníku upravena tak, aby byla zaokrouhlena na 0,05, tak systém uživatele upozorní a transakci nelze bez korekce zaokrouhlení platby zaúčtovat.
7. Funkcí *Účtovat* proveďte zaúčtování interního dokladu.

Pokud je vše správně nastaveno, spolu s jinými vznikla Fiskální položka (viz akce *Najít položky*) a na fiskální tiskárně je vytištěn „Doklad o úhradě faktury“ (na kterém je uvedeno číslo faktury a uhrazená částka).

> [!NOTE]
> Pokud je třeba uhradit fakturu více typy platidel (např. kombinace karta a hotovost), zadáte více řádků deníku s požadovanými částkami a příslušnými bankovními účty jako protiúčtem. Všechny tyto řádky pak musí mít stejné číslo dokladu.

### Vyrovnání faktury na fiskální tiskárně při jejím účtování

Jedná se o případ, kdy má být výsledkem účtování prodejního dokladu Účtovaná prodejní faktura a zároveň Doklad o zaplacení faktury na fiskální tiskárně.

Postup je stejný jako v kapitole [Vytvoření daňového dokladu na fiskální tiskárně](#vytvoření-daňového-dokladu-na-fiskální-tiskárně). Rozdíl je pouze v tom, že použijete Kód způsobu platby s vypnutým příznakem **Fiskální daňový doklad**.

### Úhrada zálohové faktury na fiskální tiskárně

Tento scénář popisuje případ, kdy prodejce vyhotoví prodejní zálohovou fakturu s předpokládaným bezhotovostním způsobem úhrady. Následně se zákazník s prodejcem domluví na úhradě na místě.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Pokladní doklady** a poté vyberte související odkaz.
2. Na stránce **Pokladní doklady** klikněte na funkci *Nový* a vytvořte nový pokladní doklad.
3. V poli **Typ dokladu** vyberte Příjem.
4. Na řádku dokladu vyberte v poli **Číslo účtu** příslušného zákazníka a v poli **Číslo zálohy** požadovanou zálohovou fakturu.
5. V poli **Částka** zkontroluje hrazenou částku (systém předvyplní hodnotu pro plnou úhradu).
6. Funkcí *Účtovat* proveďte zaúčtování pokladního dokladu.

Pokud je vše správně nastaveno, zaúčtováním příjmového pokladního dokladu vznikla Fiskální položka (viz akce *Najít položky*) a na fiskální tiskárně je vytištěn „Doklad o úhradě faktury“ (na kterém je uvedeno číslo faktury a uhrazená částka).

### Hotovostní úhrada nákupního dobropisu

Registrace na fiskální tiskárně je podporována i na straně nákupu. Obdobně jako u [Vyrovnání faktury na fiskální tiskárně při jejím účtování](#vyrovnání-faktury-na-fiskální-tiskárně-při-jejím-účtování) je řízeno výběrem **Kódu způsobu platby** na nákupním dokladu.

> [!NOTE]
> Příznak **Fiskální daňový doklad** na Kódu způsobu platby je ignorován, na straně nákupu se vždy jedná jen o „úhradu faktury“.

### Dotace fiskální pokladny z jiné pokladny

Tento scénář se týká převodu hotovosti z běžné pokladny do pokladny reprezentující fiskální tiskárnu.

Uživatel vytvoří a zaúčtuje 2 pokladní doklady:

- Výdajový – na řádku dokladu finanční účet „Peníze na cestě“.
- Příjmový – pro pokladnu kde Platební prostředek fiskální tiskárny má hodnotu *Hotovost*, na řádku dokladu finanční účet „Peníze na cestě“.

Pokud je vše správně nastaveno, zaúčtováním příjmového pokladního dokladu vznikla  Fiskální položka (viz akce *Najít položky*) a na fiskální tiskárně je vytištěn doklad Vklad hotovosti.

### Výběr hotovosti z fiskální pokladny

Tento scénář se týká převodu hotovosti z fiskální tiskárny. Pokud se jedná o převod do běžné pokladny, postupujte obdobně jako v [Dotace fiskální pokladny z jiné pokladny](#dotace-fiskální-pokladny-z-jiné-pokladny).

V případě propojení fiskální tiskárny s Bankovním účtem se např. scénář s vkladem na bankovní účet v bance realizuje kompletně ve Finančním deníku:

- Řádek s Bankovním účtem reprezentujícím firemní bankovní účet;  jako protiúčet je „Peníze na cestě“
- Řádek s Bankovním účtem, kde Platební prostředek fiskální tiskárny má hodnotu Hotovost; jako protiúčet je „Peníze na cestě“

Pokud je vše správně nastaveno, zaúčtováním deníku vznikla i jedna Fiskální položka (viz akce Najít položky) a na fiskální tiskárně je vytištěn doklad Výběr hotovosti.

### Funkce eKASA a přehledy prodeje

Ostatní funkce eKASA a Přehledy prodejů (Denní uzávěrka, Měsíční…) jsou k dispozici v programu Tlačový manažér.

### Hotovostní operace bez Business Central

Všechny výše uvedené hotovostní operace (Daňový doklad, Vklad, Výběr, Úhrada faktury, Storno faktury, Mincovka) je možné provádět ručně v SW „Tlačový manažér“.
Dodatečně je možné provést příslušné úkony v BC s tím, že fiskální tiskárna bude vypnuta a vytvořené fiskální položky se dodatečně ručně označí jako „Registrované“ (viz dále).

### Další operace s fiskálními položkami

#### Registrace položky

Pokud se fiskální doklad nevytiskne, může být (kromě problému se samotnou tiskárnou) problém v tom, že se nepovedlo z nějakého důvodu správně tzv. „registrovat“ položku. Informaci o registraci si nese Fiskální položka – viz sloupce **Registrováno** a **Datum a čas registrace**.

Pokud dává smysl znovu položku registrovat (byla vypnutá tiskárna apod.), může uživatel položku dodatečně registrovat:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Fiskální položky** a poté vyberte související odkaz.
2. Na stránce **Fiskální položky** najděte příslušný záznam a spusťte akci *Registrovat položku*.

> [!NOTE]
> V praxi je často vhodnějším způsobem pro nalezení správné Fiskální položky využití akce *Najít položky* na zaúčtovaném prodejním dokladu.

Pokud již není účelné znovu položku registrovat (typicky když byl doklad vytištěn a i přesto položka neobsahuje informaci o úspěšné registraci), může uživatel položku ručně označit jako již registrovanou.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Fiskální položky** a poté vyberte související odkaz.
2. Na stránce **Fiskální položky** najděte příslušný záznam a spusťte akci *Ručně nastavit jako registrováno*.

> [!NOTE]
> V tomto případě zvažte nastavení vyšší hodnoty v poli **Časový limit integrace (ms)** u příslušné fiskální tiskárny (viz [Nastavení fiskálních tiskáren](SK-FiscalPrinters-Integration-setup.md#setting-up-fiscal-printers))..

#### Tisk kopie fiskální dokladu

Pokud je třeba vytisknout kopii fiskálního dokladu (v průběhu tisku došel papír nebo byl doklad jinak poškozen), je možné přímo z BC vytisknout doklad znovu:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Fiskální položky** a poté vyberte související odkaz.
2. Na stránce **Fiskální položky** najděte příslušný záznam a spusťte akci Tisk kopie fiskálního dokladu.

#### Zobrazení vyměňovaných dat

V případě nejasností je možné si zobrazit soubory, které jsou předmětem výměny mezi BC a fiskální tiskárnou. Tyto jsou evidovány přímo v položkách:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Fiskální položky** a poté vyberte související odkaz.
2. Na stránce **Fiskální položky** najděte příslušný záznam.
3. Spusťte akci *Stáhnout registrační dávku* (data, která byla zaslána do fiskální tiskárny).
4. Spusťte akci *Stáhnout potvrzení registrace* (přijatá data – interní data o registraci).

## Viz také

[Nastavení Integrace s SK fiskálními tiskárnami](SK-FiscalPrinters-Integration-setup.md)  
[Streamline Tools](streamlinetools.md)  
[ARICOMA řešení](solutions.md)