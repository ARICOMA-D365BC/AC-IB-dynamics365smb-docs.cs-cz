---
title: Czech Local Functionality - Receivables & Payables | Microsoft Docs
description: This section describes local functionality - Receivables & Payables
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, Receivables, Payables, Finance, CZ, Cash
ms.date: 10/06/2019
ms.author: v-pejano
---

# Receivables & Payables

## Credits

Company Customers are quite often, to some extent, company Vendors as well. In such situations, it is quite common for companies to compensate their Receivables and Payables.

List of the main features of the Credits functionality: 
- View Balance as Vendor/Balance as Customer – to view Balance as Vendor on Customer card and Balance as Customer on Vendor card, user needs to set a Customer and Vendor business relation with a contact to indicate to the system that even though particular company is registered in application as Vendor and as Customer, it is in fact the same company.
- Credits Setup – Credit Nos., Credit Bal. Account No., etc.
- Credit Maintaining on Credit Card – choose Customer/Vendor, suggest lines/entries for compensation.
- Agreement printout.
- Credit posting – posted credit is created, entries application is posted.

entries to be counted can be entered manually or automatically from the Credit Card. In addition, there are functions to mark entries to count and balance the balance.
 
There is also a print of the Agreement on Mutual Settlement of Receivables and Payables under Czech legislation.

## Multiple interest rates feature

The Finance Charge feature operates with several interest rates. The Finance Charge Terms table for multiple interest rates calculates the interest rates using multiple rates for the specified periods.
This feature takes into account changes in the level of interest due to delays by the debtor. If the delay continues every calendar half year, then the level of interest from the delay dependents on the level of repo tariff specified by the local bank. The level of interest according to the repo tariff is applicable from the first day of the calendar half-year.

## Exchange rates adjustment feature

The majority of companies in the Czech Republic request the following improvements to be implemented in Exchange Rates Adjustment: 
- Ability to run Exchange Rates Adjustment for Customers, Vendors and Bank Accounts separately 
- Ability to have Exchange Rates Adjustment batch post adjustments in detail as well as summarized per currency 
- Ability to run Exchange Rates Adjustment just as simulation (without posting) in Test Mode

On standard report Adjust Exchange Rates is now possible to:
- Set Bank Account, Customer, Vendor filter for adjustment
- Choose adjustment for Customer or Vendor or Bank Account
- Choose the test mode
- Choose summarizing entries 
- Choose the method for dimension transfer

The Adjust Exchange Rate report feature also modifies the calculation principle for implemented gains and losses based on the Income Tax Act. This feature calculates the implemented gain or loss against the recently adjusted amount.
This feature in the standard version of Microsoft [!INCLUDE[d365fin](../../includes/d365fin_md.md)] reverses the non-implemented gain or loss first, and calculates the implemented gain or loss afterwards. The calculation is expressed against the amount in the initial exchange rate during the application of the payment and the invoice.
The new calculation principle is implemented for fluctuation in the already adjusted exchange rate.
The Adjust Exchange Rates batch job has been for Czech Advance Payments has also been extended.

## Multiple payables/receivables accounts

Users often post transactions like bad debt or other types of Receivable/Payable transactions that need to be recorded in Customer and Vendor Ledgers, but at same time posted to different Receivable/Payable GL Account, other than the one specified on Customer or Vendor posting groups. The easiest way to enable such functionality is to allow users to change Customer and Vendor posting groups in the moment of posing a particular transaction.

## Customers/vendors reconciliations

At the end of each fiscal year (or another period, when requested), companies send a statement of balances to Customers and Vendors in order to reconcile them with Customer and Vendor records. Customers and Vendors either confirm the statement or not and send it back with corrections, based on their own information. This feature allows users to prepare such report in [!INCLUDE[d365fin](../../includes/d365fin_md.md)].

## Sales correcting documents

According to the VAT law amendment, it is necessary to differentiate types of Sales Credit-Memo documents. This feature allows users to set up the following Credit Memo Types:
- Corrective Tax Document
- Internal Correction
- Insolvency Tax Document

This Credit Memo Type defines how is handled Postponed VAT on Sales Credit-Memo documents.

## Tax corrective documents for vat

According to the VAT law amendment (Act No 235/2004 Coll.; amended with Act No 47/2011 Coll.), companies must correct the VAT base and amount when they are changed due to different reason (financial discount, payment discount and other corrections).
The printout of the correction document is named Tax Correction Documents.
In the moment of paying the invoice with a defined payment discount, a Sales (or Service) Credit-Memo will be created. The document will reflect payment discount amount and calculated VAT Amount. The document can be printed in an ordinary way. The printout of the created Credit-Memo is a Tax Corrective Document. A Tax Corrective Document for payment discounts will be created if a payment discount is calculated based on an amount including VAT (it means the Adjust for Payment Disc. field is active in the General Ledger Setup form) and for those combinations which are active in the Adjust for Payment Discount fields in the VAT Posting Setup. In other cases payment discount will be calculated in an ordinary way.

## Contacts actualization from ares

ARES stands for Access to Register of Economic Subjects. ARES is an information system allowing a retrieval of information on economic entities registered in the Czech Republic.  
The user can fill in ARES http to General Ledger Setup. 
It is possible to run ARES actualization from Contact, Vendor and Customer Card. It is possible to search company and decide which fields can be updated in NAV (Name, Address, City, Post Code).

## Vendor templates

New feature for creating templates for different group of vendors has been added. This feature copies similar functionality for customers – Customer templates. The Vendor Template feature makes creating vendors easy and decreases amount of mistakes.
When the user creates a new Vendor, Apply Template function can be used. Some fields will be automatically filled in thanks to that. 

## New design of output documents

New set of printed reports for company external documents was created.
All documents have the same layout design (headers, footers, font type and size, etc.).
Additionally to standardisation, NAV documents were extended by all requirements required by the Czech legislation: 
- Registration No., VAT Registration No.
- Deduction of advances with information about invoice and date of payment received
- VAT specification printout grouped by VAT Identifier
- Naming of tax corrective documents based on Credit Memo type
- Printout of documents related to advance payments

### List of reports in the cz document set:
- Sales – Advance Letter CZ
- Sales – Advance Invoice CZ
- Sales – Advance Credit Memo CZ
- Purchase – Advance Letter CZ
- Purchase – Advance Invoice CZ
- Purchase – Advance Cr. Memo CZ
- Purchase – Quote CZ
- Order CZ
- Return Order Confirmation CZ
- Sales – Quote CZ
- Order Confirmation CZ
- Sales – Invoice CZ
- Sales – Credit Memo CZ
- Sales – Shipment CZ
- Sales – Return Receipt CZ
- Charge Memo CZ
- Reminder CZ
- Service - Contract CZ
- Service - Contract Quote
- Service - Quote CZ
- Service - Order CZ
- Service - Invoice CZ
- Service - Credit Memo CZ
- Service - Shipment CZ

## See Also
[Czech Local Functionality](czech-local-functionality.md)  
[Finance](finance.md)