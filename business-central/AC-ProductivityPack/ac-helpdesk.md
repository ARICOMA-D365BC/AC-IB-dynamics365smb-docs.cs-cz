---
Title: "HelpDesk"
Description: 
Author: AUTOCONT
Date: 04/04/2019
Product: dynamics365-business-central
Contentlocale: cs-cz
---

# HelpDesk

Modul  Helpdesk slouží k centralizovanému zadávání, evidenci, zpracování a vyhodnocování různých požadavků uživatelů v systému Microsoft Dynamics NAV. Uživatelé zde mohou zadávat požadavky na servisní úkony, na poskytnutí podpory, úpravu nebo doplnění funkcionality, evidovat reklamace a podobně. Umožňuje také kategorizaci požadavků, nastavení priorit a řízené zpracování přiřazenými řešiteli. K dispozici je i historie uzavřených požadavků HelpDesku.

## Založení požadavku

Po provedení potřebných nastavení lze zadávat požadavky HelpDesku. Požadavky lze zadávat ručně nebo prostřednictvím Průvodce vytvořením požadavku. Povinnost použití průvodce lze definovat v Nastavení helpdesku.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Pult dispečera helpdesku**.
2. V okně Pult dispečera helpdesku v záložce Navigace vybrat funkci **Průvodce**.
3. Prvním krokem v průvodci je určení **Kódu zadavatele** a **Priority požadavku**.
   - Obě pole jsou povinná, nelze pokračovat bez vyplnění obou hodnot.
4. Dalším krokem je **stručný popis požadavku** (nadpis) a **popis požadavku**.
5. Při dalším kroku je možné vybrat nastavení do předem definovaných kategorií (1-3)
6. Na spolední straně průvodce je volba **Publikovat dokumenty**, automaticky se spustí průvodce publikováním. Publikování dokuemntu vyžaduje modul Publikování SharePoint.
7. Posledím krokem je tlačítko **Dokončit**.

## Požadavky Helpdesku

Karta helpdesk požadavku zobrazuje relevantní informace vztahující se ke zvolenému požadavku. Údaje v bílých polích lze editovat (např. je možné doplnit prioritu dispečera, upravit data odezvy či řešení, event. změnit zařazení do kategorií na záložce Kategorie). 

Požadavek lze také přidělit k určitému projektu. Pokud příslušný projekt ještě neexistuje je možné jej vytvořit přímo z karty požadavku na záložce Akce pomocí tlačítka **Vytvoř projekt**. Touto operací je založen nový projekt se stejným kódem jako je číslo požadavku (i se stejným popisem) a tento kód se automaticky doplní do pole **Číslo projektu**. Kartu přiřazeného projektu a jeho položky lze pak zobrazit pomocí tlačítka **Karta projektu**.

Na záložce Řádky se po založení objeví nový záznam s výchozím stavem podle definice v šabloně workflow pro helpdesk. Při každé další změně stavu workflow požadavku se, v případě že máte pro tento stav nastavenu Akci Workflow logování (52068291 WriteStatusChangeHlpDesk), vygeneruje další řádek s odpovídajícími hodnotami (viz podrobnější popis níže u zpracování požadavku).

### Poznámky k požadavku

Ke každému vytvořenému požadavku je možné doplnit poznámky. První vstup do poznámek je možný už při vytváření požadavku v Průvodci, jak bylo popsáno výše.
Uživatelé mohou využívat 2 formy poznámek: 
- řádkové poznámky dostupné na záložce Řádky poznámek – tyto strukturované poznámky obsahují pole Datum, Poznámka (100 znaků) a Kód. 
- volné poznámky dostupné na záložce Detailní údaje – tyto poznámky umožňují zadávat libovolný text, který může být navíc zobrazen v informačním okně Náhled obsahu.

Je na rozhodnutí správce, která forma poznámek bude v rámci celé firmy využívána. 

**Dokumenty**

Pokud je instalován modul Publikování SharePoint, pak je možné u každého požadavku v Přehledu helpdesk požadavků na záložce Akce pomocí tlačítka Publikovat publikovat dokument a pomocí tlačítka Zobrazit zobrazit publikovaný dokument. Podrobnější popis postupu nastavení a práce při publikování a zobrazování dokumentů je v manuálu k modulu Publikování SharePoint.

**Tisk**

Pomocí tlačítka Tisk v Přehledu helpdesk požadavků se spustí sestava Helpdesk požadavky (do vstupního filtru se nabídne číslo aktuálně zobrazeného požadavku, rozsah tisku lze pak blíže specifikovat prostřednictvím filtrů a parametrů.




## Zpracování požadavku

Po vytvoření požadavku je možné jej dále zpracovávat. K tomu se na Kartě helpdesk požadavku využívá především záložka **Řešení**.

1. Otevřít kartu požadavku.
2. Rozbalit/otevřít záložku **Řešení**
3. Vyplnit potřebné údaje:
   - **Kód řešení** (vybírá se z předdefinované tabulky možných způsobů řešení)
   - **Trvání**
   - **Popis řešení** (max. 250 znaků)
   - **Kód dalšího řešitele**
4. Po zadání dat je potřeba změnit stav požadavku pomocí funkce** Změna stavu** v ribbonu.
5. Po změně na vybrat daný **stav workflow** (viz. definice stavu WF)
6. Dokončit potvrzením OK.
Pokud uživatel chce, může vygenerovat požadavky do PDF. Tento soubor lze později připojit jako přílohu e-mailu.
8. Na kartě požadavku v ribbonu sekci Akce použít funkci **Export PDF a mail**.
9. Zavřít kartu pomocí OK.

## Pult dispečera 

Pult dispečera umožňuje souhrnný pohled na zadané požadavky. Tato volba HelpDesku nabízí přehledové zobrazení požadavků s přednastavenými volitelnými filtry v záhlaví pro snadnější vyhledávání a orientaci. Požadavky lze filtrovat např. podle stavu, podle uživatele, zadavatele, řešitele či podle kategorií. Zobrazený přehled požadavků je možno navíc seřadit podle různých klíčů, zvl. podle čísla, priority, stavu workflow nebo kategorií.

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Pult dispečera helpdesku**.
2. Vybrat daný požadavek
3. Otevřít se karta požadavku
4. Zavřít pomocí OK

## Priorita požadavku

Jedním z nejdůležitějších kritérií pro rozhodování o plánování a  koordinaci kapacit na řešení požadavků je stupeň naléhavosti, s jakou je nutno se tím kterým požadavkem zabývat. Významnou pomůckou dispečera v tomto procesu může být ukazatel celkové priority požadavku, jak byl vypočítán programem na základě vstupních parametrů:
- Váha oprávněné osoby, tj. zadavatele požadavku
- Priorita požadavku stanovená zadavatelem při vytváření
- Priorita požadavku stanovená dispečerem helpdesku při event. následném přehodnocení důležitosti požadavku.
  
**Celková priorita je vypočtena jako**:
- součin hodnot Váha zadavatele (hodnota na kartě příslušné oprávněné osoby) a Priorita požadavku stanovené zadavatelem pokud dispečer nestanoví jinou prioritu (tj. priorita dispečera je nevyplněna)
- součin hodnot Váha zadavatele a Priorita požadavku stanovené dispečerem (tj. priorita dispečera je vyplněna)

## Sestavy

Nabídka tiskových sestav přiřazených modulu HelpDesk.
1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Helpdesk - Sestavy a Analýzy**.
2. Podle zadaných filtrů se vytisknou jednotlivé karty požadavků, zpožděné požadavky a seznam helpdesk požadavků.

## Export HelpDesk požadavků

1. Pomocí vyhledávací funkce **Řekněte mi, co chcete udělat (Alt + Q)** vyhledejte **Export helpdesk požadavků**.
2. Vyplnit vstupní filtry reportu.
    - Číslo, Nový požadavek, Uzavřený požadavek
3. Potvrďte pomocí OK.

## Viz také
[HelpDesk - nastavení](ac-helpdeks-setup.md)  
[AC Productivity Pack](ac-productivity-pack.md)
