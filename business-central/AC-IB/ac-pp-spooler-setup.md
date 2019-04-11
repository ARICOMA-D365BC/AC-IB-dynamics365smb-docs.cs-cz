---
Title: "Spooler - Setup"
Description: 
Author: AUTOCONT
Date: 15/03/2019
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# Spooler - Nastavení

Modul Spooler slouží pro komunikaci systému Microsoft Dynamics NAV s externími systémy nebo datovými zdroji.
Má dvě základní funkce:
- slouží jako úložiště nezpracovaných úloh a jako archív komunikačních dokumentů 
- slouží jako nástroj pro různé typy komunikací a pro zpracování příchozích dokumentů

Komunikace může probíhat jak z NAV do externího systému nebo naopak z externího systému do NAV. Spooler umožňuje aktuálně využívat celkem 5 komunikačních protokolů (TCP , http, FileSystem, webservices, email).


## Nastavení Spooleru

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení spooleru**.
2. Vyplnit **Source System (Cílový systémm)** - jak se daný systém v komunikaci identifikuje.
3. Source System se vybírá z tabulky **Cílové systémy**, kde jsou všechny, s kterými Spooler komunikuje.
4. V nastavení Spooleru je několik nutných polí pro vyplnění:
   - Pole **Nezpracované In úlohy** a **Nezpracované Out úlohy** zobrazují počet nezpracovaných úloh v In Bufferu nebo Out Bufferu.
   - Pole **Počítat velikost dokumentu IN Bufferu** a **Počítat velikost dokumentu OUT Bufferu** určují, zda se mají počítat velikosti dokumentů zobrazovaných v IN a OUT Bufferech.
   - Pole **Archivovat IN Buffer při zpracování** a **Archivovat IN Buffer** při expiraci určují, kdy a jestli se mají položky IN Bufferu archivovat.
   - Pole **Archivovat OUT Buffer při zpracování** a **Archivovat OUT Buffer při expiraci** určují, kdy a jestli se mají položky OUT Bufferu archivovat.
   - Pole **Nehledat příchozí zprávu v archívu** určuje, zda se má hledat příchozí zpráva dle jednoznačného identifikátoru GUID (ID dokumentu) v archivovaných položkách.
   - Pole **Nehledat odpověď v archívu** určuje, zda se má hledat odpověď dle jednoznačného identifikátoru GUID (ID dokumentu) v archivovaných položkách.
   - Pole **Maximální počet položek v Bufferu** omezuje počet zobrazovaných položek v In-Bufferu a Out-Bufferu ve specifických stránkách Položky In-bufferu a Položky Out-bufferu (jde o kombinované stránky zobrazující data z více tabulek, z důvodu výkonu je tam tato limitace, tyto Page slouží jen pro hledání v případě problémů). Pokud je počet položek větší než zde zadané maximum, stránka nezobrazí žádný záznam. Pokud se zadá hodnota 0, jedná se o neomezený počet položek v Bufferech. 
   - Pole **Interval spouštěče agentů** (s) definuje časový interval, ve kterých se spouštěč agentů pokouší spouštět agenty. Výchozí hodnota je 60s, pokud je pole prázdné použije se 60s.
   - **Výchozí emailová adresa**– adresa odesilatele emailu v případě typu komunikace email. Pokud zůstané prázdné, vezme výchozí údaj z nastavení SMTP.
   - **Výchozí emailové jméno**  – jméno odesilatele emailu v případě typu komunikace email.
5. Potvrďte pomocí OK.

## Přihlašovací údaje Spooleru

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Přihlašovací údaje spooleru**
2. Do polí zadat:
    - Kód (uživatele)
    - Uživatelské jméno
    - Heslo
3. Potvrďte pomocí ok

## Nastavení Agentů

Agenti jsou
   - Aktivní – periodicky časově spouštěné
   - Pasivní – spouštěné vnější událostí
     - IN agent TCP
     - IN agent webservice

### Druhy agentů

-	IN agent TCP – čeká na portu na příchozí komunikaci, musí běžet samostatné na samostatném NST (service) a musí běžet v NAS relaci, (např. dotaz webshopu na cenu produktu, na objednávku, apod.), pro zpětnou kompatibilitu s předchozími verzemi NAV
-	IN agent Filesystem – v časové periodě testuje existenci souboru na disku nebo síti a ten následně uloží do IN bufferu nebo je zpracuje. Např. soubor s údaji o nové zakázce, produktu, apod.
-	IN agent http timer - v časové periodě pravidelně kontaktuje http/https službu a vyžádá si data, které uloží do IN bufferu nebo je zpracuje. (např. dotaz na kurzovní lístek, apod.)
-	IN agent webservice - čeká na adrese webservice na příchozí komunikaci, kterou uloží do IN bufferu nebo je zpracuje.  (např. dotaz webshopu na cenu produktu, na objednávku, apod.), výhodou je paralelní zpracování více dotazů najednou (multithread).
-	Out agent – prochází OutBuffer a odesílá položky. (např. el. faktury, číselníky, atd.)
-	Work agent – procesní – prochází IN buffer a zpracovává položky. Vlastní způsob zpracování musí být následně vyvinut pro konkrétní implementaci


### Základní nastavení Agentů

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Agenti**.
2. Nastavit pole:
    - Pole **ID agenta** a **Popis** slouží k evidenčnímu rozlišení agentů.
    - Pole **Typ** rozlišuje druhy agentů:
        - **In** – slouží pro příchozí komunikace. Přijímá zprávy z okolí a ukládá je do IN Bufferu.
        - **Out** – prochází OUT Buffer a odesílá zprávy do okolí.
        - **Procesní** – prochází úlohy v IN Bufferu, zpracovává úlohy IN Bufferu a ukládá případné odpovědi do OUT Bufferu k odeslání.
    - Pole **ID codeunity agenta** se nastaví automaticky, ale dá se přepsat na jinou.
    - Pole **Druh komunikace** a **Parametr komunikace** je pouze pro **IN Agenty**. Pole Parametr komunikace se nastavuje dle zvoleného druhu komunikace:
        - **TCP** – port [,] Timeout [,] adresa webové sl. Pro přesměrování [,] ID Přihlášení
          - Složité pro popsání, ext.DLL komponenta která sleduje TCP komunikaci a předá ke zpracování (shazuje NAV), proto možnost přesměrování na ws (jen pro zpětnou kompatibilitu, raději nepoužívat.)
        - **Disk** – cesta [čárka] filtr souboru
        - **HTTP** – adresa http
3. Potvrďte pomocí OK.

Pro **Diskového** a **HTTP** (timer) **In agenta** je možné nastavit ID výchozí úlohy pro každý parametr komunikace, aby bylo možné rozlišit, jakým typem úlohy bude přijatá zpráva následně zpracována.
Všichni agenti jsou buď tzv. pasivní, nebo aktivní. Aktivní agent se sám aktivuje a vykonává nějakou činnost. Pasivní agent čeká na podnět zvenčí, na nějaké přerušení systému a na tuto změnu reaguje.
Pasivní agent běží sám na NST v NAS relaci. IN Agent TCP je pasivní agent.
- Pole **Interval komunikace** (s) slouží pro aktivní agenty. Určuje, v jakém časovém intervalu se aktivuje a vykonává činnost.
- Pole **Přídavné parametry komunikace** využívají v podstatě aktivní agenti. Někteří agenti mohou mít více parametrů. Např. Diskový agent může sbírat data z více adresářů. 
- Pro IN Agenty slouží pole **ID výchozí úlohy**. Pokud se úloha Spooleru nenajde dle hlavičky XML, vezme se výchozí úloha.
- Pole **Změnit agenta po počtu chyb** je pouze pro OUT Agenty a Procesní Agenty. Pokud se agentovi nepodaří úlohu zpracovat (např. 5 chyb) lze nastavit do pole Změnit na agenta ID nového agenta, který se pokusí úlohu zpracovat.
- Pole **Logovat** určuje, zda a jak se zapisuje do aplikačního logu. Hodnoty mohou být Nikdy, Dle úlohy a Vždy.
- Pole O**dpovídat pouze na XML** je pro IN Agenty TCP a ukazuje, zda se bude odpovídat pouze na XML.
- Pole **Spustit na pozadí** pro aktivní agenty, které poběží v background session a budou spuštěny agent starterem.
- Pole **Automaticky spustit z NAS** pro aktivní agenty říká, že budou spuštěny agent starterem. 
- Pole **Spustit na tomto NAS počítači** a** Spustit na této NAS instanci** - umožňuje určit konkrétní počítač a NAS instanci, kde se spustí v případě, že používám větší počet NAS. 
- **Stav** – stav daného Agenta (,Spouští se, Běží, Zastavuje se, Zastaven, Pozastaven).
- Další informativní a nastavovací pole - Poslední signál, ID instance serveru, ID relaci, Běži pod uživatelským ID, Logovat běh delší než (s), atd.

Na stránce Agenti lze Agenty spustit nebo zastavit pomocí akcí:
-	Spustit 
-	Zastavit
-	Spustit zde


### Způsob zprovoznení agentů

Způsob zprovoznění agentů:

1. **IN Agent webová služba**
   - Na stránce Webové služby vypublikovat webslužbu s názvem Spooler
   - Musí k ní existovat agent v tabulce agenti (se stejnou CU jako vypublikovaná, v AP máme univerzální CU co přijme xml)
   - Musím běžet alespoň jedna NST s nastaveným SOAP
2. **Agent v NAS relaci** – jakýkoli další agent (TCP IN Ag. Lze jen takto)
   - Na NST vytvoři instanci NAS, zadat Default Company  a Startup CU = CU v Agentovi, Startup metoda = NasStart, StartUp Argument = kód agenta
   - Uživatelský účet pod kterým je NAS spuštěn musí mít práva do NAV
3. **Agent starter** (doporučená varianta pro všechny aktivní agenty) 
   - Startup CU = 52068364 
   - Musí být vyplněna Service Default Company
   - Uživatelský účet pod kterým je NAS spuštěn musí mít práva do NAV
   - Agent starter si už spustí sám ostatní agenty v různých společnostech


## Nastavení Úloh spooleru

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Úlohy spooleru**. 
2. Vyplnit pole tabulky:
   - Pole **ID úlohy** evidenčně označuje danou úlohu spooleru.
   - Pole **Typ** určuje, zda je daná úloha pro IN Buffer – In nebo Out pro OUT Buffer.
   - Pole** Druh komunikace** slouží pouze pro OUT úlohy. Druh komunikace je podobný jako u agentů, tzn. Disk, HTTP, TCP, E-mail a webová služba.
   - **Popis** slouží k popsání dané úlohy.
   - Pole **Výchozí priorita** označuje, v jakém pořadí se úlohy zpracovávají.
   - Pole **ID Agenta** určuje, který agent bude úlohu spooleru zpracovávat. U IN úloh to bude Procesní agent a u OUT úloh to bude OUT agent.
   - Pole **ID codeunity zpracování** označuje, kterou codeunitu agent spustí nad položkou Bufferu. U OUT úloh se pole vyplní automaticky při výběru druhu komunikace.
   - 	Dle polí **Typ procesu** a **Typ dokumentu** se rozpoznává úloha. Slouží k tedy nalezení úlohy dle hlavičky XML dokumentu v Bufferu.
   - Pole **Výchozí cílový systém** se může vyplnit pouze pro OUT úlohy, pokud se cílový systém neurčí přímo z hlavičky XML dokumentu.
   - Pole **Číslo posledního dokladu** využívá systém interně, nenastavuje se a slouží pouze pro OUT úlohy.
   - Do pole **Expirovat po** se zadává doba trvání (proměnná Duration).
   - Pole **Logovat** určuje, zda a jak se zapisuje do aplikačního logu. Hodnoty mohou být Nikdy, Dle úlohy a Vždy.
   - Pole **Typ odpovědi** využívají pouze IN úlohy. 
     - Potvrzení – vloží se úloha do IN Bufferu
     - Výsledek – vloží se úloha do IN Bufferu a okamžitě se spustí zpracování.
   - Pole **Čekat po množství chyb** a **Čekací doba po chybách** slouží k určení, po kolika chybách se bude jak dlouho čekat s dalším pokusem o zpracování. 
   - Pole **ID codeunity** při vložení – umožňuje spustit  codeunitu při vložení do Bufferu.
   - 	Pole **Nenutit posloupnost odesílání** – pokud zaškrtnuto, tak se položky úlohy se neúčastní výpočtu pro vynucení posloupnosti odesílání (zaškrtnout pouze na úlohách, kde je vysloveně nežádoucí vynucovat posloupnost odesílání. Např. pro odesílání dokladů E-Mailem (zde nemusí platit, že když neprojde odeslání jednoho dokladu (třeba kvůli velikosti), tak potom neprojde odesílání dalších)
   - Polem **Kódování XML** určujeme, jak bude XML dokument kódován.
   - 	Pole **Nearchivovat při zpracování a Nearchivovat při expiraci** nám určují, kdy a jestli se mají položky Bufferu archivovat. Tyto pole mají vyšší prioritu než pole v nastavení spooleru.
   - Pole **Nehledat příchozí zprávu v archívu a Nehledat odpověď v archívu** slouží k zabezpečení komunikace. Viz popis nastavení spooleru.

### Cílové úlohy Spooleru

Cílové úlohy spooleru se zobrazují na formuláři Úlohy spooleru na tlačítku **Úloha – Cílové systémy**. Týká se pouze OUT úloh.
Zde je vyplněno s kým komunikuji (pole ID cílového systému) a s jakým parametrem (pole **Parametr komunikace**). 
Dle zvoleného druhu komunikace nastavují parametry:
- TCP – IP adresa [čárka] port [čárka] Timeout
- Disk – cesta [čárka] přípona
- HTTP – adresa http
- E-mail – emailové adresy
- Webová služba – adresa ws[, Kód přihlášení]
  
Pro druh komunikace E-mail platí: Při vložení úlohy do OUT Bufferu lze přenastavit (přepsat) parametr komunikace pro konkrétní položku v OUT Bufferu. Dále je možno vyplněním tabulky „OUT Buffer Dokument“ odeslat více souborů příloh v jednom e-mailu z jedné položky OUT Bufferu.

|       Viz také       |                       Seznam                       |
| -------------------- | -------------------------------------------------- |
| AC Productivity Pack | [AC Productivity Pack](ac-pp-productivity-pack.md) |
| Spooler              | [Spooler](ac-pp-spooler.md)                        |