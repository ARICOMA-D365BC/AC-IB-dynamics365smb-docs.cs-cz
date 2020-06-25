# AC - Implementační báze - Nápověda

Tento repozitář slouží k evidenci nápovědy D365 Business Central.

## Obsah nápovědy

Pro psaní nápovědy k addonům dodržujte náležitosti:

 - Název souboru nápovědy se bude skládat z:
   - ```ac-nazevsouboru.md```
   - *(```ac-helpdesk.md```)*
 - Pro každý addon vzniknou dva soubory, jeden pro popis a použití, druhý pro nastavení.
   - Například: ```ac-helpdesk.md``` a ```ac-helpdesk-setup.md```
 - Struktura souborů nápovědy je:
   - Nadpis, krátký popis a kroky jak danou činnosti udělat.
   - viz. vzorová nápověda [Helpdesku](business-central/AC-ProductivityPack/ac-helpdesk.md)
 - ### Vlastnosti a tagy
    Každý dokumentu musí obsahovat hlavičku v následujícím tvaru:

    ```
    ---
    title: Czech Local Functionality - Advance payments and invoices | Microsoft Docs
    description: This section describes local functionality - Advance payments and invoices
    author: ac-kunes
    ms.service: dynamics365-business-central
    ms.topic: article
    ms.devlang: na
    ms.tgt_pltfrm: na
    ms.workload: na
    ms.search.keywords: Czech, Advance payment, Advance invoices, Payables, Finance, CZ, Cash
    ms.date: 15/05/2019
    ms.author: v-pejano
    ---
    ```
- Každý dokument musí nakonci obsahovat tabulku "Viz také"

    Pod každým souborem nápovědy bude odkaz na nadřazený balík a také odkaz na nastavení daného addonu nebo v opačném případě na obecný popis s návodem k použití.


    Příklad konce souboru HelpDesk (použití):


```
## Viz také
[HelpDeks - Nastavení](business-central/AC-IB/ac-helpdesk-setup.md)  
[AC Productivity pack](business-central/AC-IB/ac-productivity-pack.md)
```

- Pro základní editaci je zde [šablona](template.md).



## Pojmenovávání souborů

### Pravidla
- Nenechávat mezery mezi slovy v názvu souboru, používejte pomlčky.
- Používejte pouze malá písmena.
- Limit je maximálně 80 symbolů.
- Všechny soubory musí být ve formátu markdown (.md).



## Nahrávání souboru
Při každém nahrávání, editaci nebo mazání souborů je nutné podepsat každý **commit** svým jménem a popsat o jako událost se jedná. To je důležité zejména v případech, kdy používáte sdílené účty ke GitHubu a ne přímo své na jméno, kdy se Vaše jméno zaznamená automaticky při commitu.

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

## Základní syntaxe

### Obecný text

Text není třeba formátovat. Pro tučné písmo slouží dvě hvězdičky, pro kurzívu jedna. Mezi odstavci a nadpisy musí být volný řádek. Pro text na další řádek, je za větou třeba napsat dvě mezery (V případě enteru, text nezačíná na novém řádku).

```
*Kurzíva*
**Tučný text**
***Tučně a kurzíva***


# Téma

## Nadpis 1

Vzorový text, vzorový text, vzorový text, vzorový text, vzorový text, vzorový text, vzorový text.
```

### Nadpisy

Pro nadpisy slouží symbol dvojítého křížku. Dle počtu křížků se rozlišuji úrovně nadpisů. 

```
# Hlavní nadpis
## Název kapitoly
### Název podkapitoly
```


### Odrážky a seznamy

Odrážky pomocí pomlčky

  ```
  - odrážka 1
  - odrážka 2
  ```
### Číslovaný seznam

Stačí psát pouze číslo a tečku.

```
1. Položka
2. Položka
```

### Odkaz na jiný soubor

V hranatých závorkách je text, který se zobrazí a v závorce název souboru. (V tomto případě je soubor finance ve stejné složce.)

```
[Finance](finance.md)
```

### Názvy produktů a aplikací

Aby byly názvy produktů a aplikací jednotné, je potřeba používat malé zástupné soubory, ve kterých je uveden název. Zástupné soubory jsou ve složce  ve složce "INCLUDES". V případě změny názvu, se pouze jednou přepíše v zástupném souboru a tím bude automaticky aktuální ve všech dalších souborech kde je použit. 

Např. pro **Business Central** se vloží ```[!INCLUDE[d365fin]```(../../includes/d365fin_md.md)]```  

