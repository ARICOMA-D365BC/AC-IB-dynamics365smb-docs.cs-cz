---
title: AUTOCONT SOLUTIONS - Parcels setup | Microsoft Docs
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

# Nastavení Balíkobotu

Pro správné fungování addonu Zásilek je zapotřebí nastavit několik oblastí:

- Expediční místa
- Nastavení Balíkobotu
- Přepravce
- Nastavení lokací
- Parametry zásilky
- Nastavení tisku
- Nastavení způsobu platby (dobírka)


Ostatní číselníky (Služby přepravce, Manipulační jednotky a Pobočky přepravce) si addon stahuje z API Balíkobotu.


## Expediční místa

Expediční místo je místo Vašeho skladu odkud jsou expedovány zásilky. Uživatel může mít několik expedičních míst. Každé expediční místo je spojeno s jednou lokací Vaší společnosti. 

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Expediční místa** a poté vyberte související odkaz. 
2. Na přehledu vyhrat funci **Nový**
3. Zadat **Kód** pro expediční místo, popis, adresu a **Název uživatele a heslo** k Vašemu API.
4. Zavřít přehled expedičních míst pomocí OK
## Nastavení balíkobotu

Pro spuštění funkce Balíkobotu je potřeba provést nastavení:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení Balíkobotu** a poté vyberte související odkaz.
2. Vybrat číselnou řadu pro zásilky
3. Zadat do pole URL služby: https://api.balikobot.cz
4. Vybrat kód výchozího expedičního místa
5. Povolit nebo zakázat automatický tisk protokolů svozu
6. Povolit nebo zakázat Protokol aktivity
7. Povolit nebo zakázat synchronizaci master dat (stahování číselníku z API Balíkobotu)
8. Povolit nebo zakázat funkce Balíkobotu (Po povolení se začnou stahovat číselníky)
9. Potvrdit pomocí OK

## Nastavení přepravců

Na přehledu **Přepravci** v rámci addonu přibyly nová pole a funkce.

Pole nad přepravci:

- Povoleno pro Balíkobot - Přepravce je povolen a je možné ho používat
- Povolit více balíků - Při vytváření zásilky funkce umožní vytvořit více balíků v rámci jedné zásilky
- Paletová přeprava
- Počet manipulačních jednotek - U paletové přepravy je možnost nastavit více manipulačních jednotek

Funkce nad přepravci:

- Služby přepravců - Tabulka služeb jednotlivých přepravců
- Pobočky přepravců - Tabulka lokalit, kde si mohou zákazníci zboží od přepravce převzít 
- Manipulační jednotky - Tabulka manipulačních jednotek paletové přepravy

## Nastavení lokací

Na kartě lokace je zapotřebí nastavit **Kód Expedičního místa**. 

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Lokace** a poté vyberte související odkaz.
2. Otevřít kartu požadované lokace
3. Vyplnit pole **Kód expedičního místa** v záložce Obecné


## Parametry zásilek

Parametry pro jednotlivé přepravce nejsou stahovány z API balíkobotu a je potřeba je zadat ručně nebo pomocí RapidStart Balíku.


 ## Nastavení tisku

 Pro nastavení tisku štítku je potřeba nastavit ID sestavy a přidělit uživateli tiskárnu. Funkce tisk štítků je nastavená, aby tiskla na definové tiskárně.

Definice tiskárny:
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Výběry tiskáren** a poté vyberte související odkaz. 
2. Zvolit **Nový**
3. Vybrat ID uživatele, ID sestavy 52068430 a Název tiskárny

Tisk předávacího protokolu se tiskne automaticky po objednání svozu. Pokud uživatel nechce automatický tisk, stačí v Nastavení Balíkobotu vypnout Boolean - Tisk předávacích protokolů svozu. Tisk se provádí z Výchozí tiskárny dle Vašeho zařízení. Případně pokud máte nastavenou výchozí tiskárnu ve **Výběry tiskáren** jako zbytek Vašich tiskových sestav.

## Nastavení způsobu platby - Dobírka

Pro nastavení a používání funkce zásilka na dobírku je zapotřebí nastavit na způsobu platby booeal **Dobírka**

1.  Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **způsob platby** a poté vyberte související odkaz.  
2. V přehledu vybrat na daný způsob platby boolean **Dobírka**
3. Zavřít přehled způsobu platby

## Viz také
[Zásilky](ac-parcels.md)  
[AC Productivity Pack](ac-productivity-pack.md)  
[AUTOCONT řešení](index.md)
