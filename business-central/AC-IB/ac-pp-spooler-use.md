---
Title: "Spooler - Použití"
Description: 
Author: AUTOCONT
Date: 15/03/2019
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# Spooler - Použití

## Použití In a OUT BUfferu

Každý záznam v tabulce IN Bufferu i OUT Bufferu má přiděleno jedinečné číslo **ID dokumentu**. Je zde také zobrazen **Typ procesu** a **Typ dokumentu**. Dále je v záznamu vidět jaká úloha se zpracovává – **pole ID úlohy**, jakým agentem je zpracovávána – **pole ID agenta**. Stav záznamu označuje pole **Zpracováno**. Nabývá hodnot Ne, Ano, Expirováno a Odloženo. Pole **ID zdrojového systému** nám v IN Bufferu ukazuje odkud (z jakého systému) daný záznam pochází. 

Na OUT Bufferu je pole **Nenutit posloupnost odesílání** - tady je možno kódem vyjmout položku Bufferu z výpočtu o posloupnosti odesílání. Při odesílání dokladů z OUT Bufferu se snaží OUT Agent držet posloupnost odesílání takto:

- Pokud se nějaká položka nepodaří odeslat, tak se neodešlou ani žádné další položky směřující ke stejnému cíli (dle polí ID cílového systému a Parametr komunikace z nastavení příjemců, bez ohledu na úlohu). Funkcionalita posloupnosti odesílání pracu-je tak, že pokud je v OUT Bufferu vyplněno pole Parametr komunikace, tak se jede dle tohoto pole.

Držení posloupnosti odesílání ve spooleru má 2 základní důvody:

1.	Dodrží posloupnost odesílaných dokumentů
2.	Šetří čas serveru v případě nefunkčnosti spojení - pokud je potřeba poslat větší množství dokumentů na jedno místo (například TCP adresa/port) a spojení není funkční, tak pokus o odeslání může trvat i několik vteřin a  je vysloveně nežádoucí aby se tento pokus opakoval s každou položkou - v krajním případě to může zastavit server i na několik hodin => používat pole Nenutit posloupnost odesílání po důkladné úvaze 


Na formuláři stránce IN Buffer je v záložce Akce položka **volba Out Buffer** – odpověď – systém zobrazí jakým záznamem v OUT Bufferu odešla odpověď na danou úlohu v IN Bufferu. Volba Out Buffer – dotaz zobrazuje OUT úlohy – jakou úlohou se ptal. Vyhledává se vždy dle ID dokumentu.

Dále je zde možnost daný záznam expirovat, změnit poznámku nebo ručně odeslat do archívu.

Pokud je daný záznam ve stavu Zpracováno = Ne, tak je možno danou úlohu spustit z formuláře ručně. Provádí se přes volbu **Funkce – Spusť úlohu**. Tato funkčnost je pouze na formuláři IN Bufferu. Program pak umožňuje zobrazit chybu, kvůli které se úloha nezpracovala. Pokud se po ručním spuštění úloha zpracovala, je zřejmě problém s aplikačním serverem (např. uživatelská práva). Na formuláři OUT Bufferu je funkce Odešli úlohu, která umožňuje danou úlohu odeslat z OUT Bufferu.

Úlohy do IN Bufferu nebo OUT Bufferu lze vložit i ručně. Umožňuje to funkcionalita na tlačítku **Funkce – Vlož úlohu**.
 
V poli Dokument se vybírá dokument úlohy. Pokud se dle hlavičky dokumentu najde úloha spooleru, tak se automaticky nastaví údaje ve formuláři např. ID agenta, Typ procesu, Typ dokumentu. Pokud ne, tak se musí ručně nastavit.

**Pole Není XML** nás informuje, zda přiřazený dokument není nebo je XML. 

**Pole Priorita** má pouze evidenční charakter.

##  Archiv IN a OUT Buffer

Do archívu se položky dostanou automaticky při zpracování, pokud je to nastaveno v úloze spooleru (Nearchivovat při zpracování, Nearchivovat při expiraci) nebo v nastavení spooleru (Archivovat IN Buffer při zpracování a Archivovat IN Buffer při expiraci, Archivovat OUT Buffer při zpracování a Archivovat OUT Buffer při expiraci).

Do archivu se položky dostanou také ručně z formuláře IN Bufferu nebo OUT Bufferu pomocí funkce Přesuň do archívu.

Další možností, jak dostat položky do archívu je pomocí reportů R4002900 Move IN Buffer to Archive a R4002901 Move OUT Buffer to Archive.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Archivovaný IN Buffer nebo Archivovaný OUT buffer**.

|       Viz také       |                       Seznam                       |
| -------------------- | -------------------------------------------------- |
| AC Productivity Pack | [AC Productivity Pack](ac-pp-productivity-pack.md) |
| Spooler - Nastavení  | [Spooler - Nastavení](ac-pp-spooler-setup.md)      |