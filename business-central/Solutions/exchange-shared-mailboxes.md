---
Title: ARICOMA SOLUTIONS - Sdílená poštovní schránka Exchange
Description: Slouží k importu příloh e-mailů z sdílené e-mailové schránky do Business Centralu, kde mohou být přílohy dále zpracovány.
Author: Ondřej.Slavík
Date: 23/03/2023
Product: dynamics365-business-central
Contentlocale: cs-cz
ms.search.keywords: Exchange, Shared, Mailbox, IN Buffer, Agent, E-Mail, Azure
---

# Sdílená poštovní schránka Exchange
> Aktualizace: 12.04.2023

Řešení **Sdílené poštovní schránky Exchange** umožňuje vytěžování e-mailových zpráv ze sdílené poštovní schránky do IN Bufferu, kde mohou být e-maily dále zpracovány.

> [!IMPORTANT]
> **Sdílená poštovní schránka Exchange je rozšířením funkcionality addonu Spooleru.**

## Příklady využití

-	Příchozí nákupní faktury ve formátu PDF, které dojdou do sdílené schránky, jsou automaticky založeny jako došlá pošta. Alternativně:
    - Jsou z nich vytvořeny Nákupní faktury v Business Central.
    - Jsou předány přes Kofax webovou službu OCR a zpět je založena faktura s daty.
-	Příchozí nákupní faktury ve formátu XML (např.EDI), které dojdou do sdílené schránky, jsou automaticky založeny jako došlá pošta a z nich vytvořeny Nákupní faktury v Business Central.
-	Příchozí prodejní objednávky a poptávky s přílohou, které dojdou do sdílené schránky, jsou automaticky založeny jako prodejní doklady s přílohou (publikované dokumenty) v Business Central.
-	Příchozí katalogy ve formátu XML/XLS, které dojdou do sdílené schránky, jsou automaticky zpracovány do struktur neskladovaného zboží v Business Central.
-	Další typické možnosti:
    -	Potvrzení objednávek
    -	Dodací listy 


## Použití
Po odeslání emailu na vybranou sdílenou poštovní schránku, která je nastavena jako výchozí pro vytěžování se automaticky vytěží a poté zmizí z došlé pošty, kde se přesune do archivu. V tento okamžik je možné e-mail považovat za **vytěžený** a je možné ho najít v **IN bufferu**.

Pro nalezení vytěženého e-mailu:
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **IN Buffer** a poté vyberte související odkaz.
2. Zde jsou v seznamu všechny soubory nahrané v IN Bufferu, budou zde i záznamy s přílohami z právě vytěženého e-mailu.
3. V následujících polích jsou vybrané informace, které jsou k souboru dostupné:

| Název pole         | Popis                                                 |
|--------------------|-------------------------------------------------------|
| **ID úkolu**       | Úloha, která bude zpracovávat danou přílohu           |
| **Zpracováno**     | Určuje, jestli byla příloha již zpracována            |
| **ID Agenta**      | Agent, který vytěžení provedl                         |
| **Název souboru**  | Úplný název přílohy                                   |
| **Předmět**        | Předmět e-mailu, ze kterého byla přílohy vytěžena     |
| **Příjemci**       | Příjemci e-mailu, ze kterého byla přílohy vytěžena    |
| **Příjemci kopie** | CC příjemci e-mailu, ze kterého byla přílohy vytěžena |

4. Pokud je vyplněna úloha v poli **ID úkolu**, pak po kliknutí na akci **Spustit úlohu** dojde ke zpracování přílohy a nastaví se hodnota pole **Zpracováno** na *Ano*.

Pro více informací k použití samotného IN Bufferu navštivte [stránku nápovědy](spooler.md).


## Vizte Také
[Exchange Shared Mailbox - Nastavení   ](exchange-shared-mailboxes-setup.md)  
[IN Buffer](spooler.md)  
[Productivity Pack](productivity-pack.md)
