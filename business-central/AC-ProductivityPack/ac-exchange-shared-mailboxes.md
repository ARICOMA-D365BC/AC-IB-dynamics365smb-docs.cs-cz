---
Title: "Exchange Shared Mailbox"
Description: Slouží k importu příloh e-mailů z sdílené e-mailové schránky do Business Centralu, kde mohou být přílohy dále zpracovány.
Author: AC-Ondřej.Slavík
Date: 23/03/2023
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# Exchange Shared Mailbox

Řešení Exchange Shared Mailbox umožňuje vytěžování e-mailových zpráv ze sdílené poštovní schránky do IN Bufferu, kde mohou být e-maily dále zpracovány.

## Nastavení
Podrobnější informace jsou obsaženy v [tomto souboru](ac-exchange-shared-mailboxes-setup.md).

Nastavení sestává z vytvoření záznamu v tabulce Exchange Mailbox na stránce Exchange Mailboxes a spuštění agenta, kterému jako parametr komunikace nastavíme kód sdílené schránky. Jako ID codeunity agenta nastavíme 52068378.

Více informací k nastavení agentů jsou obsaženy v [tomto souboru](ac-spooler-setup.md).

## Použití
Odešlete e-mail na sdílenou poštovní schránku, kterou jste nastavili pro vytěžování. Jakmile nový e-mail zmizí z došlé pošty a přesune se do archivu, e-mail považujeme za *vytěžený*.

Nyní je k nalezení v IN Bufferu:
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **IN Buffer**.
2. Zde jsou v seznamu všechny soubory nahrané v IN Bufferu, budou zde i záznamy s přílohami z právě vytěženého e-mailu.
3. V následujících polích jsou některé informace, které jsou k souboru dostupné:

| Název pole         | Popis                                                 |
|--------------------|-------------------------------------------------------|
| **ID úkolu**       | Úloha, která bude zpracovávat danou přílohu           |
| **Zpracováno**     | Určuje, jestli byla příloha již zpracována            |
| **ID Agenta**      | Agent, který vytěžení provedl                         |
| **Název souboru**  | Úplný název přílohy                                   |
| **Předmět**        | Předmět e-mailu, ze kterého byla přílohy vytěžena     |
| **Příjemci**       | Příjemci e-mailu, ze kterého byla přílohy vytěžena    |
| **Příjemci kopie** | CC příjemci e-mailu, ze kterého byla přílohy vytěžena |

4. Pokud je vyplněna úloha v poli **ID úkolu**, pak po kliknutí na akci **Spustit úlohu** dojde ke zpracování přílohy a nahodí se hodnota pole **Zpracováno** na *Ano*.

Více informací k IN Bufferu lze nalézt v [tomto souboru](ac-spooler.md).

## Vizte Také
[Exchange Shared Mailbox - Nastavení   ](ac-exchange-shared-mailboxes-setup.md)  
[AC Productivity Pack](ac-pp-productivity-pack.md)