---
title: CZ Banking Extension - Setup
description: CZ Banking Extension - Setup
author: RobertJelen
date: 05/30/2025
reviewer: janousek
ms.service: dynamics-365-business-central
ms.search.keywords: banking, finance, czech, API
---
# Nastavení rozšířeného CZ bankovnictví

> Update 30.05.2025

Modul Rozšíření CZ bankovnictví je potřeba zapnout, v produkčním prostředí bude uživatel požádán o aktivaci předplatného (viz  [dokumentace k monetizaci](https://www.aricoma.com/docs/cs-cz/dynamics365/business-central/ProductivityPack/monetization.html)).

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení rozšíření CZ bankovnictví** a poté vyberte související odkaz.
2. Aktivujte **Povoleno** pro zapnutí funkcionality.

> [!TIP]
> Před nastavením spusťte Asistované nastavení pro tento modul, který najdete v Asistovaná nastavení -> Nastavení rozšíření ARICOMA. Ten vám umožní nahrát konfigurační balíček a jeho prostřednictvím doplnit vzorová nastavení, na která se mimo jiné odkazují scénáře v dalších kapitolách.

## Formáty bankovních výpisů a platebních příkazů

Modul Rozšíření CZ bankovnictví je určen primárně pro optimalizaci práce s výpisy a příkazy, nicméně obsahuje i univerzální import bankovních výpisů v ABO formátu (\*.gpc), který v základní podobě podporuje většina bank v České republice. Rovněž umožňuje export platebních příkazů v ABO formátu (\*.kpc).

> [!TIP]
> Využijte některý z doplňků k tomuto addonu pro API komunikaci právě s vaší bankou.

### Nastavení pro manuální dávkový import výpisů

Pokud vaše banka podporuje elektronické výpisy, které obsahují více transakce pro více účtů, je možné toho využít pro vytvoření více výpisů najednou (v rámci jedné společnosti).

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení exportu/importu banky** a poté vyberte související odkaz.
2. Přejděte na vybraný řádek (např. s kódem „CZBE_ABO-IMP-LOCAL“)
3. Zkontrolujte, že v poli **ID procedury zpracování** je hodnota 52057427 umožňující import výpisů prostřednictvím akce Import bankovních výpisů.
4. Spusťte akci *Rozšířené nastavení*
5. Na stránce Rozšířené nastavení importu výpisů ověřte, že je příznak **Dávkový import povolen** nastaven na Ano.
6. Zkontrolujte, že v poli **ID procedury zpracování** je hodnota 52057431 určená pro zpracování souborů ve formátu ABO.

> [!TIP]
> Aktivujte pole Podpora souborů ZIP pro povolení importu více souborů výpisů najednou v rámci jednoho zip souboru.

#### Nastavení kódování pro import

V případě nesprávných znaků v naimportovaném výpisu je třeba upravit použité kódování. Nastavte správné kódování v poli **Kódování obsahu**. Pro ověření funkčnosti nastaveného kódování doporučujeme použít akci *Test kódování obsahu* na stránce Rozšířené nastavení importu výpisů.

### Nastavení pro manuální import bankovních výpisů prostřednictvím API

Pokud máte od Aricoma zakoupen doplněk pro API komunikaci s vaší bankou a nechcete využívat podpory automatizace zpracování, pak je třeba upravit nastavení. Detailní popis všech kroků je v dokumentaci ke každému doplňku, nicméně samotný import se v případě formátu ABO nastaví takto:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení exportu/importu banky** a poté vyberte související odkaz.
2. Přejděte na vybraný řádek (např. s kódem „CZBE_ABO-IMP-LOCAL“)
3. Řádek označte, stiskněte Ctrl+C, přejděte na nový řádek a stiskněte Ctrl+V.
4. Přejmenujte v poli **Kód** např. na „CZBE_ABO-IMP-API“
5. Zkontrolujte, že v poli **ID procedury zpracování** je hodnota 52057427 umožňující import výpisů prostřednictvím akce Import bankovních výpisů.
6. Spusťte akci *Rozšířené nastavení*.
7. Na stránce Rozšířené nastavení importu výpisů spusťte akci *Nový*.
8. V poli **Popis** můžete upravit předvyplněný text.
9. Doplňte parametry pro API konektor – viz [documentace](ext-banking-API-setup.md) ke konkrétnímu API.

> [!IMPORTANT]
> Pokud takto vytvořené nastavení importu banky použijete na kartě Bankovního účtu, pak uživatel každým stiskem tlačítka Import na kartě Bankovního výpisu, popř. při spuštění funkce Import bankovního výpisu začne komunikovat s API rozhraním banky. To nemusí být vždy žádoucí, banky obvykle mají nastaveny limity pro počet dotazů (např. za 10 minut).

## Nastavení automatizace importu a zpracování bankovních výpisů prostřednictvím centrálního zásobníku

Automatizaci lze nastavit pouze pro metody, u kterých není vyžadován zásah uživatele. Nelze ji tedy použít pro import z lokálního úložiště, ale je typicky vhodná pro komunikaci s bankou prostřednictvím API.

### Nastavení stahování do centrálního zásobníku

Následující postup navazuje na výsledek nastavení z kapitoly  [Nastavení pro manuální import bankovních výpisů prostřednictvím API](#nastavení-pro-manuální-import-bankovních-výpisů-prostřednictvím-api).

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení exportu/importu banky** a poté vyberte související odkaz.
2. Přejděte na vybraný řádek (např. s kódem „CZBE_ABO-IMP-API“)
3. Spusťte akci *Rozšířené nastavení*.
4. Na stránce Rozšířené nastavení importu výpisů nastavte pole **Povoleno pro Centrální zásobník** na hodnotu Ano.

### Automatické stahování výpisů do centrálního zásobníku

Zapnout automatické stahování výpisů do Centrálního zásobníku je nutné pouze v jedné společnosti. Funkce pak v této společnosti prochází všechna rozšířená nastavení pro import výpisů, kde má pole **Povoleno pro Centrální zásobník** hodnotu Ano. Dle těchto nastavení naimportuje výpisy dostupné na rozhraní umožňující import bez zásahu uživatele (typicky API).

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení rozšíření CZ bankovnictví** a poté vyberte související odkaz.
2. Nastavte příznak **Automaticky stahovat výpisy do centrálního zásobníku**.

> [!NOTE]
> Vytvořená položka fronty úloh je ve výchozím nastavení spuštěna v 5:45 ráno ve všední dny.
> [!TIP]
> Chcete-li omezit nastavení, podle kterých bude automat (viz výše) provádět import, můžete nastavit filtr na kód v poli Řetězec parametrů na kartě Položky fronty úloh (např. „CZBE_ABO\*“).

### Nastavení importu z centrálního zásobníku

Následující postup prochází klíčové nastavení, které je součástí vzorových dat.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení exportu/importu banky** a poté vyberte související odkaz.
2. Přejděte na řádek s kódem „CZBE_ABO-IMP-CENTRAL“.
3. Zkontrolujte, že v poli **ID procedury zpracování** je hodnota 52057427.
4. Spusťte akci *Rozšířené nastavení*.
5. V poli **Poskytovatel bankovních výpisů** vyberte hodnotu „Centrální zásobník“.
6. Zkontrolujte, že v poli **ID procedury zpracování** je hodnota 52057429 určená pro zpracování souborů ve formátu ABO

### Nastavení bankovních účtů pro automatizaci

Pro centrální zpracování a z toho planoucí možnosti automatizace zpracování je třeba jednoznačně definovat, do kterých společností patří které bankovní účty. K tomu slouží evidence Nastavení zpracování bankovních výpisů. Do této tabulky se automaticky zakládají všechna čísla účtů, které obsahovaly soubory importované do Centrálního zásobníku bankovních výpisů. Následně je třeba přiřadit účet k některé ze společností v BC.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení zpracování bankovních výpisů** a poté vyberte související odkaz.
2. Vyberte řádek s číslem účtu, který nastavujete.
3. Je-li účet veden v cizí měně, vyberte příslušný kód v poli **Kód měny**.
4. V dolní části stránky v části Nastavení vyplňte pro příslušnou Společnost pole **Počáteční datum výpisu**, od kterého se má provádět zpracování výpisů. Toto datum se vztahuje na Datum výpisu.

> [!IMPORTANT]
> Počet záznamů v této tabulce s vyplněným Počátečním datem výpisu je určující pro kontrolu počtu účtů v předplatném. V případě, že je definován větší počet, než kolik je platný v předplatném, není možné otevřít Centrální zásobník a musí být nejprve ponížen počet platných záznamů v tomto nastavení. Vypnutí importu je možné nastavením příznaku **Zpracování zakázáno**.
> [!TIP]
> Pokud máte nový bankovní účet, ale zatím se žádný výpis neimportoval, nastavení můžete provést i v předstihu ručním vložením čísla účtu.

### Automatické zpracování výpisu z centrálního zásobníku

Zapnout automatické zpracování výpisů z Centrálního zásobníku je nutné pouze v jedné společnosti.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení rozšíření CZ bankovnictví** a poté vyberte související odkaz.
2. Nastavte příznak **Automaticky vytvářet bankovní výpisy**.

> [!NOTE]
> Vytvořená položka fronty úloh je ve výchozím nastavení spuštěna v 6:00 ráno ve všední dny.

### Čištění zpracovaných výpisů z Centrálního zásobníku bankovních výpisů

Doporučujeme průběžně mazat již zpracované záznamy v tabulce Centrální zásobník bankovních výpisů, nejlépe automatizovanou úlohou v jedné firmě:

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení rozšíření CZ bankovnictví** a poté vyberte související odkaz.
2. Nastavte příznak **Automaticky čistit centrální zásobník**.

> [!NOTE]
> Vytvořená položka fronty úloh je ve výchozím nastavení spuštěna v 6:00 ráno ve všední dny. Automatická dávka ve výchozím nastavení maže výkazy starší 14 dnů, ale lze ji přepsat v dialogovém okně sestavy (pole „Vzorec data“).

## Podpůrná nastavení pro import výpisů

### Automatické formátování čísla účtu (volitelné)

Zapnutí této funkce zajistí automatické formátování čísel bankovních účtů v BC, čím dojde k eliminaci problémů s importem bankovních výpisů

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Informace o společnosti** a poté vyberte související odkaz.
2. Aktivujte pole **Formátovat číslo účtu**

### Číslo bank.účtu na bank.výpisu (volitelné)

Slouží pro zadání přesného formátu čísla bankovního účtu, který je v souborech výpisů, pokud se liší od hodnoty zadané standardně v poli Číslo bankovního účtu.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Bankovní účty** a poté vyberte související odkaz.
2. Vyplňte pole **Číslo bank.účtu na bank.výpisu**

## Podpůrná nastavení pro automatické zpracování výpisů

### Poslední úroveň dávkového zpracování (povinné)

Určuje, jaká je poslední úroveň automatického zpracování bankovních výpisů. Samotné zpracování bankovního výpisu probíhá standardním procesem: Bankovní výpis / Vydaný bankovní výpis / Deník

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Bankovní účty** a poté vyberte související odkaz.

1. Vyberte požadovanou hodnotu v poli **Poslední úroveň bankovního výpisu**:
    - Bankovní výpis (výchozí hodnota)
    - Vydaný bankovní výpis
    - Deník

> [!NOTE]
> Obvykle se nastaví hodnota *Deník*. Hodnota *Bankovní výpis* se nastaví v případě, kdy je třeba provést v importovaném bankovnímu výpisu ruční změnu (např. import platebního avíza).

### Číselná řada (povinné)

Je nutné nastavit stejnou číselnou řadu pro nevydané a vydané bankovní výpisy na Kartě bankovního účtu.
Tato číselná řada musí mít aktivované Ruční číslování a vyplněnou Masku. Maska musí obsahovat min. 2 znaky pro rok (rr) a volné číslo (ccc).  
Funkčnost zpracování bankovních výpisů automaticky čísluje bankovní výpisy v BC tak, že vkládá dle masky rok a pořadové číslo výpisu přidělené bankou.

### Kontrolovat obraty bankovního výpisu (volitelné)

Při „Vydání“ bankovního výpisu funkce kontroluje, zda obrat výpisu souhlasí na rozdíl mezi Počátečním a Koncovým saldem výpisu uvedeným na hlavičce bankovního výpisu. Počáteční a Koncové saldo výpisu se importuje ze souboru Bankovního výpisu.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Bankovní účty** a poté vyberte související odkaz.
2. Aktivujte pole **Kontrolovat obraty bankovního výpisu**

## Úpravy na míru

### Vlastní funkce pro stahování výpisů do centrálního zásobníku

V případě, že stahujete výpisy v jiném formátu nebo pokud potřebujete specificky upravený import, musí váš partner vytvořit vlastní procesní codeunitu řešící import bankovních výpisů do zásobníku bankovních výpisů.
Zásobník by měl být naplněn neformátovanými daty tak, jak jsou přímo v souboru bankovního výpisu příslušného formátu (o formátování a validaci dat se stará až funkce na vytváření bankovních výpisů).

    codeunit xxx "Bank Stmt.Imp.-MyFormat"

    TableNo = "Bank Stmt. Import Request Acb";

    trigger OnRun()
    var
        DotNetStreamReader: Codeunit DotNet_StreamReader;
        InStream: InStream;
       TempCentralBankStmtBufferAcb: Record "Central Bank Stmt. Buffer Acb" temporary;
        TempBankStmtLineBufferAcb: Record "Bank Stmt. Line Buffer Acb" temporary;

    begin
        //StreamReader initialization to read the contents of the dump file:
        Rec.CreateStreamReader(InStream, DotNetStreamReader); 
        
        //Where to populate the contents of the StreamReader dump into temporary tables - see examples below

        //Example of header filling:
        NextBufferNo += 1;
        TempCentralBankStmtBufferAcb.Init();
        TempCentralBankStmtBufferAcb."No." := NextBufferNo;
        TempCentralBankStmtBufferAcb."Account No." :=  ;    //our account no.
        TempCentralBankStmtBufferAcb."Statement No." := ;
        TempCentralBankStmtBufferAcb."Statement Date" := ;
        TempCentralBankStmtBufferAcb."Starting Balance" := ;
        TempCentralBankStmtBufferAcb."Ending Balance" := ;
        TempCentralBankStmtBufferAcb.Insert();

        //Example of filling rows:
        TempBankStmtLineBufferAcb.Init();
        TempBankStmtLineBufferAcb."Buffer No." := NextBufferNo;
        TempBankStmtLineBufferAcb."Line No." := NextLineNo;
        TempBankStmtLineBufferAcb."Variable Symbol" := ;
        TempBankStmtLineBufferAcb."Constant Symbol" := ;
        TempBankStmtLineBufferAcb."Specific Symbol" := ;
        TempBankStmtLineBufferAcb."Account No." := ;   //account no. in 16+4 format
        TempBankStmtLineBufferAcb.Description := ;
        TempBankStmtLineBufferAcb.Amount := ;
        TempBankStmtLineBufferAcb.Insert();
        NextLineNo += 1;

        //Save the result of processing:
        Rec.SetData(TempCentralBankStmtBufferAcb, TempBankStmtLineBufferAcb); 
    end;

**See also**  

[Nastavení API konektorů](cz-banking-extension-API-setup.md)  
[Rozšířené CZ bankovnictví](cz-banking-extension.md)  
[Financial Pack](finance-pack.md)
