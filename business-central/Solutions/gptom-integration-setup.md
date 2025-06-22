---
title: GP Tom Integration
description: GP Tom Integration
author: jelen
date: 09/30/2024
ms.service: dynamics-365-business-central
ms.search.keywords: GP Tom Integration, Streamline Tools, Global Payments, settings
---
# Nastavení integrace s GP tom
> Update 14.10.2024

## Nastavení

### Aktivace modulu
Prvním krokem (v produkční databázi) je kontrola, zda-li má společnost aktivováno předplatné modulu (viz [nápověda k Aricoma monetizaci](https://www.aricoma.com/docs/cs-cz/dynamics365/business-central/ProductivityPack/monetization.html)).
V dalších krocích je uživatel proveden registrací prvního platebního terminálu.
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení platebních terminálů** a poté vyberte související odkaz.
2.	Na stránce **Nastavení platebních terminálů** spusťte akci Nastavit API.
3.	Zadejte API klíč získaný aktivací v terminálu.

### Nastavení terminálů
Každé fyzické zařízení musí být zaevidováno v tabulce Platební terminály. Popis nastavení dále odpovídá nejběžnější konfiguraci, kterou je evidence plateb kartou.

> [!POZNÁMKA]
>Aplikace GP Tom umožňuje evidenci i hotovostních nebo kryptoměnových plateb, Tyto možnosti jsou podporovány, nicméně nejsou popisována žádná další nastavení v BC, při kterých registrace takových operací dávaly smysl.
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Platební terminály** a poté vyberte související odkaz.
2.	Na stránce **Platební terminály** klikněte na funkci *Nový* a vytvořte novou platební terminál.
3.	Zadejte *Kód* a *Popis terminálu*.
4.	V poli *ID terminálu* zadejte číslo přiřazené terminálu.
5.	V poli *Uživatelské jméno obchodníka GP tom* zadejte jméno (e-mail) uživatele terminálu.
6.	V poli *Heslo obchodníka GP tom* zadejte heslo uživatele terminálu.
7.	V poli *Časový limit transakcí GP tom (s)* ponechte výchozí hodnotu, pokud nemáte specifický požadavek na zkrácení či prodloužení času, kdy BC neukončí čekání na odezvu z terminálu.
8.	V poli *Preferovaný typ platby* zvolte Karta. 
9.	V poli *Preferovaný typ účtenky* zvolte, má-li být stvrzenka z terminálu vytisknuta nebo zaslána e-mailem či na mobilní telefon.
10.	V poli *Čísla dokladů plateb* vyberte číselnou řadu pro označení záznamů o platbách v BC.
11.	Spusťte akci *Získat přístupový token* pro ověření, že jsou zadané přihlašovací údaje správné.


### Volání registrace platby odjinud
Propojení lze provést obecně 2 způsoby:
- Spouštěním page „PT Register Payment_acc“ pomocí funkcí RegisterPaymentDialog v CU "PaymentTerminalsInterface_acc" (viz dále).
- Vlastním rozhraním, popř. zcela bez uživatelského rozhraní pomocí funkce RegisterPayment v CU "PaymentTerminalsInterface_acc".

Následující popis CU PaymentTerminalsInterface_acc zobrazuje všechny dostupné funkce:

codeunit 72056620 "PaymentTerminalsInterface_acc"

```al 
/// <summary>
/// Function for running the batch closing on the payment terminal with GUI (Confirmation dialog).
/// </summary>
/// <param name="PaymentTerminal">Record of the "Payment Terminal_acc" table where batch closing will be performed.</param>
procedure TerminalBatchYesNo(PaymentTerminal: Record "Payment Terminal_acc")

/// <summary>
/// Function for running the batch closing on the payment terminal without GUI (no confirmation dialog).
/// </summary>
/// <param name="PaymentTerminal">Record of the "Payment Terminal_acc" table where batch closing will be performed.</param>
/// <param name="ShowDialog">Indicates whether a progress dialog and messages are displayed when the operation is performed.</param>
procedure TerminalBatch(PaymentTerminal: Record "Payment Terminal_acc"; ShowDialog: Boolean)

/// <summary>
/// Function for running a page that enables user to register payments on the payment terminal.
/// </summary>
/// <param name="PaymentTerminal">Record of the "Payment Terminal_acc" table where transaction will be registered.</param>
procedure RegisterPaymentDialog(PaymentTerminal: Record "Payment Terminal_acc")

/// <summary>
/// Function for running a page that enables user to register a transaction on the payment terminal with predefined values.
/// </summary>
/// <param name="InitialPaymentTerminalTransaction">Record of the "PaymentTerminalTransaction_acc" table with the initial values of the transaction (e.g. amount, document number, payment method, etc.).</param>
procedure RegisterPaymentDialog(InitialPaymentTerminalTransaction: Record PaymentTerminalTransaction_acc)

/// <summary>
/// Function for registering a transaction on the payment terminal based on defined parameters directly without dialog page.
/// </summary>
/// <param name="PaymentTerminalCode">A unique code of the payment terminal</param>
/// <param name="PaymentType">Type of the payment (Cash, Card etc.).</param>
/// <param name="DocumentNo">Number of the documet to which a payment is registered.</param>
/// <param name="PostingDate">Posting date of the documet to which a payment is registered.</param>
/// <param name="CurrencyCode">Currency code of the payment.</param>
/// <param name="Amount">Amount of the payment.</param>
/// <param name="ShowDialog">Indicates whether a progress dialog and messages are displayed when the operation is performed.</param>
procedure RegisterPayment(PaymentTerminalCode: Code[20]; PaymentType: Enum "PT Payment Type_acc"; DocumentNo: Code[20]; PostingDate: Date; CurrencyCode: Code[10]; Amount: Decimal; ShowDialog: Boolean)

/// <summary>
/// Function for cancelling the transaction on the payment terminal with GUI (Confirmation dialog).
/// </summary>
/// <param name="PaymentTerminalTransaction">Record of the "PaymentTerminalTransaction_acc" table of the transaction that will be cancelled.</param>
procedure CancelTransactionYesNo(var PaymentTerminalTransaction: Record PaymentTerminalTransaction_acc)
begin
    PaymentTerminalsMgt.CancelTransactionYesNo(PaymentTerminalTransaction);
end;
/// <summary>
/// Function for cancelling the transaction on the payment terminal without GUI (No confirmation dialog).
/// </summary>
/// <param name="PaymentTerminalTransaction">Record of the "PaymentTerminalTransaction_acc" table of the transaction that will be cancelled.</param>
/// <param name="ShowDialog">Indicates whether a progress dialog and messages are displayed when the operation is performed.</param>
procedure CancelTransaction(var PaymentTerminalTransaction: Record PaymentTerminalTransaction_acc; ShowDialog: Boolean)
```

## Viz také
[Integrace s GP tom](gptom-integration.md)  
[Streamline Tools](streamlinetools.md)  
[ARICOMA řešení](../index.md)
