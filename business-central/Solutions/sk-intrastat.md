---
title: ARICOMA SOLUTIONS - SK Legistaltive Pack| Microsoft Docs
description: This section describes ARICOMA Solutions - Slovak legislation
author: kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Slovak, , additional functions, sale, VAT
ms.author: v-makune
---

# Výkaz Intrastat

> Aktualizace 17.10.2025

Pro účely generování výkazu Intrastat se používá standartní funkcionalita.

Rozdíl oproti standardní funkčnosti je v struktuře souboru s příponou .xml generovaném pro účely slovenského vykazování.

Pro aktivování slovenských funkčností jsou potřebná tato nastavení, využijte následující postup:

## Nastavení financí

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení financí** a poté vyberte související odkaz.
2. Na kartě **Nastavení financí** je nutné vybrat do pole **Legislativa** hodnotu **SK**.
3. Potvrďte pomocí tlačítka **OK**.

> [!IMPORTANT]
> Od verze 25 je potřeba mít nastavenu základní funkcionalitu v *Nastavení hlášení Intrastat* (viz [dokumentace](https://learn.microsoft.com/cs-cz/dynamics365/business-central/finance-how-setup-report-intrastat)).

## Intrastat mapování souboru

Nastavení slouží pro mapování polí v aplikaci na uzly .xml. Tato tabulka je součástí dodávaného konfiguračního balíčku.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Intrastat mapování souboru** a poté vyberte související odkaz.
2. Na kartě **Intrastat mapování souboru** zkontrolujte, nebo doplňte nastavení.
3. Potvrďte pomocí tlačítka **OK**.

![Mapování souboru](media/sk-intrastat.png)

> [!TIP]
> Kompletní nastavení mapování najdete v Konfiguračním balíčku, který získáte spuštěním Asistovaného nastavení *Nastavit SK lokalizaci* (buď pouze naimportujte poslední verzi pomocí tlačítka *AssistEdit* ve stávající společnosti nebo v prázdné společnosti proveďte kompletní import vzorové parametrizace pomocí akce *Použít balíček*).

## Export souboru pro Intrastat

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Deníky Intrastat** a poté vyberte související odkaz.
2. Vložte řádky deníku pomocí funkce **Návrh řádků**.
3. Exportujte pomocí funkce **Exportovat**, je nutné vyplnit *Kontaktní osoba*, *Typ*, *Pořadové číslo výkazu*
4. Potvrďte pomocí tlačítka **OK**.

## Viz také




[ARICOMA Řešení](solutions.md)  
[SK Legislativní balíček](sk-legislative-pack.md)
