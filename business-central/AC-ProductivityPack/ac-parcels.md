---
title: AUTOCONT SOLUTIONS - Parcels | Microsoft Docs
description: This section describes parcel functionality - Balikobot Integration
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, shipment, parcels, Shipping
ms.date: 06/24/2020
ms.author: v-makune
---

# Zásilky

Addon zásilek slouží k vytvořání zásilek a přímému tisku štítků vybraných dopravců, odesílání dat o zásilkách přepravci a objednání samotného svozu balíků. Pomocí totoho rozšíření je zrychlen proces zpracování a vytváření zásilek posílaných zákazníkům. Tento Addon využívá API služby Balíkobot.

Tento addon je stavěn na základu načítání čárového kódu (čísel) účtovaných dokladů. Zásilky je možno vytvářet z účtovaných prodejních dodávek a faktur. Pokud uživatel bude vytvářet zásilku z účt. prodejní dodávky, zásilka se vytváří bez dobírky a z faktur s dobírkou.

Seznam přepravců:
 - Česká pošta s.p.
 - DHL Express
 - Direct Parcel Distribution CZ s.r.o.
 - Geis CZ s.r.o.
 - General Logistics Systems Czech Republic s.r.o.
 - IN TIME SPEDICE s. r.o.
 - Pošta bez hranic (Frogman s.r.o.)
 - PPL CZ s.r.o. 
 - Slovenská pošta a.s.
 - TNT
 - TOPTRANS EU a.s.
 - Uloženka s.r.o.
 - UPS
 - Zásilkovna s.r.o.

## Vytvoření nové zásilky z účtovaného dokladu

Po zaúčtování dodání nastává proces vytvoření zásilky pro zákazníka. Jedním ze způsobů je vytvoření zásilky s dodacího listu nebo účtované faktury. Pomocí načítání čísla dokladu se automaticky předvyplní formulář **Vytvořit zásilku**. Tímto krokem uživatel nemusí ručně vypisovat údaje o zásilce.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Vytvořit zásilku** a poté vyberte související odkaz.
2. Vložte číslo účtovaného dokladu (účtovaná prodejní dodávka, účtovananá prodejní faktura) do pole **Číslo dokladu**
3. Vyberte funkci **Vytvořit zásilku a vytisknout štítek**
4. Zásilka je nyní vytvořena a zároveň je ve stavu **Ke svozu**, tzn. má již od dopravce přidělené číslo, štítek a data jsou na straně Balíkobotu).

## Ruční vytvoření zásilky

Zásilky lze vytvářet i bez účtovaných dokladů.

1. Na přehledu zásilek zvolit funkci **Nový**
2. Naplnit potřebná pole pro daného přepavce a jeho službu
3. Funkce **Přidat ke svozu** (zásilka je ve stavu **Ke svozu** a je možné tisknout štítek)
4. Funkce **Tisk štítku**
5. Zásilka je připravena k objednání svozu.

## Úprava zásilky
Upravovat zásilky lze pouze pokud jsou ve stavu **Nová**. Pokud je zásilka ve stavu **Svozeno** nelze ji již editovat. Pro úpravu/smazání informací zásilky, musí být ve stavu **Ke svozu**. Pomocí funkce Odebrat ze svozu se změní stav z **ke svozu** na **Nová**.

 Po tomto kroku je třeba uvědomit přepravce, že zásilku mažete nebo upravujete. V tento okamžik je zásilce odebráno číslo od přepravce a je smazán štítek. Po upravení dat uživatel použije funkci **Přidat ke svozu** a pro vytištění nového štítků použít funkci **Tisk štítků**.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Zásilky** a poté vyberte související odkaz.
2. Postavit se na řádek ze zásilkou a použít funkci **Odebrat ze svozu**
3. Otevřít danou zásilku (nyní má stav **nová**)
4. Doplnit údaje/hodnoty o zásilce (Změna přepravce, počet balíků, hmotnost, rozměry...)
5. Použít funkce **Přidat ke svozu** (zásilka je ve stavu **Ke svozu** a je možné tisknout štítek)
6. Dále je nutné použít funkci **Tisk štítku**
7. Zásilka je připravena k **objednání svozu**.

## Objednání svozu
Objednání svozu slouží k definitivnímu objednání svozu zásilek. Data zásilek budou předány dopravci a zaevidovány v jeho systému. Zásilka čeká na expedici.

1. Na přehledu zásilek vybrat funkci **Objednat svoz**
2. Na kartě objednat svozu zvolit, zda se bude objednávat svoz jednoho přepravce (**Objenad svoz**) nebo všech (**Objednat všechny svozy**).
3.  Po spuštění funkce se vytiskne **Předávací protokol svozu**.

## Tisk předávacího protokolu svozu

Pro dodatečný tisk předávacího protokolu svozu slouží funkce **Předávací protokol svozu**.
1. Kliknout na funkci **Tisk předávacího protokolu svozu**.
2. Otevře se PDF soubor, který se následně vytiskne z okna prohližeče.

## Kontroly a omezení

 - Pokud jsou na prodejní objednávce vyplněny pole Kód přepravce a Kód služby přepravce, je nutné zadat telefonní číslo a e-mail příjemce. POkud pole nebudou vyplěny nelze doklad vydat.
 - Při zadávání dat na kartě zásilky (automaticky pomocí načtení kódů, nebo ručně) je na kartě zásilky funkce **Ověřit data zásilky**. PO spuštění dostanete informaci, zda jsou předávané informace v pořádku.
 - Jedno expediční místo může být přiřazeno jedné lokaci. Vzniká vazba 1:1.

## Viz také
[Nastavení zásilek](ac-parcels-setup.md)  
[AC Productivity Pack](ac-productivity-pack.md)  
[AUTOCONT řešení](index.md)
