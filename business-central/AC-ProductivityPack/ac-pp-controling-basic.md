---
Title: "Controling Basic - Použití"
Description: 
Author: AUTOCONT
Date: 14/02/2019
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# Controling Basic - Použití
Controling Basic - Sada rozšíření obsahuje funkce:

## Stav Creditcheck

Stažené informace o bonitě zákazníka CreditCheck ERP (do bonity patří i info o nespolehlivém plátci DPH) se nachází v Informačních oknech pod názvem **Hodnocení dodavatele** na kartě dodavatele.

## Spuštění webových zdrojů

Spuštění webových zdrojů kontaktu je nyní umožněno také na kartě dodavatele/zákazníka a také na souvisejících dokladech (nabídka, objednávka, faktura, pokladní doklad, příkaz k úhradě). Spuštění se provede kliknutím na ikonu stavu CreditCheck 

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Kontakty**.
2. V ribbonu v záložce Akce vybrat funkci **Spustit weboý zdroj**
3. Dokončit pomocí OK.

## Hierarchický návrh cen

Standardní prodejní cenotvorba je založena na myšlence vyhledání nejnižší možné ceny. Toto není vždy vyhovující, proto je možné v Nastavení prodeje a pohledávek zvolit tzv. Hierarchický návrh cen.
 
### Prodejní ceny
Prodejní ceny systém dohledává v následujícím pořadí:
1.	Kampaň
2.	Zákazník
3.	Cenová skupna zákazníka
4.	Všichni zákazníci

Pozn. V případě nalezení ceny v učité úrovni již nehledá dále.

### Prodejní řádkové slevy
Prodejní řádkové slevy systém dohledává v následujícím pořadí:
1.	Kampaň a Zboží
2.	Kampaň a Cenová skupina zboží
3.	Zákazník a Zboží
4.	Cenová skupna zákazníka a Zboží
5.	Všichni zákazníci a Zboží
6.	Zákazník a Cenová skupina zboží
7.	Cenová skupna zákazníka a Cenová skupina zboží
8.	Všichni zákazníci a Cenová skupina zboží

Jak na to:
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Nastavení prodeje a pohledávek**.
1. Vybrat v poli **Návrh ceny** možnost **Hierarchická**
2. Potvrdit pomocí OK


## Splátkové kalendáře

Funkcionalita Splátkových kalendářů je k dispozici v prodeji i v nákupu a její fungování je v obou oblastech obdobné.  Splátkový kalendář je možné definovat na neúčtovaném dokladu, ale i dodatečně na zaúčtovaném dokladu v měnu dokladu.

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

### Vytvoření platebního příkazu

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Platební příkazy**.
2. Vyberte příslušný účet.
3. Vytvořte nový platební příkaz pomocí tlačítka **Nový** v ribbonu.
4. Zadejte řádky na dvě faktury od vybraného dodavatele se stejným číslem účtu.
5. Platební příkaz vydejte.
6. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Vydané platební příkazy**.
7. Vyberte příslušný účet.
8. Otevřete vydaný doklad, který jste vytvořili.
9. V ribbonu karty ve skupině Akce, vyberte funkci **Vytvořit řádky exportu**, která sloučí řádky plateb pro dodavatele, kteří mají poloveno kumulovat platby dle pravidel nastavených na bankovním účtu. Neslučované položky jsou převedeny do řádků exportu platebního příkazu ve stejném detailu.
10. Pro zobrazení sloučených řádků připravených pro export zvolte tlačítko **Řádky exportu** na kartě vydaného platebního příkazu.
11. Na kartě vydaného platebního příkazu v ribbonu ve skupině akce funkcí **Export platebního příkazu** vyexportujete platební příkaz.
12. Potvrdit pomocí OK.

### Vytvoření bankovního výpisu
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Bankovní výpisy**.
2. Vyberte vybranou banku.
3. Vytvořte nový bankovní výpis pomocí tlačítka **Nový** v ribbonu.
4. Vytvořte nový řádek bankovního výpisu.
5. Vydejte bankovní příkaz (s vytvořením deníku odsouhlasením plateb)
6. Potvrďte pomocí OK.
7. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Vydané bankovní výpisy**.
8. Vyberte vybranou banku.
9. Otevřete vydaný doklad, který jste v předchozích krocích vytvořili.
10. Vydáním výpisu je kumulovaná částka opět rozdělena v případě, že najde pro identifikační údaje pohybu na řádku výpisu odpovídající záznam na vydaném platebním příkazu v řádcích exportu.
11. Pomocí OK zavřete výpis.


## Účtování přepratků nákupní záloch

Po vytvoření finální nákupní faktury a přiřazení uhrazené nákupní zálohy je v případě přeplatku na záloze možné vložit další řádek s částkou přeplatku a příznakem **Určeno pro vrácení zálohy** (příznak je následně i na řádku zaúčtované faktury).

Zaúčtováním faktury pak pro každý takový řádek s přeplatkem vznikne položka dodavatele typu Dobropis. Tato položka má stejné Datum splatnosti jako příslušná nákupní faktura, vrácení peněz dodavatelem (Refundace) pak uživatel vyrovná právě s těmito vzniklými položkami.

Při použití funkce **Odúčtovat přiřazenou zálohu** (z karty Zálohového daňového dokladu) dojde ana-logicky k odúčtování těchto zúčtování přeplatků.


## Kontrola registrace k DPH
Pro eliminaci rizika nesprávného účtování a vykázání DPH byly do systému doplněny 2 nové kontroly.

### Kontrola registrace k DPH na dokladech

Do nastavení financí bylo doplněno pole **Vzorec data kontroly DIČ na dokladech**. Je-li vyplněné, probíhá při vytváření prodejních, nákupních či servisních dokladů kontrola na existenci platného ověření registrace k DPH. Tato kontrola se provádí při validaci zákazníka/plátce (resp. dodavatele/věřitele) na dokladu, pro období od pracovního data zpětně se hledá záznam v tabulce **Protokol ověření DIČ s ověřenou registrací** (stav **Platný** = DIČ je registrováno k DPH či **Neplatný** = DIČ není registrováno k DPH).

Při vytváření dokladu systém upozorní uživatele, když příslušné DIČ nebylo v NAV ještě nikdy ověřováno.

Na prodejní, nákupní či servisní doklady bylo rovněž doplněno nové okno s fakty zobrazující vybrané informace vztažené k hlavičce dokladu.

### Kontrola registrace k DPH dle položek DPH

Na formulář pro úpravy výkazu DPH byla doplněna sestava **Ověření DIČ – položky DPH**. 
 
Tato sestava je určena pro kontrolu položek DPH, resp. jestli režim DPH v položkách odpovídá stavu registrace k DPH pro použitá DIČ.
 


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

Do nastavení financí bylo doplněno pole **Vzorec pro kontr.sm.kurzu na dokl.**. Je-li vyplněné, probíhá při procházení či vytváření prodejních, nákupních či servisních dokladů kontrola na existenci směnného kurzu pro určité datum. Toto datum se počítá vzhledem k Zúčtovacímu datu a zohledňuje víkendy a jiné nepracovní dny (státní svátky, Vánoce, Velikonoce, apod.).

Pokud pro takový pracovní den nenajde záznam v tabulce Směnné kursy, zobrazí notifikaci. Kliknutím na **Detaily**… se otevře tabulka Směnné kursy pro měnu z dokladu.


## Vymáhání pohledávek

Funkcionalita slouží jako podpora pro vymáhání pohledávek, které dosud nebyly uhrazeny. U takových pohledávek je potřeba mít především aktuální informaci o stavu pohledávky, průběhu vymáhání a mít možnost připojit dokumenty SharePoint.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Položky zákazníka**.
2. Vyberte položku, kterou chcete vymáhat.
3. V ribbonu v přehledu položek zákazníka ve skupine Položka použijte funkci **Informace o pohledávce**.
4. Na kartě **Informace o pohledávce** se nachází záložka **Stav pohledávky**. Zde nastavte informace související s vymáháním pohledávky.
5. Pro sledování celého procesu použijte funkci v ribbonu ve skupině Navigace **Archivované záznamy**.
6. Otevře se přehled informací formou needitovatelného přehledu.
7. Přehled zavřete.
8. Okno Informace o pohledávce potvrĎte pomocí OK.

Z karty informace o pohledávce lze publikovat či zobrazit dokumenty a úkoly (podmínkou addon Publikování dokumentů či Publikování úkolů v licenci). Funkcionalita publikování dokumentů SharePoint umožní připojení elektronických dokumentů, jako jsou smlouvy, zápisy či jiné doklady vztahující se např. k vymáhání, soudním líčením apod.

Stav pohledávky je zobrazen v Informačním okně Podrobnosti položky zákazníka. Díky tomu má uživatel okamžitě k dispozici tuto základní informaci, ale také detailní informace na jedno kliknutí.

|           Viz také           |                             Seznam                              |
| ---------------------------- | --------------------------------------------------------------- |
| AC Productivity Pack         | [AC Productivity Pack](ac-pp-productivity-pack.md)              |
| Controling Basic - Nastavení | [Controling Basic - Nastavení](ac-pp-controling-basic-setup.md) |