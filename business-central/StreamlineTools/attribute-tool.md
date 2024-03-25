---
title: Attribute Tool
description: Attribute Tool documents
author: pustka
ms.service: dynamics-365-business-central
ms.search.keywords: Czech, Attribute Tool, additional functions
---
# Správa atributů

Modul **Správa atributů** je rozšíření pro hromadnou práci s atributy zboží tak, aby uživatel nemusel zadávat atributy zboží u jednotlivých produktů, ale aby je mohl přidat, upravit či smazat pro všechny produkty na jedné stránce. Součástí nástroje je i export a import atributů do souboru excel

Funkcionalita je dostupná na stránce **Správa atributů**, odkud se spouští jednotlivé funkce pro práci s atributy.

## Vytváření nových atributů

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Správa atributů** a poté vyberte související odkaz.
2. Na stránce **Správa atributů** vyberte ikonu **Nový**.
3. Zadejte **Číslo zboží**, **Název atributu** a **Hodnotu atributu**.
4. Do pole **Akce** se automaticky přidá hodnota **Vytvořit**.
5. Nyní vyberte ikonu **Zápis dat**.

![Název](media/CreateNew.png)

Pro kontrolu si můžete zobrazit stránku **Zboží** a pro dané zboží ověřit atributy, které jste zadali.

## Úprava existujích atributů

Po vytvoření atributů je možné atributy upravovat nebo je smazat.
První je ale potřeba existující atributy zobrazit následovně:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Správa atributů** a poté vyberte související odkaz.
2. Na stránce **Správa atributů** vyberte ikonu **Načtení dat** a nyní si můžete zafiltrovat které atributy zboží chcete načíst podle zboží či názvu atributu.
3. Po vyfiltrování klikněte na tlačítko **OK**.

![Název](media/FilterAttributes.png)

Zobrazená data můžete libovolně upravovat. Pokud si přejete u daného atributu zboží změnit hodnotu, změníte hodnotu v poli **Hodnota atributu** a systém automaticky změní hodnotu pole akce na **Upravit**. Pokud si přejete daný atribut smazat, změníte hodnotu pole akce na **Smazat**. Jakmile máte všechny úpravy provedené, vyberete ikonu **Zápis dat** čímž změny aplikujete na data u zboží.

> [!NOTE]
> Pokud nevyberete ikonu **Zápis dat**, data zůstanou nezměněna. Načtením dat přes ikonu **Načtení dat** se automaticky přepíšou data již zapsané na stránce a neaplikují se na atributy zboží.

![Název](media/Changes.png)

Pokud si přejete hromadně smazat několik atributů zboží, klikněte u jednoho ze záznamů na **Tři tečky** a klikněte na tlačítko **Vybrat více**. To Vám umožní vybrat více záznamů kliknutím na **Kroužek** před požadovaným záznamem. Jakmile máte vybrané všechny požadované záznamy, vyberte ikonku **Nastavit na smazat**, čímž se u vybraných záznamů nastaví hodnota pole akce na **Smazat**. Pro aplikování změn opět vyberete ikonku **Zápis dat**.

![Název](media/SetToDelete.png)

## Úprava atributů v Excelu

Další možností úpravy atributů je pomocí aplikace Excel.

Podle předchozí části si opět můžete vyfiltrovat a načíst data v Business Central. Tyto data si pomocí ikony **Export dat** můžete vyexportovat do excelového souboru. Popřípadě můžete dát **Export dat** bez předešlého filtrování a načtení dat, čímž získáte excel soubor s rozložením pro správu atributů.

![Název](media/ExcelAttributes.png)

V Excel souboru si můžete upravit hodnoty podle potřeby a poté kliknout na ikonu **Import dat** v Business Central a vložit zde excelový soubor. Po vložení se zobrazí data v Business Central. Hodnota pole **Akce** bude určena podle hodnoty, kterou jste zadali v Excelu. Pokud jste žádnou nezadali, tak se upraví podle změn provedených s daným atributem. Například pokud zadáte číslo zboží a název atributu existujícího atributu zboží, ale zadáte jinou hodnotu atributu než tu, která u něj teď je, hodnota pole bude automaticky změněna na hodnotu **Upravit**.

Takto naimportovaná data můžete zkontrolovat a upravit. Po kontrole vyberte ikonu **Zápis dat** a data se propíší ke  zboží.

![Název](media/ImportedAttributes.png)

**Viz také**

[Práce s atributy zboží](https://learn.microsoft.com/cs-cz/dynamics365/business-central/inventory-how-work-item-attributes)
