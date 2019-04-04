# AC - Implementační báze - Nápověda

Tento repozitár slouží k evidenci nápovědy D365 Business Central 

## Obsah nápovědy

Pro psaní nápovědy k addonům dodržujte náležitosti:
 - Název souboru nápovědy se bude skládat z:
   - ```ac-nazevbaliku-nazevsouboru.md```
   - *(```ac-pp-helpdesk.md```)*
 - Pro každý addon vzniknou dva soubory, jeden pro popis a použití, druhý pro nastavení.
   - Například: ```ac-pp-helpdesk.md``` a ```ac-pp-helpdesk-setup.md```
 - Struktura souborů nápovědy je:
   - Nadpis, krátký popis a kroky jak danou činnosti udělat.
   - viz. vzorová nápověda [Helpedsku](business-central/AC-IB/ac-pp-helpdesk.md)
 - ### Vlastnosti a tagy
    Každý dokumentu musí obsahovat hlavičku v následujícím tvaru

    ```
    ---
    Title: "Nazev_souboru"
    Description: 
    Author: AUTOCONT
    Date: 04/04/2019
    Product: dynamics365-business-central
    Contentlocale: cs-cz
    ---
    ```
- Každý dokument musí nakonci obsahovat tabulku "Viz také"

    Pod každým souborem nápovědy bude odkaz na nadřazený balík a také odkaz na nastavení daného addonu nebo v opačném případě na obecný popis s návodem k použitíí.


    Příklad konce souboru HelpDesk (použití):

    |       Viz také       |                                  Seznám                                   |
    | -------------------- | ------------------------------------------------------------------------- |
    | Helpdesk - Nastavení | [HelpDeks - Nastavení](business-central/AC-IB/ac-pp-helpdesk-setup.md)    |
    | AC Productivity Pack | [AC Productivity pack](business-central/AC-IB/ac-pp-productivity-pack.md) |

- Pro základní editaci je zde [šablona](template.md).



## Pojmenovávání souborů

### Pravidla
- Nenechávat mezery mezi slovy v názvu souboru, používejte pomlčky.
- Používejte pouze malá písmena.
- Limit je maximálně 80 symbolů.
- Všechny soubory musí být ve formátu markdown (.md).



## Nahrávání souboru
Při každém nahrávání, editaci nebo mazání souborů je nutné podepsat každý **commit** svým jménem a popsat o jako událost se jedná.

  ### Commit Changes

  *Martin Kuneš - Náhrání nových úprava stávajících souborů*

  *Přidány nové soubory nápovědy a aktualizace dle legislativy*.

## Struktura souborů repoziáře

Ujistěte se, že se nacházíte ve správné větvi.
  - Soubory ukládejte do **master Branche**

Soubory standardní nápovědy nahrávejte do:
 - business-central/...
 - *business-central/get-started.md*

Soubory pro addony nahrávejte do:

 - business-central/nazev-slozky-baliku/
 - *business-central/AC-IB/ac-pp-productivity-pack.md*

