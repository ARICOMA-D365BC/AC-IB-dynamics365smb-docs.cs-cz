---
Title: ARICOMA SOLUTIONS - Sdílená poštovní schránka Exchange - Nastavení
Description: Slouží k importu příloh e-mailů z sdílené e-mailové schránky do Business Centralu, kde mohou být přílohy dále zpracovány.
Author: Ondřej.Slavík
Date: 23/03/2023
Product: dynamics365-business-central
Contentlocale: cs-cz
ms.search.keywords: Exchange, Shared, Mailbox, IN Buffer, Agent, E-Mail, Azure
---
# Sdílená poštovní schránka Exchange - Nastavení
> Aktualizace: 12.04.2023

Nastavení vyčítání e-mailů ze sdílených schránek do IN Bufferu.

## Předpoklady

Je nutné mít k dispozici O365 účet s právy "Global Admin" a "Exchange Admin". Tomuto účtu v následujícím textu říkáme **Administrátorský účet**.

Dalším účtem se přihlašujeme ke sdílené schránce, tento účet může být již zmíněný administrátorský účet, nebo to může být účet jiný, bez administrátorských práv. Tento účet by se neměl jmenovat po zaměstnanci, ale měl by být neosobní, třeba založený k tomuto účelu, například exchangeBC@domena.cz. Tomuto účtu v textu dále říkáme **Účet schránky**.

## Nastavení Schránky
Inspirujeme se návodem od [Micorosoftu](https://learn.microsoft.com/en-us/dynamics365/business-central/marketing-set-up-email-logging?tabs=new-experience). Lze ho nalézt též v Business Centralu na stránku **Asistované nastavení** pod odkazem **Nastavit protokolování e-mailu**.

Přepněte manuál do nastavení přes sdílené schránky výběrem záložky **New Experience**.

Podle návodu musíme:
    
1. Založit sdílenou schránku
2. Přiřadit ke schránce účet, přes který budeme vyčítat (jak je uvedeno výše, tento účet nemusí být administrátorský)

### Založení sdílené schránky
Přihlásíme se do administrátorského centra pro exchange na [tomto odkaze](https://admin.exchange.microsoft.com/#). K tomu použijeme admistrátorský účet.

Zde v **Recipients/Mailboxes** přidáme sdílenou schránku. Vyplníme Jméno zobrazení, adresu.

### Přiřazení účtu ke schránce
Poté k nově vniknuvší schránce přiřadíme účet schránky. Tento účet již nemusí mít administrátorská práva.

## Nastavení propojení
Dále nastavíme v [Azure portále](https://portal.azure.com/) aplikaci, která bude k exchange přistupovat. . Přihlásíme se administrátorským účtem.

Opět postupujeme podle Microsoft návodu, kapitola o propojení na Azure AD:

1. Založíme novou registraci aplikace.

2. v **Manage/Authentication** přidáme *Redirect URL* ve tvaru {adresaslužby}/OAuthLanding.htm, například *http://localhost:8080/BC215/OAuthLanding.htm*.

3. Pod **API Permissions** přidáme k GRAPH API delegované oprávnění *Mail.ReadWrite.Shared*. Pak udělíme souhlas správce.

4. Pod **Certificates & Secrets** přidáme nové tajemství, někam si schováme pole *value*.

5. V přehledu si pak vykopírujeme *Application ID*.

## Nastavení v BC
Na stránce 52068375 **Exchange Mailboxes** jsou následující pole, vyplníme alespoň ta označená tučným fontem:
  
| Název pole | Popis |
|------------|-------|
| **Code** | Identifikace schránky |
| **Email Address** | adresa sdílené schránky |
| **Email Batch Size** | velikost dávky pro zpracování v jednom běhu, výchozí je hodnota 50 |
| Enabled | zda je vytěžování této schránky povoleno |
| **Client Id** | ID klienta (aplikace) tak jak je zobrazeno v registraci aplikace na Azure portále (výše) |
| **Client Secret Key** | hodnota tajemství, které bylo přidáno k registraci aplikace na Azure portále (výše) |
| Redirect URL | URL přesměrování, které bylo přidáno k registraci aplikace na Azure portále (výše) |
| Attachment Filter | filtr příloh, které se budou vytěžovat (například při hodnotě **@*.pdf** se budou vytěžovat jen soubory PDF) |
| Default Task ID | ID výchozí úlohy, propisuje se do IN Bufferu |
| Default Source System ID | ID výchozího zdrojového systému, propisuje se do IN Bufferu |
| SM Template Code | kód šablony SM |
| SM Status Code | kód statutu SM |

Po vyplnění zaškrtneme pole **Enabled**. Systém nás vyzve k přihlášení administrátorským účtem a poté účtem schránky. Administrátorským účtem potvrzujeme všechna oprávnění, která jsme nastavili aplikaci v Azure portále.

Nakonec můžeme na stránce akcí **Validate Setup** zkontrolovat, zda je vše správně nastaveno.

### Agent
Dále založíme agenta, který bude vlastní vyčítání provádět. Vyplníme následující hodnoty:

| Název pole | Hodnota |
|------------|---------|
| Typ | IN |
| Druh komunikace | E-mail |
| Parametr komunikace | Kód schránky, pole *CODE* z tabulky výše. |
| ID Codeunity agenta | 52068378 |

Ostatní pole na agentovi už nejsou nastavením specifická pro tuto funkcionalitu, více informací o agentech naleznete v [Nastavení spooleru](spooler-setup.md).

Nyní můžeme na stránce schránek spustit akci **Test Run**, která schránku jednou vyčte. Při tom se přílohy z e-mailu založí do IN Bufferu, kde lze podle pole **Batch ID** později dohledat, jestli přišly v růných zprávách. Zároveň se na sdílené složce vytěžená zpráva zarchivuje.

V IN Bufferu pak lze původní zprávu zobrazit přes akci **Zobrazit přílohu**, případně přílohu stáhnout pomocí **Export dokument**.

## Vizte Také
[Sdílená poštovní schránka Exchange](exchange-shared-mailboxes.md)  
[Productivity Pack](productivity-pack.md)