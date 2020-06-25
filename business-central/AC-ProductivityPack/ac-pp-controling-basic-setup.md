---
Title: "Controling Basic"
Description: 
Author: AUTOCONT
Date: 14/02/2019
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# Controling Basic - Nastavení

## Kontrola Creditcheck

Funkčnost pro kontrolu bonity partnerů. Společnost CreditCheck deklaruje, že každý den ve své databázi českých firem provádí 185 různých typů kontrol. Služba Creditcheck ERP je zdarma stejně tak jako vytvoření výpisu CreditcheckList. V databázi Creditcheck lze tedy prověřovat partnera bez přihlášení. V případech, kdy je u firmy nalezen oranžový nebo červený semafor je potřeba se pro prohlédnutí detailů přihlásit. Toto je placená služba, kterou si zákazník dle své potřeby uzavře s CreditCheck.

### Nastavení elektronické komunikace

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení elektronické komunikace**.
2. V kartě Nastavení elektronické komunikace v záložce Kontrola CreditCheck vypnit pole **Webová služba** a pole **Nepoužívat kontakty pro CreditCheck** *(pokud firma nepoužívá kontakty je třeba zaškrtnout tento boolean. Pak se při stažení dat z CrediChecku budou plnit přímo pole „Stav CreditCheck“ na kartě zákazníka, dodavatele.).
3. Do pole pole webová služba zadat: **http://creditwebservices.creditcheck.cz/CreditCheckAktualizace.asmx?op=GetCreditChecks**
4. Potvrdit pomocí OK.


### Nastavení fronty úloh
Doporučujeme nastavit pravidelné denní stahování informace o bonitě zákazníka CreditCheck ERP ve Frontě úloh. 
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Položky fronty úloh**
2. V ribbonu zvolit **Nový**.
3. Vyplnit pole:
   - **Typ spouštěného objektu: Sestava**
   - **ID spouštěného objektu: 52057060** – stahování informací o bonitě zákazníka CreditCheck ERP
4. V záložce Perioda vybrat pole pro každý den v týdnu a **Počet minut mezi spuštěními** (pro každodenní 1440 minut).
5. 5. Potvrdit pomocí OK.

### Nastavení uživatelů
V nastavení uživatelů je zapotřebí povolit provádění změn stavu CreditChecku, který pak mu umožní zrušit naimportovaný stav.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení uživatelů**.
2. Zatrhnout pole **Povolit změnu stavu CreditCheck**
3. Potvrdit pomocí OK.

### Nastavení webových zdrojů

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Webové zdroje**.
2. V ribbonu vybrat **Nový**
3. Vyplnit pole:

    Pro bezplatný:
    - **Kód**: CREDITCHECKLIST – FREE
    - **Adresa URL**: http://www.creditcheck.cz/CCLfree.aspx?cid=F5A4EE27-D3FD-4477-A2C2-A7656605F12C&ic=%1

    Pro placený:
    - **Kód**: CREDITCHECKLIST - FULL	
    - **Adresa URL**:https://www.creditcheck.cz/CCLfull.aspx?cid=F5A4EE27-D3FD-4477-A2C2-A7656605F12C&ic=63493551&code=41HXzA1i8uFYHR84iD7Z5pMM0X/P/dzZBGc1xMCDa94=

CreditCheckList FREE parametry:

- cid: Identifikační číslo klientského ERP. CID je stejný pro všechny uživatele jednoho partnerského řešení.
- ic: Identifikační číslo prověřované firmy

CreditCheckList FULL má navíc parametr:

- code: Přístupový kód, který je vygenerovaný uživateli při registraci do systému CreditCheck. Pro každého platícího zákazníka je jiný a Credit Check, s.r.o. jej zašle po obdržení objednávky.



## Hierarchický návrh cen

Standardní prodejní cenotvorba je založena na myšlence vyhledání nejnižší možné ceny. Toto není vždy vyhovující, proto je možné v Nastavení prodeje a pohledávek zvolit tzv. Hierarchický návrh cen.

Jak na to:
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení prodeje a pohledávek**.
1. Vybrat v poli **Návrh ceny** možnost **Hierarchická**
2. Potvrdit pomocí OK


## Skonto dobropisy pro CZ

### Prodejní skonto dobropisy

Funkcionalita generování prodejních dopropisů byla rozšířena o skonto. . Nově je možné na DPH obch. účtoskupině nastavit, aby se vytvořil s odloženou DPH. To je využitelné zejména u tuzemských skonto dobropisů.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení financí**.
2. V záložce Obecné, je potřeba vybrat políčko **Adjustace skonta**.
3. Dalším krokem je nastavení kombinace účtoskupin v **Nastavení účtování DPH**, které se  nachází v ribbonu Nastavení financí.
4. Pokud uživatel bude chtít zapnout **odloženou DPH** je potřeba ji nastavit v **Nastavení prodeje** příznakem **Odložení skonta dle nast. DPH**.
5. Pro vytváření tuzemských dobropisů s odloženou DPH zbývá nastavit příznak **Prodejní skonto ODD s Odloženou DPH** na příslušné DPH obchodní účtoskupině.
6. Potvrdit pomocí OK. 



### Nákupní skonto dobropisy

Analogickým způsobem byla upravena tvorba opravných daňových dokladů na skonto i do oblasti Nákupu.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení financí**.
2. V záložce Obecné, je potřeba vybrat políčko **Adjustace skonta**.
3. Dalším krokem je nastavení kombinace účtoskupin v **Nastavení účtování DPH**, které se  nachází v ribbonu Nastavení financí.
4. Pokud uživatel bude chtít zapnout **odloženou DPH** je potřeba ji nastavit v **Nastavení Nákupu** příznakem **Skonto dle nast. DPH**.
5. Potvrdit pomocí OK. 

Pro zachování analogie s prodejem byly dále doplněny pole:
- **Kód příčiny skonta** – je-li vyplněno, systém doplní na vytvořený dobropis
- **Kopírovat jako opr. daň. doklad** – při vytváření dobropisu kopírováním je tento označen příznakem Oprava
- **Čísla opr.daň.dokladů skonta** – číselná řada pro systémem vytvářené účt.nákupní dobropisy

#### Tuzemský režim 
V tuzemsku je třeba vyčkat na daňový doklad od dodavatele. Proto při vyrovnání faktury platbou je vypočteno a zaúčtováno skonto a zároveň je ve stejné výši zaúčtována položka dodavatele typu Refundace. Tato bude uživatelem vyrovnána zaúčtováním opravného daňového dokladu od dodavatele.

Pro lepší trasovatelnost obsahují položky typu Refundace účtované při skontu odkaz na číslo související faktury v poli Číslo externího dokladu.

Pro takové chování systému je potřeba nastavit:
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **DPH obchodní účtoskupiny**
2. Příslušné DPH obchodní skupině nastavit příznak **Nákupní skonto ODD** na **Bez DPH**.
3. Potvrdit pomocí OK.

#### Zahraniční režim 
V případě uplatnění skonto režimu se zahraničními dodavateli není možné očekávat daňový doklad pro skonto. Je tedy žádoucí, aby doklad vznikl automaticky při vyrovnání faktury platbou obdobně jako v prodeji.

Pro takové chování systému je třeba nastavit:
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **DPH obchodní účtoskupiny**
2. Příslušné DPH obchodní skupině nastavit příznak **Nákupní skonto ODD** na **s DPH**.
3. Potvrdit pomocí OK.


## Splátkové kalendáře

Funkcionalita Splátkových kalendářů je k dispozici v prodeji i v nákupu a její fungování je v obou ob-lastech obdobné.  Splátkový kalendář je možné definovat na neúčtovaném dokladu, ale i dodatečně na zaúčtovaném dokladu v měnu dokladu.

### Definice splátek 

Pro vytvoření splátkového kalendáře nad fakturou:

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Prodejní faktury**.
2. Otevřete požadovanou fakturu.
3. V ribbonu faktury v záložce Navigace se nachází funkce **Splátkový kalendář**.
4. Jednotlivé splátky je možné zadat ručně nebo použít funkci **Navrhnout splátkový kalendář**
5. V okně **Vytvořit splátkový kalendář** lze nastavit počet splátek, částka splátky (EUR, LM), % splátky, datum splatnosti první splátky a perioda splátek.
6. Potvrdit pomocí OK.
7. Po zaúčtování faktury vzniknou položky zákazníka.



## Kumulování plateb na platebím příkazu

Funkcionalita umožňuje sloučení řádků platebního příkazu, což je vhodné, pokud je potřeba uhradit více nákupních dokladů jednou částkou. Kumuluje se podle Čísla účtu, SWIFT, IBAN, Měny a volitelně dle VS, KS a SS. Jestli má příkaz kumulovat, se zapíná na kartě bankovního účtu. Pokud se nekumuluje dle symbolů, tak se sloučené řádky založí s variabilním symbolem z číselné řady a SS a KS se vezmou z prvního slučovaného řádku příkazu. Datum splatnosti se vezme to nejnižší ze slučovaných řádků. 

### Nastavení dodavatele

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Dodavatelé**.
2. Otevřete příslušnou kartu dodavatele.
3. Na kartě dodavatele v záložce Platby zatrhněte políčko **Kumulovat platby**.
4. Potvrdit pomocí OK.

### Nastavení bankovního účtu

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Bankovní účty**.
2. Otevřete vybranou kartu bankovního účtu, na kterém bude umožněno provádět kumulace plateb.
3. Na kartě bankovního účtu v záložce Platební příkazy/Bankovní výpisy vyplňte příslušná pole:
   - Pole Kumulovat platební příkazy – zapíná/vypíná kumulaci
   - Pole Číselná řada variabilního symbolu – pokud se nekumuluje dle VS, KS nebo SS, pak se do pole VS doplní číslo dle číselné řady v tomto poli a SS a KS se vezmou z prvního slučovaného řádku příkazu.
   - Pole Kumulovat export podle variabilního symbolu – kumulace se za VS
   - Pole Kumulovat export podle konstantního symbolu – kumuluje se za KS
   - Pole Kumulovat export podle specifického symbolu – kumuluje se za SS
   - Pole Popis kumulovaného řádku plat. příkazu – popis pro vytvořený řádek
4. Potvrdit pomocí OK.  



## Účtování přepratků nákupní záloch

V souvislosti se zavedením Kontrolního hlášení od 1.1.2016 vznikla potřeba řešit čerpání přeplatku nákupní zálohy pod jedním číslem dokladu, stejným datem a i stejným kurzem. 

Celý postup lze realizovat ručně. Ovšem vzhledem k jeho komplikovanosti byla do systému doplněna funkcionalita, kdy v rámci konečné vyúčtovací faktury se přeúčtuje čerpání přeplatku zálohy.

### Nastavení účtování přepratků nákupní záloch

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení účtování DPH**.
2. Vyberte kombinaci účtoskupin, pro kterou chcete nastavovat.
3. Na kartě nastavení účto DPH v záložce Zálohy vyberte políčko **Určeno pro vrácení zálohy**
4. Potvrďte pomocí OK.



## Rozšíření EET

### Nastavení služby EET

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení služby EET**.
2. Vyplňte pole:
   - Služba URL: https://pg.eet.cz/eet/services/EETServiceSOAP/v3
   - Režim prodeje: Běžný
   - Kód certifikátu: CERT-EET
   - Vyberte v záložce Stav, možnost Povoleno
3. Potvrďtě pomocí OK.





## Kontrola registrace k DPH

Pro eliminaci rizika nesprávného účtování a vykázání DPH byly do systému doplněny nové kontroly.

### Kontrola registrace k DPH na dokladech

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení financí**.
2. V okně nastavení financí v záložce Hlášení vyplňte do pole **Vzorec data kontroly DIČ na dokladech** vzorec pro výpočet data.
3. Potvrďte pomocí OK.



## Kontroly směnných kurzů

Pro eliminaci rizika nesprávného zadání směnného kursu a tudíž zaúčtování dokladu s nesprávným kursem, byly do systému doplněny nové kontroly.

### Kontrola správnosti směnného kursu

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Měny**.
2. Vyberte měnu pro kterou chcete nastavovat.
3. Na kartě měny v záložce obecné definujte do políček **Dolní limit částky vzt. sm.kurzu**
 a **Horní limit částky vzt. sm.kurzu**
4. Potvrďte pomocí OK.

Je-li některé z nich vyplněno, pak systém provádí kontrolu:
- při vkládání hodnoty do Směnných kurzů, 
- při vkládání kurzu na nákupních, prodejních nebo servisních dokladech

### Kontrola importu směnných kursů
Je-li vyplněné, probíhá při procházení či vytváření prodejních, nákupních či servisních dokladů kontrola na existenci směnného kurzu pro určité datum. 

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení financí**.
2. Na kartě nastavení financí v záložce Ostatní vyplňte políčko **Vzorec pro kontr.sm.kurzu na dokl.** vzorcem.
3. Potvrďte pomocí OK.


## Vymáhání pohledávek

Funkcionalita slouží jako podpora pro vymáhání pohledávek, které dosud nebyly uhrazeny. U takových pohledávek je potřeba mít především aktuální informaci o stavu pohledávky, průběhu vymáhání a mít možnost připojit dokumenty SharePoint.


1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Druhy vymáhání**.
2. V okně Druhy vymáhání vyplňte pole:
   - **Kód** - Název vymáhání (exekuce, konkurz, postoupení,...)
   - **Popis** - Popis zadaného vymáhání
3. Potvrďte pomocí OK.


## Ostaní

### Zamezení editace uživatelů

### Rozšíření funkcionality RapidStart
Na stránky Konfigurační sešit a Karta konfiguračního balíčku byla doplněna funkce Nastavit pořadí zpracování. Tato funkce navrhne pořadí, v jakém mají být jednotlivé balíčky zpracovávány při zohlednění vzájemných vazeb.
 
Na stránce Pole konfiguračního balíčku byly doplněny informativní sloupce:
- Datový typ
- Délka
- Hodnoty
  
Na stránce Konfigurační sešit je možné spustit sestavu Definice datových struktur, která může sloužit jako dokumentace k migračním úlohám.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Konfigurační sešit**.
2. Na stránce konfiguračního sešitu v ribbonu záložce Sestavy spusťte funkci **Definice datových struktur**.
3. Před spuštením tohoto reportu, můžete definovat filtry dle potřeby.
4. Tlačítkem Tisk/Náhled vygenerujete sestavu.


|       Viz také       |                       Seznam                       |
| -------------------- | -------------------------------------------------- |
| AC Productivity Pack | [AC Productivity Pack](ac-pp-productivity-pack.md) |
| Controling Basic     | [Controling Basic](ac-pp-controling-basic.md)      |