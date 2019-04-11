---
Title: "Centrální číselníky - Nastavení"
Description: 
Author: AUTOCONT
Date: 14/02/2019
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# Centrální čísleníky - Nastavení
Centrální databáze umožňuje pomocí modulu Spooler synchronizovat číselníky mezi různými NAV databázemi a společnostmi. Způsob synchronizace (jaké tabulky, pole, odkud a kam) je v NAV parametrizovatelný. 

## Nastavení centrální databíze

Základní nastavení centrální databáze obsahuje zadání informace o systému, společnosti a další.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení centrální databáze**.
2. Zadat:
   - **ID Systému** (název firmy, jak bude používán v oblasti komunikací )
   - **ID systému centrální databáze** – název firmy, která slouží jako řídící pro komunikačně-synchronizační proces.
   - **Centrální databáze** – pole určující, zda je firma sama centrální databází.
   - **Typ procesu** – nastavení kódu, který odpovídá kódu uvedenému v nastavení úloh spooleru v poli Process Type 
   - **Typ procesu** – okamžitá odpověď – nastavení kódu, který odpovídá kódu uvedenému v nastavení úloh spooleru v poli Process Type
3. Potvrďte pomocí OK.


## Nastavení cílových systémů

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Cílové systémy**.
2. Vyplnit pole:
    - **ID** – kód firmy pro komunikaci (musí být shodný v celém komunikačním řetězci
    - **Popis** – orientační popis k dané firmě
   - **Název databáze** – název databáze, ve které se firma nachází
   - **Název firmy** – správný název firmy uvedený jako jméno firmy v její databázi (může být odlišné od kódového označení)
3. Potvrďte pomocí OK


## Nastavení tabulek centrální databáze

Aplikace umožňuje synchronizovat jednotlivé tabulky a jejich vybraná pole, lze synchronizovat i pouze data spadající do určitého filtru. Synchronizace může být nezávislá a různá pro několik firem.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení tabulek centrální databáze**.
2. Vyplnit pole dle potřeby:
   - **Vypnuto** – toto pole umožňuje dočasně vypnout synchronizaci při ponechání nastavení.
   - **Priorita** – je možno nastavit pořadí pro odesílání k synchronizaci
   - **ID centrální databáze** – ID systému, který řídí synchronizaci dané tabulky. Pokud se toto ID nerovná ID systému firmy, ve které se nacházíme, nelze záznam měnit.
   - **Číslo tabulky** – číslo objektu datové tabulky v systému.
   - **Název tabulky** – toto pole se vyplní automaticky dle nastavení pole Číslo tabulky
   - **ID** – nezávislý kód, který je součástí primárního klíče a umožňuje nastavit rozdílné synchronizace pro jednu tabulku. Tento kód nemá další vazbu v systému a uživatel si ho může nastavit, jak chce (jméno firmy, skupina firem, typ synchronizace atd.).
   - **Typ synchronizace** – tato volba nabývá dvou hodnot – Push a Pull. Význam této volby je při zakládání nových dat do systému (změna dat a mazání dat jsou posílány vždy automaticky)
     - **Push** – volba znamená, že v případě změny dat jsou tato data ihned zaslána do podřízených systému a tam updatována (data jsou “tlačena”)
     - **Pull** – tato volba znamená, že nově vytvořená data nejsou zasílána ihned do podřízených systémů, ale uživatel si sám může “sáhnout” do centrální databáze a vybrat si, která dat z centrály chce ve svém systému (data jsou “tahána”)
    - **Pole** – tato volba určuje, zda se synchronizují některá nebo všechna pole
    - **Povol změnu** – pole určuje, zda uživatel v podřízené databázi může změnit hodnotu polí v daném záznamu (kontrola na synchronizovaných polích)
    - **Povol vložit** – pole určuje, zda uživatel v podřízené databázi může založit nový záznam v synchronizované tabulce
    - **Synchronizovat po** – pole je využíváno pro optimalizaci přenosu dat a vytížení systému; lze vybrat z hodnot Limitovaný počet záznamů a Všechny záznamy
    - **Limit záznamů** – pole je využíváno pro optimalizaci přenosu dat a vytížení systému
    - **Maximální počet záznamů v odpovědi** – pole je využíváno pro optimalizaci přenosu dat a vytížení systému; systém omezuje počet záznamů zasílaných jako odpověď z centrální databáze při dotazech na synchronizovaná data
3. Potvrďte pomocíOK.


## Nastavení konkrétních polí a jejich synchronizace

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení tabulek centrální databáze**.
2. V ribbonu tlačítko Nastavení, volba **Pole**.
3. Otevře se Nastavení polí centrální databáze
4. Nastavení polí:
   - **Číslo pole** – číslo je vybíráno z objektu dané tabulky a je jednoznačnou identifikací pole v celém systému (spolu s číslem tabulky). Při změnách v systému se čísla polí nemění
   - **Titulek pole** – toto pole se vyplní automaticky dle nastavení pole Číslo pole
   - **Povol změnu** – pole určuje, zda uživatel v podřízené firmě může měnit hodnotu tohoto konkrétního pole
   - **Pole primárního klíče** – pole je používáno interně, systém hodnotu nastavuje sám. Pole s tímto označením je povinně synchronizováno vždy
   - **Nevalidovat** – pole určuje, zda po synchronizace tohoto pole nastane tzv. validační proces (spuštění funkcí souvisejících se změnou hodnoty pole). Toto pole musí nastavovat velmi zkušený uživatel systému, špatné nastavení způsobí kolizní situace.
5. Potvrďte pomocí OK.


## Nastavení příjemců

Nastavení slouží v definování komunikace pro konkrétní záznam z nastavení synchronizace tabulek. Nastavení určuje komu a jaká data (datově) se budou synchronizovat.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení tabulek centrální databáze**.
2. V ribbonu záložka navigace, volba **Příjemci**.
3. Nastavení polí:
   -  **Vypnuto** – toto pole umožňuje dočasně vypnout synchronizaci při ponechání nastavení. Používá se hlavně při řešení kolizí nebo hromadném zpracování centralizovaných dat (importy, přejmenování atd.)
   -  **ID cílového systému** – vazba do nastavení cílových systémů, kód určuje, která firma bude příjemcem synchronizovaných dat při události
   -  **Filtr synchronizace tabulky** – v poli (a pomocném podřízeném formuláři) lze nastavit obecný filtr, který určuje, která data se budou synchronizovat (pouze data spadající do filtru)
   -  **Filtr oprávnění tabulky** – v poli (a pomocném podřízeném formuláři) lze nastavit obecný filtr, který určuje, která data bude moci uživatel v podřízené firmě modifikovat či zakládat
4. Potvrďte pomocí OK

## Nastavení relací centrální databáze
Toto nastavení slouží k určení relačních vazeb, které zajišťují, aby při synchronizace záznamů z určité tabulky proběhla synchronizace souvisejících záznamů (např. zboží + měrná jednotka zboží).

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení tabulek centrální databáze**.
2. V ribbonu záložka Nastavení, volba **Relace**.
3. Nastavení polí:
   - **Vypnuto** – toto pole umožňuje dočasně vypnout synchronizaci při ponechání nastavení. Používá se hlavně při řešení kolizí nebo hromadném zpracování centralizovaných dat (importy, přejmenování atd.)
   - **Číslo tabulky relace** – číslo objektu datové tabulky v systému. Tabulku lze vybrat z číselníku již synchronizovaných tabulek. Tato tabulka je relačně nebo logicky podřízena a její data mají vazbu k nadřízené tabulce
   - **Název tabulky relace** – toto pole se vyplní automaticky dle nastavení pole Číslo tabulky relace
   - **Filtr tabulky** – v poli (a pomocném podřízeném formuláři) lze nastavit obecný filtr, který určuje, která data budou synchronizována v rámci relační synchronizace
   - **Relace existuje** – pole, které určuje, zda je již definována relační vazba
   - **Relace** – pouze zobrazované formulářové pole, v jehož podřízeném formuláři lze definovat relační vazbu
4. Potvrďte pomocí OK.

   

|            Viz také             |                               Seznam                                |
| ------------------------------- | ------------------------------------------------------------------- |
| AC Productivity Pack            | [AC Productivity Pack](ac-pp-productivity-pack.md)                  |
| Centrální číselníky - Použití | [Centrální číselníky](ac-pp-central-database.md)     |