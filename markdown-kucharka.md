
# Psaní souboru nápovědy v jazyce MarkDown
Soubory nápovědy se vytvářejí v jazyce MarkDown.

## Nadpisy
Použijte pro nadpisy symbol ```#```.

Příklady:
```#``` Nadpis úrovně 1 vypadá takto:
# Nadpis 1

```##``` Nadpis úrovně 2 vypadá takto:
## Nadpis 2

```###``` Nadpis úrovně 3 vypadá takto:
### Nadpis 3


## Odrážkový seznam
Použijte symbol ```-``` pro vytvoření seznamů, například:

Následující možnosti:
```
- první možnost
- druhá možnost
- třetí možnost
```

## Číslované seznamy
Pro číslované seznamy použijte číslo a tečku. Nevkládejte volné řádky mezi jednotlivé řádky.

```
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Kategorie uživatelů**.
2. Naplnit pole: **Kód**, **Popis** a **Váha**.
3. Potvrďte pomocí OK.
```

## Tučné písmo a kurzíva
Použijte ```**tučně**``` a ```*kurzíva*```

## Tabulky
- Pro tabulky použijte tuto strukturu.

```
|  Viz   |  Také   |
| ------ | ------- |
| <text> | <odkaz> |
|        |         |
```

- Pro vnořené tabulky použijte a seznamy použijte HTML syntaxi. Markdown moc dobře tabulky nepodporuje. 

## Struktura komentářů
Vhodné pro označení textu/kódu, který není připraven k zveřejnění.
```
<!-- Komentář -->
```
Příklady
```
<!-- [Nastavení plateb](nastaveni-plateb.md)-->
<!-- Tento text je náhodně generovaný, je delší než jeden řádek a slouží pouze pro demonstrační účely.-->
```
## Odkazy
Přímý odkaz na soubor ve stejné sloužce.

Tyto odkazy mají tento tvar ```[Text odkazu](nazevsouboru.md)```.

Příkald:
```[Nastavení financí](nastaveni-financi.md)```


## Odkaz na nadpis souboru v podsložce

Tento odkaz má tento tvar ```[Text odkazu](Podsložka/nazevsouboru.md)```.


Například se chcete odkazovatz na nastavení financí z nastavení aplikace, struktura bude vypadat takto:

- Článek
    - nastaveni-aplikace.md
- NastaveniFinanci
    - nastavení-financi.md

Odkazu bdue vypadat takto:
```[Nastavení financí](NastaveníFinanci/nastaveni-financi.md)```

## Odkaz na nadpis v jiné složce než zdrojový soubor

Tento odkaz má tento tvar ```[Text odkazu](../složka/nazevsouboru.md)```.

## Odkaz na nadpis ve stejném dokumentu
Ve jednom dokumentu můžete odkazovat na nadpis.

```[Text odkazu](#cilovy-odkaz)```

## Odkazování na MSDN
vynechejte závorky kolem verze NAV. 
Příklad:  
MSDN URL: ```https://msdn.microsoft.com/en-us/library/hh173988(v=nav.80).aspx```  
zadané v MarkDownu: ```https://msdn.microsoft.com/en-us/library/hh173988.aspx```


## TOC
Struktura TOC souboru má tvar:

```
#[Přehled](prehled.md)
 ##[Název 1](nazev-1.md)
 ##[Název 2](nazev-2.md)
 ##[Název 3](nazev-3.md)
 ##[Název 4](nazev-4.md)
```
