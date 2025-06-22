---
title: Evidence nástrojů a pomůcek - nastavení
description: Nastavení modulu evidence nástrojů a pomůcek
author: StepanUhlir
date: 11/30/2024
reviewer: janousek
ms.service: dynamics-365-business-central
ms.search.keywords: pack tracking, production tools, productivity pack
---
# Evidence nástrojů a pomůcek - Nastavení
> Aktualizace: 01.12.2024

 Náš modul **Evidence nástrojů a pomůcek** řeší problematiku evidence nástrojů, pomůcek, forem a jiných potřeb, které jsou obvykle evidovány pomocí skladové evidence systému. Tento modul je postaven na základech evidence majetku a sjednocuje evidenci pro potřeby sledování dlouhodobého majetku a výrobní evidence, včetně půjčování nástrojů a pomůcek.

 Pro plnohodnotné používání modulu je nutné je nastavit dle potřeb konkrétní společnosti. Níže jsou popsány jednotlivé části nastavení.

### Šablony deníku evidence nástrojů

1. Vyberte ikonu ![Žárovky, která otevře funkci řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete udělat") a do vyhledávacího pole zadejte **Šablony deníku evidence nástrojů**, poté vyberte související odkaz.
2. Otevře se stránka **Šablony deníku evidence nástrojů**.
3. Klikněte na tlačítko **+ Nový** pro vytvoření **nové šablony**.
4. Do pole **Název šablony** zadejte název, který nejlépe vystihuje účel této šablony.
5. V poli **Výchozí typ položky vyberte typ položky**, například **Zapůjčit**, pokud chcete, aby šablona sloužila pouze k evidenci zápůjček. 
6. Do pole **Číselná řada dokladů** zadejte nebo vyberte číselnou řadu, která bude použita k evidenci pohybů.
7. Uložte šablonu kliknutím na tlačítko **Uložit**

![Evidence nástrojů a pomůcek - nastavení šablony](media/production-tools-tool-journal-template.png)

> [!IMPORTANT]  
> **Je nutné vytvořit alespoň jednu šablonu deníku evidence nástrojů, aby bylo možné zadávat pohyby nástrojů**.

> [!TIP]
> Je možné mít jednu šablonu pro všechny typy pohybů, tedy šablonu, kde při vytvoření nezadáte žádný **Výchozí typ položky**.

### Přidání číselné řady

1. Klikněte na pole **Číselná řada**.
2. Otevře se stránka **Číselné řady**.
3. Klikněte na tlačítko **+ Nový** pro vytvoření nové číselné řady.
4. Do pole **Kód** zadejte jedinečný identifikátor pro číselnou řadu.
5. Do pole **Popis** zadejte stručný popis, který vysvětluje účel číselné řady.
6. Do polí **Počáteční číslo** a **Poslední číslo** zadejte počáteční a koncové číslo řady.
7. Zaškrtněte pole **Výchozí čísla**, pokud chcete, aby systém automaticky generoval čísla v této číselné řadě.
8. Uložte číselnou řadu kliknutím na tlačítko **Uložit**.

![Evidence nástrojů a pomůcek - přidání číselné řady](media/production-tools-add-no.series.png)

### Nastavení typů položky evidence nástrojů

Každá šablona deníku může mít definovány kontroly povinných údajů. Postupujte podle následujících kroků:

1. Vyberte ikonu ![Žárovky, která otevře funkci řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete udělat") a do vyhledávacího pole zadejte **Nastavení typů položky evidence nástrojů** poté vyberte související odkaz.
2. Otevře se stránka **Nastavení typů položky evidence nástrojů**.
3. Klikněte na tlačítko **+ Nový**, čímž vytvoříte nový řádek pro daný typ položky.
4. Vyberte typ položky. Na výběr jsou následující možnosti:
   - **Příjem** – zařazení evidovaného množství nástroje.
   - **Výdej** – vyřazení nástroje z evidence.
   - **Zapůjčit** – evidence zapůjčení nástroje.
   - **Vrátit** – evidence vrácení zapůjčeného nástroje.
5. Pro každý typ položky nastavte povinné údaje, které bude nutné vyplnit v deníku nástrojů.

![Evidence nástrojů a pomůcek - nastavení typů položky](media/production-tools-tool-entry-type-setup.png)

> [!NOTE]  
> **Povinné údaje pomáhají zajistit správnost záznamů v deníku a odpovídající evidenci nástrojů**.

### Nastavení typů poškození

Nastavení typů poškození slouží k rozlišení poškozených evidovaných kusů. Tyto informace mohou být využity pro případné náhrady ze strany zaměstnanců, kteří poškozené nářadí vrací, nebo pro pozdější statistické vyhodnocování.

1. Vyberte ikonu ![Žárovky, která otevře funkci řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete udělat") a do vyhledávacího pole zadejte **Typy poškození** následně vyberte související odkaz.
2. Otevře se stránka **Typy poškození**.
3. Pro přidání nového typu poškození klikněte na tlačítko **+ Nový**.
4. Vyplňte následující pole:
   - **Kód** – jedinečný kód pro typ poškození.
   - **Popis** – slovní popis poškození.
   - **EAN** – čárový kód, který je možné použít při práci se čtečkami čárových kódů.
5. Vyplňte pole dle potřeby a uložte nastavení.

![Evidence nástrojů a pomůcek - Nastavení typů poškození](media/production-tools-damage-types.png)

> [!NOTE]  
> **Správná definice typů poškození umožňuje přesnější evidenci a lepší analýzu stavu nástrojů v budoucnosti.**.




**Viz také**

[Evidence nástrojů a pomůcek](production-tools.md)  
[Productivity Pack](productivity-pack.md)