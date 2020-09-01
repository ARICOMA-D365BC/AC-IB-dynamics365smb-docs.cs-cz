---
title: AUTOCONT SOLUTIONS - SK Legistaltive Pack| Microsoft Docs
description: This section describes AUTOCONT Solutions - Slovak legislation
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Slovak, , additional functions, sale, VAT
ms.author: v-makune
---

# Výkaz DPH

Stejně jako v případě výkazu vztahujících se k účetní závěrce je i v případě výkazů DPH využita standartní funkcionalita systému. Pro zachování historických výkazů DPH se při každé změně struktury výkazu vyplývající ze změny legislativy vytvoří nový list výkazu DPH s příslušným označením.

## Import XML schématu
XML schéma k výkazu DPH je potřebné do aplikace naimportovat do XML schémat.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **XML schémata** a poté vyberte související odkaz.
2. Na stránce **XML schémata** vyberte akci **Načíst schéma**.
3. Otevře se vám okno pro import, kde vyberete příslušný XML soubor.
4. Po import se na kartě **XML schémata** objeví nový řádek.
5. V příslušném řádku pro každé XML vyberte správné číslo ve sloupci SML portID. 

Pro Výkaz DPH od roku 2018 to je **52068861**, pro Výkaz DPH do roku 2017 to je **52068860**, pro Kontrolní výkaz DPH **52068903** a pro Souhrnný Výkaz to je 52068870.

## Nastavení výkazu XML

Pro nastavení využijte následující postup:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení financí** a poté vyberte související odkaz.
1. Na kartě **Nastavení financí** je nutné vybrat pole **Legislativa** a kartu zavřít.
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony výkazu DPH** a poté vyberte související odkaz.
1. Na kartě **Šablony výkazu DPH** vyberte ve sloupci **Formát XML SK** možnost **Použij XML schéma**.
1. K listu šablony se vybere příslušné schéma, která bude použito při exportu – pole **XML schéma**.

K jednotlivým řádkům musíme přiřadit hodnotu do pole ID elementu xml schématu (T9610 – XML Schema Element), na základě které bude automaticky vyplněn kód atributu

Na export se používá tlačítko nacházející se na páse s nástroji „Export SK“. Prostřednictvím tohoto tlačítka se zobrazuje formulář tisku, kde je potřebné vyplnit údaje stejně jako při zadávání kritérií pro zobrazení náhledu schématu.  

Při exportu bude použita taková struktura xml souboru, která je definována pro konkrétní list výkazu DPH (přiřazený ve formuláři „Názvy výkazů DPH“ – nové pole XML schéma).  

Tímto se zabezpečí, že soubor xml bude k dispozici v platné struktuře pro každé vykazované období a bude možné jej načítat do formuláře na stránce Finanční správy, resp. Do aplikace eDane při elektronickém podání výkazu DPH.

Údaje o společnosti jsou do jednotlivých souborů načítané z tabulky Informace o společnosti a Nastavení statutárního vykazování.

## Viz také 
[AUTOCONT Řešení](../index.md)  
[SK Legislativní balíček](ac-sk-legislative-pack.md)