---
title: Czech Local Functionality - Finance | Microsoft Docs
description: This section describes local functionality Finance - VAT
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, finance, CZ, VAT
ms.date: 15/05/2019
ms.author: v-pejano
---

# Corrections posting (red storno)

According to legal requirements, costs and revenues are usually posted only to either the debit or the credit side of a G/L Account. Companies in Eastern Europe usually enforce accounting policy to post certain inventory and GL transactions as corrections. The reason for this is that auditors and revenue authorities conduct accounting controls against this rule. 

The purpose of the feature is: 
- to allow the Accounting Manager to enforce corrective posting on desired G/L Accounts, 
- to allow the Accounting Manager to enforce corrective posting in Inventory Postings (negative transfer entries, expected costs posting), 
- to allow the Accounting Manager to enforce corrective posting of cancelling in Fixed Assets, 
- to allow the user to enforce corrective posting with just one click (G/L, Inventory and Jobs Postings) 

## Statutory company information

In the current times, many documents are circulating within and outside company structures. Minimum necessary requirements of such documents are set by local legislations. It is possible to divide such requirements approximately into 3 groups:
- Company officials names need to be present on some internal and external documents
- Document footers – majority of external documents have to contain basic company information in document footers, usually in company’s partner language
- Registration numbers have to be visible in internal and external document

This feature allows users to define company officials and designate them as General Manager, Accounting and Finance Managers for usage in internal and external documents.
Users can define document footers in different languages. Such footers can be used in different reports and documents.

Additional company registration numbers and other registration information can be stored in Company Information and used in documents.

### Description feature posting

This feature enables users to customize the way the [!INCLUDE[d365fin](../../includes/d365fin_md.md)] stores the Posting Descriptions during posting to General Ledger Entries. This feature is utilized mainly to ease up auditing General Ledger by providing auditors with full posting descriptions stored in Description field of each General Ledger Entry.
The Posting Descriptions field can be defined manually before posting a document. It is also possible to use template text.
The Posting Descriptions field can be used in:
- Sales Documents
- Purchase Documents
- Service Documents
- Finance Charge
- Post Inventory Cost

## General ledger entry description

This feature transfers Sales and Purchase document line descriptions to G/L Entry description (instead of document header defined Posting Description). This functionality can be set separately for each account type in the document line.

## General journal reconciliation

This functionality has been extended. Net Change in Jnl. and Balance after Posting are not designated for G/L Accounts marked as Reconciliation Account only, but for all G/L Accounts used in General Journal, and also for other account types – Bank Account, Customer, Vendor, Fixed Asset and IC Partner. The functionality works with amounts in General Journal line and does not calculate VAT amounts for VAT Accounts. 

## Internal financial documents

Users perform General Ledger operations and must have the possibility to print documents for these operations with layout in compliance with the legal requirements.
Users also want to print a document for posted General Ledger operations.
For the reasons above, this feature provides the following reports:
- General Journal – Test Report is used to print documents from G/L Journals
- General Ledger Document Report is used to print posted General Ledger operations

## Accounting output documents 

In order to comply with the legislation, reporting features and local reporting practices of Czech companies, this feature provides the following reports:
- General Journal
- General Ledger
- Accounting Sheets
- Turnover report by Global Dimension
- Open G/L Entries to date 
- Inventory Account to date
- Joining Bank Account Adjustment
- Joining G/L Account Adjustment
- G/L VAT Reconciliation
- All payments on hold 
- Open Customer Entries at date
- Open Vendor Entries at date
- Fiscal Year Balance – standard report adjusted
- Trial Balance by Period – standard report adjusted

## Account schedule feature

As one of the most extensively used areas of application for analysis and reporting, Eastern European countries often ask for following improvements of standard Account Schedules feature:
- Common list of expressions – common list of expressions contains named lines which can be used in formulas of all Account Schedules. This is done by defining one of the Account Schedules as a common list of expressions called Shared Account Schedule.
- Saving results (current state) of analysis – this improvement allows user to store results of analysis done by using Account Schedules, modification of results and retrieval of results later on.
- Formulas Drill Down – this improvement allows user to drill down the results of formulas. Drill-down is now accessible for Totalling Type – Formula. Drilling down the result of the formula shows the user a new form containing the list of elements used to calculate results and their description.
- Additional Data Sources – apart from being able to perform analysis on GL Entries, the user can perform analysis on VAT, Customer, Vendor and Value entries.

## Statutory statements

Companies have to create Financial Statements according to the Accounting Law 563/1991. They have to create the Balance Sheet and the Profit and Loss Statement. 
This feature provides the following reports:

- Balance Sheet 
- Income Statement

These reports use the Account Schedule with the statement structure defined.

The Acc. Schedule Name contains new fields in the Czech version:
- Acc. Schedule Type – Balance Sheet or Income Statement

The Acc. Schedule Line contains new fields in the Czech version:
- Row Correction – link to other line for Balance Sheet setup
- Assets/Liabilities Type – Assets or Liabilities for Balance Sheet setup
- Calc – Always, Never, When positive, When Negative

Balance Sheet and the Profit and Loss Statements are often prepared in Excel file templates with the necessary design for statement printout. Users want to map defined Account Schedules to prepared Excel templates.

For the reasons above, this feature provides the new setup of Excel Templates and Statement File Mapping. Based on this setup users can export Account Schedule data to Excel file.

## Industry classification feature

This feature adds Industry Code classification field to Customer/Vendor tables and Sales/Purchase documents.

## Wip extended posting

The Czech legal Work in Progress (WIP) posting scheme includes the following new General Ledger Accounts:
- Consumption Account
- Change in Inventory of WIP Account
- Change in Inventory of Product Account 

This feature allows you to correctly perform Czech WIP and Production extended posting. It is therefore possible to set up combination Location and Inventory posting group for the account of Consumption, Work in Progress, Change of Semi-finished Product, Change of Product.
This new posting scheme is used in the following transactions:
- Consumption Posting in the Posting Journal
- Posting the Costs on Capacities in the Output Journal
- Finishing Orders and Auto Reporting

## See Also
[Czech Local Functionality](czech-local-functionality.md)