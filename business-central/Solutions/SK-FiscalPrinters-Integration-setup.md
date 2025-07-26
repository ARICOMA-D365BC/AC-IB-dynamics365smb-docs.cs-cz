---
title: SK Fiscal Printers Integration - Setup
description: SK Fiscal Printers Integration - Setup
author: RobertJelen
date: 07/31/2025
reviewer: janousek
ms.service: dynamics-365-business-central
ms.search.keywords: Czech, Slovak, SK Fiscal Printers Integration, Streamline Tools
---
# Nastavení integrace s SK fiskálními tiskárnami pro Dynamics 365 Business Central

> Aktualizace 31.07.2025

Integrace s fiskálními tiskárnami VAROS je postavena na funkčnosti programu Tlačový manažér od firmy VAROS. Tento je třeba nainstalovat v prostředí firmy (viz [Manuály](http://www.varos.sk/manualy.php)) přímo na počítači, ke kterému je tiskárna připojena (typicky pomocí USB). Každá fiskální tiskárna musí být rovněž připojena k internetu pomocí LAN (popř. přes Wifi).

## Nastavení oprávnění uživatelů

Sady oprávnění:

- FP_BASIC_ACC: Fiskální tiskárny - Základ
- FP_SETUP_ACC: Fiskální tiskárny - Nastavení

## Nastavení fiskálních tiskáren

Každé fyzické zařízení musí být zaevidováno v číselníku Fiskální tiskárny. Popis nastavení dále odpovídá nejběžnější konfiguraci, kdy program *Tlačový manažér* je instalovaný na každém počítači, ke kterému je připojena fiskální tiskárna pomocí USB portu.

> [!IMPORTANT]
> API komunikace s fiskálními tiskárnami vyžaduje API klíč, pro který kontaktujte obchodní oddělení Aricoma na adrese [bc_sales@aricoma.com](mailto:bc_sales@aricoma.com).

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Fiskální tiskárny** a poté vyberte související odkaz.
2. Na stránce Fiskální tiskárny klikněte na funkci *Nový* a vytvořte novou fiskální tiskárnu.
3. Zadejte **Kód** a **Popis** fiskální tiskárny.
4. Zadejte 0,05 v poli **Minimální částka hotovosti**.
5. Zadejte 0,05 v poli **Přesnost zaokrouhlení hotovosti**.
6. Nastavte sazby DPH hladin v polích **DPH % číslo 1** až **DPH % číslo 4** identicky jakou jsou nastaveny v nastavení *Tlačového manažéra*.
7. V poli **Způsob integrace** zvolte *Varos API*.
8. Vyplňte platné údaje v poli **Adresa integrační služby**; pro účely testovacího režimu nastavte [https://rps.test1.bts1.rdm.varos.sk](https://rps.test1.bts1.rdm.varos.sk).
9. V poli **API klíč integrační služby** zadejte klíč (heslo), které jste získali od Aricoma.
10. Nastavte **Časový limit integrace (s)** na hodnotu 60.
11. V poli **ID zařízení** zadejte výrobní kód fiskální tiskárny Varos.
12. V poli **Požadovaná platnost párování** zadejte počet dnů platnosti, např. 365 dní.
13. Spusťte akci *Spárovat se zařízením* (VAROS API). Varos tiskárna vygeneruje a vytiskne ověřovací kód, který zadáte do dialogu v BC a potvrdíte. Ověřte, že se u fiskální tiskárny nastavil příznak **Spárováno se zařízením** na Ano.
14. V poli **Párování platné do** systém automaticky doplní platnost propojení s fiskální tiskárnou.

> [!NOTE]
> S ohledem na legislativní úpravu na Slovensku vztahující se k úpravě výše zaokrouhlení pokladních dokladů v hotovosti na 0,05 centů, je třeba v systému nastavit i platební odchylku dle měny ve výši 0,05.

## Propojení fiskálních tiskáren na Bankovní účty / Pokladny

Pro zajištění odsouhlasení dat v rámci integrace je třeba mít samostatnou kartu bankovního účtu nebo pokladny pro každý používaný typ platidla (Hotovost, Karta, Stravenka,…).

> [!NOTE]
> Každý způsob má své výhody a nevýhody, vyzkoušejte si, který způsob bude pro vaše firemní procesy nejvhodnější. I vzhledem k jednoduchosti použití modulu Pokladna z české lokalizace je toto spojení v poslední době více preferované.

### Nastavení pokladen

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Pokladny** a poté vyberte související odkaz.
2. Na stránce **Pokladny** vyberte příslušný záznam a klikněte na akci Úpravy.
3. V poli **Kód fiskální tiskárny** zadejte odpovídající fiskální tiskárnu.
4. V poli **Platební prostředek fiskální tiskárny** vyberte příslušný typ dle nastavení Tlačového manažéra.

Dále nezapomeňte na kartě pokladny nastavit zaokrouhlení v poli **Kód způsobu zaokrouhlení**.

> [!IMPORTANT]
> Při použití funkcionality pokladních dokladů vznikají Fiskální položky pouze při účtování pokladního dokladu.

### Nastavení bankovních účtů

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Bankovní účty** a poté vyberte související odkaz.
2. Na stránce **Bankovní účty** vyberte příslušný záznam a klikněte na akci Úpravy.
3. V poli **Kód fiskální tiskárny** zadejte odpovídající fiskální tiskárnu.
4. V poli **Platební prostředek fiskální tiskárny** vyberte příslušný typ dle nastavení Tlačového manažéra.

## Nastavení způsobů plateb

V seznamu Způsoby platby je třeba nastavit pro všechny kombinace fiskální tiskárny a platebních prostředků způsoby, které bude následně možné použít na prodejních dokladech k jejich vyrovnání v průběhu účtování.

V případě napojení fiskální tiskárny na kartu Bankovního účtu zvolte v poli **Typ protiúčtu** hodnotu Bankovní účet a v poli **Číslo protiúčtu** vyberte číslo karty bankovního účtu. Pokud bude fiskální tiskárna napojena na “běžnou” pokladnu tak, v poli **Kód pokladny** vyberte požadovanou hodnotu (v poli **Akce pokladního dokladu** zvolte zda-li doklad vydat či účtovat).

> [!IMPORTANT]
> V poli **Fiskální daňový doklad** nastavte, zda-li chcete doklad registrovat jako daňový doklad v eKASA nebo pouze evidovat jako „úhradu faktury“ (tedy bez informací o DPH, jejichž nositelem je daňový doklad v BC).

## Nastavení účtování DPH fiskální tiskárny

Následující tabulka zobrazuje specifické DPH režimy použitelné na fiskálních tiskárnách a instrukce, jaké parametry nastavit pro příslušné kombinace DPH účtoskupin:

| DPH režim                    | Instrukce pro nastavení                 |
|------------------------------|-----------------------------------------|
| Sleva                        | V poli **Typ řádku fiskálního dokladu** vyberte „B – Sleva“. |
| Poukaz                       | V poli **Typ řádku fiskálního dokladu** vyberte „D – Poukaz“. |
| Vratné obaly                       | V poli **Typ řádku fiskálního dokladu** vyberte „V - Vratné obaly“. |
| Zaokrouhlení                 | V poli **Typ řádku fiskálního dokladu** vyberte „RND – zaokrouhlení“.<br>V poli **Důvod osvobození od DPH fiskálního dokladu** vyberte „N – Osvobozeno od daně“. |
| Cestovní kanceláře                | V poli **Důvod osvobození od DPH fiskálního dokladu** vyberte „K - Cestovní kanceláře“. |
| Osvobození od daně           | V poli **Důvod osvobození od DPH fiskálního dokladu** vyberte „N – Osvobozeno od daně“. |
| Přenesení daňové povinnosti  | V poli **Důvod osvobození od DPH fiskálního dokladu** vyberte „P – Přenesení daňové povinnosti“. |
| Použité zboží                | V poli **Důvod osvobození od DPH fiskálního dokladu** vyberte „T - Použité zboží“. |
| Umělecká díla                | V poli **Důvod osvobození od DPH fiskálního dokladu** vyberte „U – Umělecká díla“. |
| Zběratelské předměty a starožitnosti                | V poli **Důvod osvobození od DPH fiskálního dokladu** vyberte „Z - Zběratelské předměty a starožitnosti“. |

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení účtování DPH fiskální tiskárny** a poté vyberte související odkaz.
2. Na stránce **Nastavení účtování DPH fiskální tiskárny** vytvořte řádky pro relevantní kombinace DPH účtoskupin reprezentující specifické režimy DPH využívané firmou ve spojitosti s fiskálními tiskárnami.

## Viz také

[Integrace s SK fiskálními tiskárnami](SK-FiscalPrinters-Integration.md)  
[Streamline Tools](streamlinetools.md)  
[ARICOMA řešení](solutions.md)
