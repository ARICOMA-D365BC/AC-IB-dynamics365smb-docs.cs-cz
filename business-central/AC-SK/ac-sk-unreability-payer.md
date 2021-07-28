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

# Institut nespolehlivosti plátce

Funkcionalita zahrnuje systémové kontroly, které upozorňují uživatele na nespolehlivého plátce DPH při zpracování dokladů.

Seznam subjektů, u kterých nastaly důvody pro zrušení registrace platitele daně z přidané hodnoty, je dostupný na webových stránkách Finanční správy:

https://www.financnasprava.sk/sk/elektronicke-sluzby/verejne-sluzby/zoznamy/exporty-z-online-informacnych

Soubor "Zoznam platiteľov DPH zrušených.zip (XML)" je potřeba uložit a naimportovat do systému.

## Import souboru

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Položky nespolehlivosti plátce** a poté vyberte související odkaz.
2. Na stránce **Položky nespolehlivosti plátce** vyberte **Akce** a pak možnost **Hromadné načtení nespolehlivosti dod.**
3. Otevře se okno **Volba importu podle legislativy**, kde je nutné vybrat sekvenci **SK** a potvrdit pomocí tlačítka **OK**.
4. Poté se otevře okno **Import nespolehlivosti plátců DPH z xml formátu**, kde uživatel vybere **Název souboru**, který se má importovat.
5. Import potvrďte pomocí tlačítka **OK**.

![Import nespolehlivých plátců DPH z xml formátu](media/unreliability-payer-xml.png)

Po vytvoření **položek nespolehlivosti plátce** systém zkontroluje údaje na kartách zákazníků (Datum kontroly nespolehlivosti, Nespolehlivý plátce DPH) / dodavatelů a dohledá a vepíše na karty zákazníků nebo dodavatelů nacházejících se v uvedeném seznamu do pole **Nespolehlivý plátce** – ANO a do pole **Datum kontroly nespolehlivosti** se přenáší datum importu údajů ze souboru.

![Import nespolehlivých plátců DPH z xml formátu](media/customer-unreliability-payer.png)

V případě, že se zákazník / dodavatel v uvedeném v seznamu nenachází, zůstane údaj Nespolehlivý plátce prázdný.

## Aktualizace nespolehlivosti plátce

Při vytvoření nové karty Zákazníka / Dodavatele je potřebné tabulku Položky nespolehlivosti plátce aktualizovat.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Položky nespolehlivosti plátce** a poté vyberte související odkaz.
2. Na stránce **Položky nespolehlivosti plátce** vyberte **Akce** a pak možnost **Kontroluj všechny položky**.

## Viz také

[AUTOCONT Řešení](../index.md)  
[SK Legislativní balíček](ac-sk-legislative-pack.md)
