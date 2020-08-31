---
title: AUTOCONT SOLUTIONS - SK Legistaltive Pack | Microsoft Docs
description: This section describes AUTOCONT Solutions - Slovak legislation - 
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Slovak, , additional functions, sale, VAT
ms.author: v-makune
---

# Rozvaha a výkaz zisku a ztrát - SK xx

Pro potřeby výkazů slovenské legislativy je v systému D365 BC využívána standartní funkčnost účetních schémat doplněná o úpravy, které umožňují export jednotlivých účetních výkazů na portál finanční správy SR.

## Rozlišení schéma pro vybranou zemi

Jednotlivé řádky výkazů, rozvaha a výkaz zisků a ztrát, se definují v Účetních schématech. Pro každý výkaz je nadefinované samostatné schéma a k příslušnému účetnímu schématu je nadefinované rozložení sloupců.

V Účetních schématech lze vybrat pro jakou legislativu je schéma vytvořeno v poli **Přiřazeno** legislativě. Pole Přiřazeno legislativě slouží k oddělení SK a CZ výkazů prostřednictvím filtru. 

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Účetní schémata** a poté vyberte související odkaz.
2. Ve sloupci **Přiřazeno legislativě** se bude vyplněno **SK**

## Mapování souborů finančního schématu

Pro export finančních výkazů do xml musí mít jednotlivé řádky nastaveno mapování v pomocné tabulce podle výkazů stanovených Finanční správou SR. Je potřebné namapovat každé porovnávací období a řádek/sloupec samostatně. To znamená, že pro každý řádek výkazu je nastavené mapování běžného a minulého období.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Účetní schémata** a poté vyberte související odkaz.
2. Na kartě **Účetní schémata** zvolte akci **Proces** a funkci **Upravit účetní schéma**.
3. Na kartě vybraného **Účetního schématu** vyberte tlačítko **Akce** a poté vyberte funkci **Mapování souborů**.
4. Na kartě **Mapování souborů účetního schématu** nastavte pole dle potřeby.
5. Po úpravách kartu zavřete.

## Export finančního schématu

Pro samotný export účetního schématu lze použít sandardní funkčnost sytému.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Účetní schémata** a poté vyberte související odkaz.
2. Na kartě **Účetní schémata** zvolte akci **Proces** a funkci **Upravit účetní schéma**.
3. Na kartě vybraného **Účetního schématu** vyberte tlačítko **Akce** a poté vyberte funkci **Uložit výsledky** nebo **Výsledky**.
4. V okně **Uložit výsledek úč. schématu** vyplňte pole dle potřeby.
5. Potvrďte pomocí tlačítko **OK**.

Výsledky účetních schémat se ukládají do seznamu v chronologickém sledu jejich vzniku. Na označení výsledků výkazů je vytvořena číselná řada nastavená v Nastavení financí.

## Viz také 
[AUTOCONT Řešení](../index.md)  
[SK Legislativní balíček](ac-sk-legislative-pack.md)