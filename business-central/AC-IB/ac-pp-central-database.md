---
Title: "Centrální číselníky - použití"
Description: 
Author: AUTOCONT
Date: 14/02/2019
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# Centrální čísleníky - použití

Centrální databáze umožňuje pomocí modulu Spooler synchronizovat číselníky mezi různými NAV databázemi a společnostmi. Způsob synchronizace (jaké tabulky, pole, odkud a kam) je v NAV parametrizovatelný. 

## Sychronizace
Synchronizace probíhá buď automaticky při změnách v definovaných datových tabulkách nebo na ruční pokyn. 

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení tabulek centrální databáze**.
2. Klikněte na iknou **Synchronizovat** v záložce Akce.
3. Vyplňte filtry dle potřeby
4. Potvrďte pomocí OK.

### Ruční synchronizace:
Při ruční synchronizaci lze pomocí filtrů přesně specifikovat, jaké tabulky, odkud a kam chci aktuálně synchronizovat. 
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Synchronizovat data do systémů**.
2. Do dialogového okna nastavit všechny potřebné filtry, tedy:
   - **Číslo tabulky**,
   - **Id centrální databáze**,
   - **ID**, a další.
  
      Při ruční synchronizaci lze pomocí filtrů přesně specifikovat, jaké tabulky, odkud a kam chci aktuálně synchronizovat. Tato volba se uplatňuje hlavně při synchronizaci již existujících dat do nových systémů (migrace a parametrizace).
3. Potvrďte pomocí OK


|            Viz také             |                              Seznam                              |
| ------------------------------- | ---------------------------------------------------------------- |
| AC Productivity Pack            | [AC Productivity Pack](ac-pp-productivity-pack.md)               |
| Centrální číselníky - Nastavení | [Centrální číselníky - Použití](ac-pp-central-database-setup.md) |
