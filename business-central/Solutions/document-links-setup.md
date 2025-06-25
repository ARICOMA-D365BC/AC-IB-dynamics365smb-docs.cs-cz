---
title: ARICOMA SOLUTIONS - Připojené dokumenty - Nastavení | Microsoft Docs
description: Document links
author: kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, document links, additional functions
ms.author: v-makune
---
# Připojené dokumenty - nastavení
> Aktualizace 16.06.2023

Následující řádky popisují nastavení od těch nezbytných pro samotné zprovoznění (Registrace aplikace v AAD, nastavení Aplikace SharePoint Azure AD) až po nastavení pokrývající speciální požadavky zákazníků (např. při ukládání souborů nebo evidenci doplňujících atributů).

## Registrace aplikace v Azure Active Directory
Prvním úkolem je pomocí portálu Azure zaregistrovat aplikaci pro službu Business Central ve vašem nájemci služby Azure AD. Součástí registrace je také přidělení přístupu k aplikaci příslušným službám. Účelem registrace je zajistit, aby Business Central a služby navzájem znaly údaje o Azure Active Directory (Azure AD).

1.	Přihlaste se na portál Azure a zaregistrujte aplikaci pro Business Central v Azure Active Directory tenant.
    - Postupujte podle obecných pokynů na stránce Registrace aplikaci v tenantu služby Azure Active Directory.
    Při přidávání aplikace do nájemce Azure AD musíte zadat následující informace:

    
    |Nastavení|Popis|
    |-|-|
    |Název|Zadejte název řešení Business Central, například Business Central - Sharepoint.|
    |Podporované typy účtů|Vyberte možnost pouze Účty v organizačním adresáři.|
    |Přesměrování URL|Chcete-li zadat webovou aplikaci, nastavte první pole na hodnotu Web. Zadejte adresu URL klienta prohlížeče Business Central a poté OAuthLanding.htm, například: https://businesscentral.dynamics.com/OAuthLanding.htm nebo https://MyServer/BC200/OAuthLanding.htm|

    - Po dokončení se na portálu zobrazí Přehled nové aplikace.
    
    - Zkopírujte **ID aplikace (klienta)**, které bylo přiřazeno aplikaci, **Koncový bod autorizace **OAuth 2.0** (v2)** a také **Adresu URL přesměrování**, kterou jste zadali. Tyto informace použijete později.

2.	Vytvořte tajný klíč klienta pro registrovanou aplikaci
    - Postupujte podle obecných pokynů na stránce Přidání pověření do webové aplikace.
    - Než opustíte stránku **Certifikáty a tajné klíče**, zkopírujte hodnotu tajného klíče do dočasného umístění. Po opuštění stránky není hodnota přístupná. Tento klíč použijete později v kódu klientské aplikace.
3.	Udělte registrované aplikaci delegované oprávnění pro přístup k požadované službě Sharepoint. 
    Na stránce přehledu registrované aplikace vyberte **Oprávnění API > Přidat oprávnění**. Poté pomocí podokna Požádat o oprávnění rozhraní API vyhledejte rozhraní API a přidejte oprávnění. Další informace najdete v tématu Přidání oprávnění pro přístup k webovým rozhraním API v dokumentaci k Azure.

    Následující tabulka vám pomůže nastavit minimální oprávnění:

|API|Název oprávnění|Typ|Popis|
|-|-|-|-|
|Microsoft Graph|User.Read.All|Delegovaný|Čtní všech uživatelskáý profilů|
||Sites.ReadWrite.All|Delegovaný|Úprava nebo odstranění položek ve všech kolekcích lokalit|
||Sites.Read.All|Delegovaný|Čtení položek ve všech kolekcích stránek|
||Files.ReadWrite.All|Delegovaný|Plný přístup ke všem souborům, ke kterým má uživatel přístup|

Pro případ ukládání pod účtem aplikace je třeba přidat následující:

|API|Název oprávnění|Typ|Popis|
|-|-|-|-|
|Microsoft Graph|User.Read.All|Aplikace|Čtená kompletních profilů všech uživatelů|
||Sites.Selected|Aplikace|Přístup k vybraným kolekcím stránek|

## Aplikace Sharepoint Azure AD

> [!WARNING] 
> Prvotní nastavení proveďte pomocí asistovaného nastavení, které vás provede nastavením Aplikace SharePoint Azure AD a navíc doplní i další užitečná nastavení (např. pravidla transformace, viz dále).

Pro každý Sharepoint site, který budete propojovat s Business Central, je třeba definovat propojení:
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Aplikace Sharepoint Azure AD** a poté vyberte související odkaz.
2.	Na stránce Aplikace Sharepoint Azure AD zadejte **Kód** a **Popis** nového záznamu.
3.	V poli **ID aplikace/klienta** zadejte ID aplikace z předchozí kapitoly.
4.	V poli **Tajný klíč klienta** zadejte klíč z předchozí kapitoly.
5.	V poli **URL autorizace** zadejte URL z předchozí kapitoly.
6.	V poli **URL přesměrování** zadejte URL z předchozí kapitoly.
7.	V poli **Typ pověření** zvolte způsob předávání pověření pro klientskou část. (Autorizační kód – přístup k Sharepoint bude pod oprávněními uživatele v BC; Pověření klienta – přístup k Sharepoint bude pod oprávněním AAD aplikace).
8.	V poli **Typ pověření na pozadí** zvolte Pověření klienta jako způsob předávání pověření pro úlohy běžící na pozadí (typicky pomocí Fronty úloh apod.).
9.	Spusťte akci Přihlásit se pro ověření funkčnosti propojení.
10.	Zavřete stránku.

## Nastavení připojení dokumentů
Funkcionalitu modulu je třeba globálně zapnout:
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení připojení dokumentů** a poté vyberte související odkaz.
2.	Aktivujte příznak **Povoleno**.
3.  **BC online**: Pokud systém nenajde aktivní (či již ukončené) předplatné pro tento modul, vyzve uživatele k vytvoření zkušebního předplatné (viz dokumentace k AC Monetizace).
**BC Onprem**: Přečtěte si Podmínky třetích stran a potvrďte souhlas tlačítkem **Přijímám**.
4.	Zavřete stránku.

## Knihovny dokumentů
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz.
6.	Na stránce Knihovny dokumentů spusťte akci Nový.
7.	Na stránce Knihovna dokumentů zadejte **Kód** a **Název** nové knihovny. 
8.	V poli **Typ knihovny** zvolte hodnotu Sharepoint.
9.	V poli **Aplikace SharePoint Azure AD** vyberte z definovaných aplikací.
10.	Spusťte akci Nastavit knihovnu SharePoint. Na stránce Výběr knihoven SharePoint vyberte požadovanou knihovnu.
11.	Zavřete stránku.

> [!NOTE]
> Když zapnuté na webu „Chcete vyžadovat rezervaci dokumentů před úpravami“, pak je třeba mít na knihovně zapnuté **Vyžaduje rezervaci dokumentů**.

> [!NOTE]
> V případě potřeby využití informací o datu a času z metadat souborů je třeba nastavit pole Časové pásmo SharePoint. Tím se zajistí soulad mezi těmito informacemi z SharePoint a z BC.

## Přidání Připojených dokumentů k vybrané funkcionalitě BC
### Krok 1 – Přidání na stránku jako Pageextension

Na všechny stránky, kde má být funkcionalita dostupná, musí být doplněno okno s fakty „DocumentLinksFactBox_ach“. Pokud si nejste jistí, jak vytvořit rozšíření stránky (viz následující kód), požádejte svého BC partnera.

    {
        layout
        {
            addlast(factboxes)
            {
                part(DocumentLinksFactBox_ach; "Document Links FactBox_ach")
                {
                    ApplicationArea = All;
                    Visible = false;
                }
            }
        }

        trigger OnAfterGetCurrRecord()
        begin
            UpdateDocumentLinksFactBox();
        end;

        local procedure UpdateDocumentLinksFactBox()
        begin
            CurrPage.DocumentLinksFactBox_ach.Page.SetContext(Rec);
        end;
    }


### Krok 2 – Základní nastavení šablony připojení dokumentů
Následující nastavení je pro entitu Zákazník, u které jsou v základu doplněny stránky Zákazníci a Karta zákazníka o potřebné okno s fakty.
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony připojení dokumentů** a poté vyberte související odkaz.
2.	Na stránce Šablony připojení dokumentů spusťte akci Nový.
3.	Na stránce Šablona připojení dokumentů zadejte **Kód** a **Popis** nové šablony.
4.	V poli **ID tabulky** zadejte 18.
5.	V poli **Kód knihovny** vyberte knihovnu SharePoint.
6.	Přepněte příznak **Povoleno** na Ano.
7.	Zavřete stránku.
8.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Zákazníci** a poté vyberte související odkaz.
9.	Spusťte akci Přizpůsobení.
10.	Najděte okno s fakty s názvem Připojené dokumenty, klikněte levým tlačítkem myši a zvolte Zobrazit.
11.	Pro libovolného zákazníka spusťte akci Zobrazit.
12.	Najděte okno s fakty s názvem Připojené dokumenty, klikněte levým tlačítkem myši a zvolte Zobrazit.
13.	Zastavte režim Přizpůsobení stiskem červeného tlačítka Hotovo.

## Různé šablony pro filtrované záznamy
Potřebujete-li mít šablonu definovánu pouze pro určité záznamy, popř. různé šablony pro jinak filtrované záznamy, můžete na šabloně nastavit filtr tabulky.
Příklad – šablona pro tuzemské zákazníky:

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony připojení dokumentů** a poté vyberte související odkaz
2.	Vytvořte novou šablonu připojení dokumentů dle postupu pro základní nastavení.
3.	Rozklikněte AssistEdit u pole Filtr tabulky (viditelné po stisku Zobrazit více).
4.	Na stránce Úpravy – Filtr tabulky zadejte „21“ do **Číslo pole** a „TUZ*“ do **Filtr pole**.
5.	Zavřete stránku.

> [!NOTE]
> Vytváření nových šablon je možné si usnadnit pomocí akce Zkopírovat šablonu dostupnou na kartě šablony.


## Rozšířené možnosti umístění souborů
Na šabloně je možné flexibilně nastavit pravidla pro ukládání souborů při připojení k entitám.

### **Příklad – smlouvy se zákazníky ukládáme do určené podsložky:**
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony připojení dokumentů** a poté vyberte související odkaz
2.	Vytvořte novou šablonu připojení dokumentů pro smlouvy se zákazníky dle postupu pro základní nastavení.
3.	Dále na stránce Šablona připojení dokumentů rozklikněte AssistEdit u pole **Výchozí složka**.
4.	Na stránce Výběr složky vyberte již existující, popř. vytvořte novou pomocí funkce Nová složka (popř. Nová podsložka) a následně výběr potvrďte stiskem OK.
5.	V poli **Výchozí složka** zkontrolujte cestu (např. „/ZAK/Smlouvy“)
6.	Zavřete stránku.

### **Příklad – každý zákazník má automaticky vlastní složku a v ní podsložku pro smlouvy:**
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony připojení dokumentů** a poté vyberte související odkaz.
2.	Vytvořte novou šablonu připojení dokumentů pro smlouvy se zákazníky dle postupu pro základní nastavení.
3.	Spusťte akci Parametry šablony. 
4.	Na stránce Parametry šablony připojení dokumentů vytvořte nový řádek pro parametr odpovídající číslu zákazníka (Kód parametru = CISLO-ZAK; Popis = Číslo zákazníka; Zdroj dat = Pole zdrojové tabulky; Číslo pole zdrojové tabulky = 1).
5.	Vytvořte další nový řádek pro parametr odpovídající názvu zákazníka (Kód parametru = NAZEV-ZAK; Popis = Název zákazníka; Zdroj dat = Pole zdrojové tabulky; Číslo pole zdrojové tabulky = 2).
6.	Pro odstranění případných nepovolených znaků v názvu zákazníka vyberte ještě v poli **Pravidlo transformace** hodnotu „NAZEV_SHP“.
7.	Zavřete stránku Parametry šablony připojení dokumentů.
8.	Na stránce Šablona připojení dokumentů zadejte v poli **Maska relativní cesty** (viditelné po stisku Zobrazit více) hodnotu: {{CISLO-ZAK}}-{{NAZEV-ZAK}}/Smlouvy
9.	Přepněte příznak **Vytvořit neexistující složku** na Ano.
10.	Zavřete stránku.

> [!NOTE]
> Kromě předdefinovaných zdrojů dat pro parametry šablony je možné nechat si připravit na míru vlastní funkci, která vytvoří požadovaný řetězec. Jedná se o zdroj dat Vlastní funkce, pro který pak v poli **ID vlastní funkce** přiřadíte číslo připravené codeunity.

### **Příklad – soubory jsou ukládány s generovaným názvem souboru:**
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony připojení dokumentů** a poté vyberte související odkaz.
2.	Vytvořte novou šablonu připojení dokumentů pro smlouvy se zákazníky dle postupu pro základní nastavení.
3.	Spusťte akci Parametry šablony. 
4.	Na stránce Parametry šablony připojení dokumentů vytvořte nový řádek pro parametr odpovídající číslu z číselné řady (Kód parametru = CISLO-CR; Popis = Číslo dokumentu; Zdroj dat = Číselná řada; v poli Číselná řada vyberte dle uvážení).
5.	Vytvořte další nový řádek pro parametr odpovídající názvu zákazníka (Kód parametru = NAZEV; Popis = Název souboru; Zdroj dat = Název souboru; Pravidlo transformace = NAZEV_SHP).
6.	Vytvořte další nový řádek pro parametr odpovídající názvu zákazníka (Kód parametru = PRIPONA; Popis = Přípona souboru; Zdroj dat = Přípona souboru).
7.	Zavřete stránku Parametry šablony připojení dokumentů.
8.	Na stránce Šablona připojení dokumentů zadejte v poli **Maska názvu dokumentu** (viditelné po stisku Zobrazit více) hodnotu: {{CISLO-CR}}-{{NAZEV}}.{{PRIPONA}}
9.	Zavřete stránku.

## Rozšířené možnosti nastavení oprávnění
V některých případech je třeba omezit přístup uživatelů k šablonám. Existuje možnost definovat jmenovitě uživatele, kteří mají mít přístup:
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony připojení dokumentů** a poté vyberte související odkaz.
2.	Vyberte šablonu a spusťte akci Oprávnění uživatelů.
3.	Na stránce Uživatelé šablony připojení dokumentů vyberte uživatele s přístupem.
4.	Zavřete stránku.

## Nastavení atributů knihovny dokumentů
Nejčastěji je funkcionalita atributů v BC využita k tomu, aby se automatizovaně či ručně doplnila metadata (sloupce) k souboru ukládanému v knihovně Sharepoint (viz Vytvoření sloupce v seznamu nebo knihovně - Podpora Microsoftu).

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz.
2.	Na stránce Knihovny dokumentů vyberte knihovnu a spusťte akci Atributy dokumentů.
3.	Na stránce Atributy knihovny dokumentů spusťte akci Přidat sloupec SharePoint.
4.	Na stránce Výběr sloupce knihovny SharePoint vyberte sloupec knihovny SharePoint, který chcete udržovat prostřednictvím BC.
5.	Předchozí bod opakujte, dokud nebudete mít přidány všechny požadované sloupce Sharepoint.
6.	Zavřete stránku.

> [!NOTE]
> Pokud se v průběhu času upraví definice hodnot sloupců SharePoint (primárně se jedná o typ Volba), je třeba tyto změny promítnout do BC ručně. 

Je-li požadován atribut pro využití pouze na úrovni BC, je možné jej definovat. Následující příklad popisuje jeden povinný atribut pro evidenci jména prodejce
1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz.
2.	Na stránce Knihovny dokumentů vyberte knihovnu a spusťte akci Atributy dokumentů.
3.	Na stránce Atributy knihovny dokumentů vytvořte nový řádek pro atribut evidující hodnocení zákazníka (Název = Prodejce; Datový typ = Text; Povinný = Ano).
4.	Na stránce Atributy knihovny dokumentů vytvořte nový řádek pro atribut evidující hodnocení zákazníka (Název = Hodnocení; Datový typ = Volba; Povinný = Ne).
5.	Pro atribut Hodnocení spusťte akci Hodnoty atributu.
6.	Na stránce Hodnoty atributu knihovny dokumentů vytvořte tři řádky s hodnotami: Pozitivní, Neutrální, Negativní a zavřete stránku.
7.	Zavřete stránku.

> [!NOTE]
> Hodnota v sloupci **Atribut SharePoint** indikuje, o který typ atributu se jedná.

## Nastavení automatického doplňování atributů knihovny dokumentů
Následující scénář navazuje na předchozí kapitolu, tedy že jeden z definovaných atributů knihovny dokumentů budeme automaticky plnit při nahrávání souboru.

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Šablony připojení dokumentů** a poté vyberte související odkaz.
2.	Vyberte šablonu pro připojení dokumentů k zákazníkům.
3.	Spusťte akci Parametry šablony. 
4.	Na stránce Parametry šablony připojení dokumentů vytvořte nový řádek pro parametr odpovídající jménu prodejce definovaného na kartě zákazníka (Kód parametru = JMENO-PRODEJCE; Popis = Jméno prodejce; Zdroj dat = Pole návazné tabulky; ID návazné tabulky = 13; Číslo pole návazné tabulky = 1; v poli Vazba tabulky definujte Kód = Kód prodejce).
5.	Zavřete stránku.
6.	Na stránce Šablona připojení dokumentů v části Mapování atributů dokumentu nastavte automatické vyplňování atributu knihovny pro jméno prodejce (Název atributu = Prodejce; Mapování na parametr = JMENO-PRODEJCE)
7.	Zavřete stránku.

> [!NOTE]
> V případě, že máte na knihovně definován větší počet atributů, můžete použít akci Aktualizovat atributy knihovny. Tato akce doplní do řádků pro mapování všechny zde chybějící atributy definované pro související Knihovnu dokumentů.

## Implementace Vlastní funkce

Zde je uveden návod k vytvoření vlastní funkce pro definici atributů popsaných v kapitole Rozšířené možnosti umístění souborů.

    {
        TableNo = "Doc.LinkTemplate Parameter_ach";

        trigger OnRun()
        begin
            // Input/Output of this function is the global variable Rec that contains the current record of the template parameter whose value is to be evaluated
            // The field Rec."Source RecordId" contains the id of the record to which the document is linked
            // The field Rec."Document FileName" contains the name of the document file that is linked

            // Here write your code to evaluate the parameter value
            // ...

            // Finally return the value formatted as Text data type in the Rec."Value" field
            Rec."Value" := 'Result value';
        end;
    }


## Viz také

[Připojené dokumenty](document-links.md)  
[Productivity Pack](productivity-pack.md)
