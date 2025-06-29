---
title: CZ Banking Extension - API connector settings
description: CZ Banking Extension - API connector settings
author: RobertJelen
date: 05/30/2025
reviewer: janousek
ms.service: dynamics-365-business-central
ms.search.keywords: banking, finance, czech, API
---
# Nastavení API konektorů

> Update 30.05.2025

## ČSOB API konektor

### Zprovoznění služby ČSOB Business Connector

Kroky ke zprovoznění služby jsou tyto:

- povolení služby ČSOB Business Connector u smlouvy o využívání služby CEB,
- získání certifikátu od certifikační autority nebo přímo od banky,
- registrace certifikátu pro použití ve službě ČSOB Business Connector v portálu,
- konfigurace služby ČSOB Business Connector v portálu,
- nastavení klientské aplikace v Business Central

**Povolení služby ČSOB Business Connector u smlouvy o využívání služby CEB**
Zakázání, resp. povolení, služby ČSOB Business Connector je možné provést v portálu nebo pobočce banky

**Získání certifikátu**  

Služba ČSOB Business Connector umožňuje používat certifikáty vydané certifikačními autoritami I. Certifikační autorita a PostSignum. Pro použití ve službě ČSOB Business Connector jsou vhodné pouze takzvané Serverové komerční certifikáty, které musí umožňovat takzvanou Klientskou autentizaci.

Certifikát lze získat také přímo od banky, což lze provést v zásadě 2 způsoby, buď

- prostředky Windows (např. s pomocí IT pracovníka)
    - ruční vytvoření žádosti o certifikát v klientském počítači (např. pomocí nástroje Windows *certmgr.msc*),
    - podání žádosti o certifikát a vydání certifikátu (CEB -> Business Connector -> *Požádat o certifikát* a následně stažení certifikát volbou *Stáhnout*)
    - instalace vydaného certifikátu v klientském počítači (např. pomocí nástroje Windows *certmgr.msc*)
- nebo za pomoci aplikace *ČSOB Business Connector*(získání komunikačního certifikátu je popsáno v příručce [csob-business-connector-implementacni-prirurucka.pdf](https://www.csob.cz/documents/10710/15532355/csob-business-connector-prirucka.pdf?v2401)). Jedná se o
    - instalaci aplikace ČSOB Business Connector na počítač (kapitola 2),
    - získání komunikačního certifikátu (kapitola 3).

> [!TIP]
> Aplikace ČSOB Business Connector nebude pro běžnou práci využívána. Doporučujeme v ní ale nastavit upozornění na vypršení certifikátu (viz příručka v kapitole Obnova komunikačního certifikátu).

**Registrace certifikátu**  

V případě certifikátu od banky (viz výše) je automaticky registrován.

**Konfigurace služby ČSOB Business Connector v portálu**
V portálu je nutné povolit požadované operace, které bude klient pomocí ČSOB Business Connectoru využívat. V našem případě se jedná o *Stahování výpisů pro konkrétní účty* a *Odesílání podepsaných souborů platebních příkazů pro konkrétní účty*.

**Nastavení klientské aplikace v Business Central**  

Pro nastavení Business Central je třeba stáhnout komunikační certifikát ve formátu pfx:

1. vStiskněte klávesy Windows + R a do otevřeného okénka napište certmgr.msc a stiskněte OK.
2. V nástroji certmgr rozbalte po levé straně Osobní a v seznamu nalezněte řádek certifikátu. Bude mít vydavatele CEB Business Connector CA a jméno subjektu, které jste zvolili.
3. Stiskněte na certifikátu pravé tlačítko myši a v kontextovém menu vyberte Všechny úkoly a Exportovat…
4. V průvodci exportem certifikátu vyberte Ano, exportovat privátní klíč a následně proveďte export do souboru PKCS #12 s koncovkou .pfx. Zadané heslo budete potřebovat v dalším kroku.

Dalším krokem je nastavení přístupu v Business Central:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Klienti ČSOB CEB** a poté vyberte související odkaz.
2. Zadejte ČSOB v poli Kód na novém řádku
3. Do pole **Popis** zadejte např. „ČSOB API“
4. V poli **API** ponechte hodnotu „Produkční prostředí“.
5. V poli *Dostupný pro* ponechte hodnotu „Společnost“ pro nastavení společného přístupu pro všechny oprávněné uživatele modulu.
6. V poli **Číslo smlouvy** zadejte hodnotu ze smlouvy o přístupu k API, kterou jste s bankou podepsali.
7. Spusťte akci*Nahrát certifikát* a vyberte soubor s certifikátem ve formátu pfx.
8. Zadejte heslo k certifikátu v poli **Heslo k certifikátu**.

> [!TIP]
> Chcete-li přístup určovat podle přihlášení uživatele, musí si každý uživatel sám provést výše uvedené nastavení Klienta ČSOB CEB. V poli **Dostupný pro** vybere hodnotu „Uživatel“.

**Specifické parametry pro ČSOB API konektor**
Následující parametry je třeba doplnit do Rozšířeného nastavení v případě, že chcete používat ČSOB API konektor pro import bankovních výpisů:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení exportu/importu banky** a poté vyberte související odkaz.
2. Přejděte na vybraný řádek typu Import.
3. Spusťte akci *Rozšířené nastavení*.
4. V poli **Poskytovatel bankovních výpisů** vyberte hodnotu „ČSOB CEN Connector“.
5. V poli **Kód klienta ČSOB CEB** vyberte kód klienta definovaný v předchozím kapitole.
6. V poli **Formát souboru ČSOB CEB** vyberte volbu GPC reprezentující formát ABO.
7. V poli **Kódování obsahu** doplňte hodnotu – viz kap. [Nastavení kódování pro import](cz-banking-extension-setup.md/#Nastavení-kódování-pro-import)
8. V poli **ID procedury zpracování** zkontrolujte, že se doplnila hodnota 52057431 (Bank Stmt.Imp.-ABO Acb).

Následující parametry je třeba doplnit do Rozšířeného nastavení v případě, že chcete používat ČSOB API konektor pro export platebních příkazů:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení exportu/importu banky** a poté vyberte související odkaz.
2. Přejděte na vybraný řádek typu Export.
3. Spusťte akci *Rozšířené nastavení*.
4. V poli **Poskytovatel bankovních výpisů** vyberte hodnotu „ČSOB CEN Connector“.
5. V poli **Kód klienta ČSOB CEB** vyberte kód klienta definovaný v předchozím kapitole.
6. V poli **Formát souboru ČSOB CEB** vyberte volbu KPC reprezentující formát ABO.
7. V poli **ID procedury zpracování** zkontrolujte, že se doplnila hodnota 52057438 (Paym.Order Export-ABO acb).

## KB API konektor

### Zprovoznění API Business suite služby

Pro využití služby [API Business suite](https://www.kb.cz/cs/kbapi/sluzby-kb-api/api-business-suite) od Komerční banky musíte mít aktivovánu vybranou aplikaci internetového bankovnictví (*Moje Banka Business*, or *Profibanka*, or *Mobilní banka Business*).

Základní kroky pro zprovoznění API rozhraní jsou:

- Firma si aktivuje v KB službu API Business Suite.
- Firma zažádá u firmy Aricoma o Autorizační klíč, který bude vygenerován speciálně pro ni a díky němuž Aricoma zaregistruje KB API konektor v KB.
- Firma nastaví modul v Business Central.
- Firma udělí souhlas BC aplikaci ke se stahováním dat z KB a vybere bankovní účty, ke kterým bude mít BC přístup.

**Získání Autorizačního klíče**  

Kontaktujte nás e-mailem na adrese <bc_sales@aricoma.com>. Stačí nám pouze jméno vaší firmy, v odpovědi vám zašleme Autorizační klíč. Tento je určen pouze pro potřeby vaší firmy a nesmí být používán nikým jiným.

**Nastavení modulu v BC**  

Dalším krokem je nastavení přístupu v Business Central:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Klienti KB API** a poté vyberte související odkaz.
2. Na stránce Klienti KB API zadejte „KB“ v poli **Kód** na novém řádku.
3. Do pole **Popis** zadejte např. „KB API“.
4. V poli **API** ponechte hodnotu „Produkční prostředí“.
5. V poli **Autorizační klíč** zadejte hodnotu, kterou jste obdrželi od Aricoma (viz předchozí odstavec).
6. V poli **Počet dnů transakční historie** zadejte 10

**Udělení souhlasu**  

1. Na stránce Klienti KB API spusťte akci *Autorizovat klienta*
2. V automaticky otevřeném novém okně se objeví dialog banky, kde po přihlášení budete vyzváni k udělení souhlasu s použitím aplikace „Aricoma KB konektor“.
3. Ihned poté se objeví další výzva k přihlášení, po kterém vyberete bankovní účty, ke který má mít „Aricoma KB konektor“ přístup.

<!-- ### Specific parameters for KB API connector
-->

**See also**  

[Nastavení rozšířeného CZ bankovnictví](cz-banking-extension-setup.md)  
[Rozšířené CZ bankovnictví](cz-banking-extension.md)  
[Financial Pack](finance-pack.md)  
