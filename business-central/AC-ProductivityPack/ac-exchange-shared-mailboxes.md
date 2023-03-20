# Spooler/ExchangeSharedMailbox
Řešení sestává ze tří objektů:

    - table 52068368 "Exchange Mailbox_ach",
    - page 52068375 "Exchange Mailboxes_ach",
    - codeunit 52068378 "INAgent-ExchangeMailbox_ach".

Tabulka uchovává informace o jednotlivých sdílených schránkách, které chceme vytěžovat, stránka tyto informace zobrazuje a spravuje a codeunit zodpovídá za vlastní vytěžování schránek.

Objekty jsou provázány tak, že codeunit se nastaví na novém IN agentovi a jako parametr se mu předá kód schránky, kterou chceme vyčítat.


## Tabulka
Struktura tabulky sestává ze 13 polí:
    
    - Code: pro identifikaci schránky,
    - Email Address: adresa schránky,
    - Email Batch Size: velikost dávky pro zpracování v jednom běhu,
    - Enabled: jestli je vytěžování této schránky povoleno,
    - Client Id: ID klienta (aplikace) tak jak je zobrazeno v registraci aplikace na Azure portále,
    - Client Secret Key: hodnota tajemství, které bylo přidáno k registraci aplikace na Azure portále,
    - Redirect URL: URL přesměrování, které bylo přidáno k registraci aplikace na Azure portále,
    - Consent given: administrátorem udělen souhlas, uživatel nevyplňuje
    - Attachment filtr: filtr příloh, které se budou vytěžovat
    - Default Task ID: ID výchozí úlohy, propisuje se do IN Bufferu
    - Default Source System ID: ID výchozího zdrojového systému, propisuje se do IN Bufferu
    - SM Template Code: kód šablony SM
    - SM Status Code: kód statutu SM

## Stránka
Funkcionalita na stránce:

    - Na validaci pole Enabled: přihlášení administrátorským účtem pro udělení souhlasu a poté účtem připojeným ke sdílené schránce pro zpřástupnění pro vyčítání,
    - Akce:
        - Renew Token: obnoví token,
        - Validate Setup: zjistí, zda je vše správně nastaveno
        - Test Run: jednou spustí vyčítání pomocí příslušného agenta

## Codeunit
Vytěží přílohy z e-mailů ve schránce a tyto e-maily zarchivuje, přílohy nahraje do IN Bufferu.