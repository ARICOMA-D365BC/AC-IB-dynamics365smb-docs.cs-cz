# Spooler/ExchangeSharedMailbox - nastavení
Vyčítání exchange pomocí *sdílených schránek*. Nová funkcionalita, dříve to běželo přes veřejné složky.

V tomto manuálu bude představeno nastavení vyčítání e-mailů ze sdílených schránek do IN Bufferu.

## Nastavení Schránky
Mimo BC se inspirujeme návodem od Microsoftu. V době psaní manuálu se nachází na [tomto odkaze](https://learn.microsoft.com/en-us/dynamics365/business-central/marketing-set-up-email-logging?tabs=new-experience). Lze se k němu dostat i přes "Asistované nastavení"/"Nastavit protokolování e-mailu".

Jak bylo zmíněno výše, dříve se to dělalo přes veřejné složky, nyní to běží přes věřejné schránky. Proto na stránce návodu zaškrtáváme "New Experience".

Předpoklad: máme k dispozici O365 účet, při nejlepším s právy "Global Admin" a "Exchange Admin". Dalším účtem se přihlašujeme ke schránce. Lze použít stejný účet, může ale být administrátorský s právy a běžný s přístupem ke schránce.

Podle návodu musíme:
    
    -Založit sdílenou schránku
    -Přiřadit ke schránce účet, přes který budeme vyčítat (jak je uvedeno výše, tento účet nemusí být administrátorský)

### Založení sdílené schránky
Přihlásíme se do administrátorského centra pro exchange na [tomto odkaze](https://admin.exchange.microsoft.com/#). K tomu použijeme admistrátorský účet.

Zde v Recipients/Mailboxes přidáme sdílenou schránku. Vyplníme Jméno zobrazení, adresu.

### Přiřazení účtu ke schránce
Pak účet, který bude přistupovat ke schránce, přiřadíme k nově vzniknuvší schránce. Tento už nemusí mít administrátorská práva.

## Nastavení propojení
Dále nastavíme v Azure portále aplikaci, která bude k exchange přistupovat. Portál je na [tomto odkaze](https://portal.azure.com/). Přihlásíme se administrátorským účtem.

Opět postupujeme podle Microsoft návodu, kapitola o propojení na Azure AD.

Založíme novou registraci aplikace.

v **Manage/Authentication** přidáme *Redirect URL* ve tvaru {adresaslužby}/OAuthLanding.htm, například *http://localhost:8080/BC215/OAuthLanding.htm*.

Pod **API Permissions** přidáme k GRAPH API delegované oprávnění Mail.ReadWrite.Shared. Pak udělíme souhlas správce.

Pod **Certificates & Secrets** přidáme nové tajemství, někam si schováme pole *value*.

V přehledu si pak vykopírujeme *Application ID*.

## Nastavení v BC
Na stránce 52068375 *Exchange Mailboxes* vyplníme nějaký kód; adresu sdílené schránky, kterou jsme zakládali; velikost dávky; ID klienta (aplikace, výše); hodnotu klientova tajemství (výše); URL adresu přesměrování (výše); Filtr příloh (například při "@*.pdf" se budou vytěžovat jen soubory PDF).

Po vyplnění zaškrtneme pole povoleno, přihlásíme se administrátorským účtem a potom účtem přiřazeným ke sdílené schránce. Administrátorem potvrzujeme všechna oprávnění, která jsme nastavili aplikaci v Azure portále. Nakonec v akcích můžeme ještě zkontrolovat, jestli je nasatavení v pořádku.

### Agent
Dále založíme agenta, který bude vlastní vyčítání provádět. Bude typu *IN*, Druh komunikace je *MAIL*, parametr komunikace je kód sdílené schránky ze stránky výše, codeunit 52068378. Všechno ostatní nastavení je jako u všech agentů.

Teď na stránce schránek můžeme spustit akci testovacího běhu, která schránku jednou vyčte. Při tom se přílohy z e-mailu založí do IN Bufferu, kde se podle pole *Batch ID* dá později dohledat, jestli přišly v růných zprávách. Zároveň se na sdílené složce vytěžená zpráva zarchivuje.

V IN Bufferu pak lze původní zprávu zobrazit přes akci *Zobrazit přílohu*, případně přílohu stáhnout pomocí *Export dokument*.
