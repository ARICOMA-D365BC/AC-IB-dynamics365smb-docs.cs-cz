---
title: AUTOCONT SOLUTIONS - AC Parcels - Balikobot integration - setup | Microsoft Docs
description: This section describes parcel functionality - Setup of Balikobot
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, shipment, parcels, Shipping, settings
ms.date: 06/24/2020
ms.author: v-makune
---

# Nastavení - Zásilky - Integrace Balíkobot

Pro správné fungování addonu Zásilek je zapotřebí nastavit několik oblastí:

- Číslenou řadu
- Expediční místa
- Nastavení Balíkobotu
- Přepravce
- Nastavení lokací
- Parametry zásilky
- Nastavení tisku
- Nastavení způsobu platby (dobírka)


Ostatní číselníky (Služby přepravce, Manipulační jednotky a Pobočky přepravce) si addon stahuje z API Balíkobotu.


## Expediční místa

Expediční místo je místo Vašeho skladu odkud jsou expedovány zásilky. Uživatel může mít několik expedičních míst. Pro každé expediční místo je nutné jiné API, dále je expediční místo spojeno s jednou lokací Vaší společnosti. 

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Expediční místa** a poté vyberte související odkaz. 
2. Na přehledu vyhrat funci **Nový**
3. Zadat **Kód** pro expediční místo, popis, adresu a **Název uživatele a heslo** k Vašemu API.
4. Zavřít přehled expedičních míst pomocí OK
![Nastavení Balíkobotu](media/BB_exp_pl.png)

## Nastavení lokací
Na kartě dané lokace je potřeba vybrat expediční místo, které je spjaté s daným API. Pokud bude více lokací, je nutné na každé nastavit příslušné expediční místo. Toto slouží k omezení chybovosti uživatelů, aby nemohli spojit do zásilky doklady s různými expedičními místy.

Pro přiřazení expedičního místa lokaci je zapotřebí nastavit **Kód Expedičního místa**. 

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Lokace** a poté vyberte související odkaz.
2. Otevřít kartu požadované lokace
3. Vyplnit pole **Kód expedičního místa** v záložce Obecné

![Nastavení Balíkobotu](media/BB_lokace.png)
## Nastavení Balíkobotu
Základní nastavení Balíkobotu je nutné provést na stránce **Nastavení Balíkobotu**
![Nastavení Balíkobotu](media/BB_setup.png)
### Stránka Nastavení zásilek

Okno nastavení Zásilek obsahuje:
 - **Čísla zásilek** - Číselná řada pro zásilky.
 - **Kód výchozího expedičního místa** - Výchozí expediční místo, odkud budou odváženy zásilky (viz další kapitola)
 - **Tisk předávací protokolů svozu** – Automatický tisk předávacích protokolu po objednání svozu
 - **Výchozí název tiskárny** – Určuje tiskárnu štítků
 - **Mezdí doba odezvy** – Určuje dobu timeoutu komunikace v jednotlivé zprávě
 - **Povolen protokol aktivity** - Spuštění sledování logu aktivity
 - **Režim ladění** – Umožňuje odchytávání zpráv v komunikaci s danou službou


Základní číselník přepravců se nahrává pomocí RapidStart balíčku pro D365 Business Central.
Ostatní tabulky se stahují a plní po zapnutí synchronizace master dat.
Aktualizace těchto dat probíhá ručně pomocí funkce „Resynchronizace master dat“.
### Spuštění addonu Zásilky - Balíkobot
Pro spuštění funkcí Balíkobotu je potřeba provést nastavení:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení Balíkobotu** a poté vyberte související odkaz.
2. Vybrat číselnou řadu pro zásilky
4. Vybrat kód výchozího expedičního místa
5. Povolit nebo zakázat automatický tisk protokolů svozu
6. Povolit nebo zakázat Protokol aktivity

## Nastavení přepravců

Základní číselník se nahrává pomocí RapidStart balíčku pro Business Central. Tento balíček obsahuje data, která se nestahují z API Balíkobotu:
### Tabulku přepravců

Ostatní tabulky se stahují a plní po synchronizaci master dat a v tabulce přepravců.
Aktualizace těchto dat probíhá ručně pomocí funkce „Resynchronizace master dat“.
![Nastavení Balíkobotu](media/BB_shipping-agents.png)
 
Přehled obsahuje i dopravce, které nemáte u Balíkobotu nakonfigurované. Pro takové se neprovádí import dalších dat (viz dále).
### Na přehledu přepravců je několik polí k nastavení:
 - **Integrační služba** – Určuje přes jakou integrační službu se přepravce používá (v tomto případě Balikobot.cz)
 - **Povolení synchronizace master dat** – Po zapnutí se mohou stánout master dat
 - **Poslední synchronizace master dat** – Datum poslední synchronizace master dat
 - **Povoleno pro Balíkobot** - Přepravce je povolen a je možné ho používat
 - **Povolit více balíků** - Při vytváření zásilky funkce umožní vytvořit více balíků v rámci jedné zásilky
 - **Paletová přeprava**
 - **Počet manipulačních jednotek** - U paletové přepravy je možnost nastavit více manipulačních jednotek
 - **Pouze pobočky** – Určuje, že přepravce slouží pouze jako výdejní místo
 - **Maximální délka adresy** – Nastavuje délku adresy u vybraného přepravce
 ### Funkce nad přepravci
 - **Test spojení** – Test komunikace mezi integrační službou a Business Central
 - **Synchronizace master dat** – Spustí synchronizaci master dat
 - **Služby přepravců** - Tabulka služeb jednotlivých přepravců
 - **Pobočky přepravců** - Tabulka lokalit, kde si mohou zákazníci zboží od přepravce převzít 
 - **Manipulační jednotky** - Tabulka manipulačních jednotek paletové přepravy
 - **ADR jednotky přepravce** – Tabulka ADR jednotek přepravce


## Nastavení služeb přepravců

Služby přepravců se stahují automaticky pomocí API Balíkobotu. Je možné vynutit určité nastavení pro jednotlivé služby přepravce. Pro nastavení musíte:
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Přepravci** a poté vyberte související odkaz.
2. V seznamu vyberte požadovaného přepravce a zvolte funkci **Služby přepravce**
3. Na následující stránce vyplňte pole dle pořeby:
    - **Povoleno pro Balíkobot** - Službu je možné používat (ve výchozím stavu povoleno)
    - **Vynutit hmotnost zásilky**
    - **Vynutit objem zásilky**
    - **Vynutit cenu zásilky**
    - **Vynutit dobírku zásilky**
    - **Vynutit variabilní symbol zásilky**
    - **Hmotnost na řádku** - Hmotnost musí být vyplěna v řádku zásilky 
    - **Služby ČP** – Pouze pro Českou poštu - dlouhý textový řetězec služeb pošty nad danou zásilkou
o	https://www.balikobot.cz/dokumentace/cp_ciselnik_sluzeb.pdf

      



## Parametry zásilek

Parametry pro jednotlivé přepravce nejsou stahovány z API balíkobotu a je potřeba je zadat ručně nebo pomocí RapidStart Balíku.

## Nastavení způsobu platby - Dobírka

Pro nastavení a používání funkce zásilka na dobírku je zapotřebí nastavit na způsobu platby booeal **Dobírka**

1.  Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **způsob platby** a poté vyberte související odkaz.  
2. V přehledu vybrat na daný způsob platby boolean **Dobírka**
3. Zavřít přehled způsobu platby
 ## Nastavení tisku
### Výběr formátu tisku – klientská zóna
Základním krokem nastavení tisku štítků je definice jakým způsobem se budou generovat PDF se štítky ze strany Balíkobotu. V klientské zóně (https://client.balikobot.cz/) uživatel musí nastavit, zda se bude tisknout ve formátu na celou stránku nebo dle pozic na papíru velikosti A4. Vše záleží na tom, na jaké tiskárně se bude tisknout. Pro tisk na tiskárně pro štítky se nemusí vybírat pozice tisku štítku.
### PDF reader
Pro tisk štítků je zapotřebí mít nainstalovaný PDF reader. Pro práci se štítky doporučujeme Foxit pdf a také ho mít nastavený jako výchozí program pro PDF soubory.
### Výběr formátu tisku – klientská zóna
Základním krokem nastavení tisku štítků je definice jakým způsobem se budou generovat PDF se štítky ze strany Balíkobotu. V klientské zóně (https://client.balikobot.cz/) uživatel musí nastavit, zda se bude tisknout ve formátu na celou stránku nebo dle pozic na papíru velikosti A4. Vše záleží na tom, na jaké tiskárně se bude tisknout. Pro tisk na tiskárně pro štítky se nemusí vybírat pozice tisku štítku.

### Výběr tiskárny
 Pro nastavení tisku štítku je potřeba nastavit ID sestavy a přidělit uživateli tiskárnu. Funkce tisk štítků je nastavená, aby tiskla na definové tiskárně.

Pro definice tiskárny je nutné:
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Výběry tiskáren** a poté vyberte související odkaz. 
2. Zvolit **Nový**
3. Vybrat ID uživatele, ID sestavy 52068430 a Název tiskárny

Tisk předávacího protokolu se tiskne automaticky po objednání svozu. Pokud uživatel nechce automatický tisk, stačí v Nastavení Balíkobotu vypnout Boolean - Tisk předávacích protokolů svozu. Tisk se provádí z Výchozí tiskárny dle Vašeho zařízení. Případně pokud máte nastavenou výchozí tiskárnu ve **Výběry tiskáren** jako zbytek Vašich tiskových sestav.


## Viz také
[Zásilky](ac-parcels.md)  
[AC Productivity Pack](ac-productivity-pack.md)  
[AUTOCONT řešení](../index.md)
