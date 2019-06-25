---
title: Czech Local Functionality - Finance VAT| Microsoft Docs
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

# Finance - VAT

## Vat date

The VAT Date is important for tax documents by §28 of VAT Law 235/2004. The VAT Date can be different from the posting date or the document date. The VAT Date is an important field for the VAT reporting.  

This feature focuses on improving the following:

### Setup of VAT Date feature

- Enabling VAT Date usage in system generally.
- Select the way the system will default the VAT Date’s value in different areas (Posting Date or Document Date).
- Periods for reporting VAT and company accounting periods are often different. To allow users to seamlessly report and post VAT according to VAT periods, and to issue internal and other statutory reporting based on accounting periods, this VAT Date feature introduces VAT Periods.
- Allow VAT Posting From/To – enter a date range in from/to fields to prevent mistakes of posting to closed Accounting or VAT periods.

### Posting Sales, Purchase and Service transactions with VAT Date

To post transactions using the VAT Date, the user needs to be able to enter VAT Dates in the document headers and Journal lines throughout the application.
After the posting of the VAT Date, it becomes a part of the posted documents and G/L Entries and VAT Entries.

### Calculating and posting VAT Settlement

System filters VAT Entries use the VAT Date (instead of the Posting Date) by selecting VAT Period and prepares a report showing which entries will be transferred to the Settlement Account. Printout also contains VAT Date information.

### Reconciling VAT and GL Entries

Users frequently reconcile amount kept in VAT Entries and VAT amounts posted to GL Entries.
Amounts shown in new Net Change (VAT Date) columns in all following forms will always be filtered out by VAT Date:

- Chart of Accounts form
- G/L Balance form
- G/L Account Balance form 

## VAT rounding improvements

Necessary standard functionality modification to round the VAT amount according to the Czech Republic law requirements has been added. The VAT Rounding is subject of VAT Law 235/2004 (§37). The rounding procedure uses rounding precision in order to calculate the result. Further additions include an ability to select special rounding precisions (special rounding is identified by a new field Round VAT Coeff. on the General Ledger Setup form) during VAT calculation for the following entities in G/L posting, Sales and Purchase. The implemented changes affect only Normal VAT or Reverse Charge VAT case during price calculation including VAT.

## Posting VAT on sales credit memo

Special function for the Sales Credit memo documents can be used. It is important to know (by §42 part 3b) of VAT Law 235/2004) the delivery date of the Sales Credit memo document. User can fill in the delivery date in the Posted Sales Credit Memo as the new VAT Date.  
Sales VAT Postponed Account field has been added in the VAT posting setup.
The Postponed VAT field was filled in the VAT Entry.

## VAT Statement

The VAT Statement contains many improvements which enable the user to:

- Add Stat. Reporting Setup with general setup for VAT reporting.
- Add two new operation rows (Row Division and Row Multiplication) in the Type field.
- Add setup for VAT from advances.
- Define a coefficient (constant) in the VAT statement when required to reduce VAT deduction – support for Non-deductible VAT.
- Filter the VAT Entries selection for the VAT Statement line by the EU Triangular Trade field. This is required, as EU (European Union) triangular trade (middle person – 1 debtor) must be reported in separate rows.
- Calculate and print VAT Statement for fulfilment in another country.
- Print the VAT Statement report with a new option to round off calculated amounts in the VAT statement to the nearest whole value.
- Filter data based on VAT Date using VAT Periods.
- Filter data for the posted VAT Statement of later date.
- More VAT Statement Types – Recapitulative, Corrective, Supplementary (by §43 part 1 of VAT Law 235/2004) – payer can submit Supplementary VAT Statement (see further). 
- Export the VAT statement to .xml file.
- Add Comments and Attachments to export for Tax Office.

## Supplementary VAT statement

By §43 part 1 of VAT Law 235/2004, payer can submit Supplementary VAT Statement. In case user wants to issue the Supplementary VAT Statement, it is necessary to choose Supplementary type of VAT Statement by exporting the Statement.
In the Calculate and post VAT Settlement functionality, the Posted Document Number is stored in closed VAT entries as VAT Settlement No. for further filtering in VAT Statement and reports. This feature allows calculation and printing VAT statement for different VAT statements posted and submitted in one VAT Period.

## Non-deductible VAT

This functionality is important due to §76 of VAT Law 235/2004 – the shortened claim to deduction.
The functionality includes:

- Extension VAT posting setup – allow Non-deductible VAT.
- Special Non-deductible VAT Setup – user can set up Non Deductible VAT % and applicability.
- User can see VAT % (Non-deductible), VAT Base (Non-deductible), VAT Amount (Deductible) in the VAT Entry.
- VAT Statement functionality has been extended.
- Batch for adjusting non-deductible VAT after conversion of the coefficient - used after the end of the current calendar year to settle the tax deduction according to the newly calculated coefficient.
  
## VIES

The VIES report is used for sales declaration to tax authorities in EU (European Union) countries. By §102 of VAT Law 235/2004, payers are obliged to submit VIES declaration („Souhrnné hlášení“). The VIES declaration has to be submitted to the Tax Office electronically.
The VIES functionality allows to:

- Set up State Reporting 
- Select combinations of VAT Business/Product posting group (VAT Posting Setup) to include into the VIES Reporting
- Keep the VIES Reporting history
- Input all information needed for electronic file submission
- Suggest Lines for VIES Reporting
- Support corrective declarations
- Export data into file for electronic submission

## VAT registration in others countries

This functionality extends the possibility to work with VAT and allows the user to:

- Set up the company as the payer in the another EU country (new Registration Country table)
- Set up Exchange rates for Performance Country
- Set up Registration country for Customers and Vendors
- Set up Registration Country routes for changing VAT Bus. Posting Group
- Set up Registration Country for company
- Define the VAT Country and the Performance VAT Country on Documents
- Calculate and print VAT Statement for fulfilment in another Performance VAT country
- Calculate and post VAT Settlement for fulfilment in another Performance VAT country

## Unreliable payer

The amendment of VAT Law 235/2004 (§106a) introduced the institute of Unreliable Payer. The Treasury Department is obliged to publish the names of Unreliable Payers. 
This feature uses this service to obtain published information and indicate payer status on Vendor card and purchase documents. 
The Treasury Department also publishes information about registered bank accounts of the payer (only these accounts are allowed for payments). Information about payer registered bank accounts is stored on the Vendor Bank Accounts and used in Cash Management.

## VAT Exchange rate
The exchange rate is located in documents, but Czech Republic requires the possibility to set different exchange rates for posting and VAT in sales and purchase documents. This feature adds VAT Currency Code field and VAT Exchange Rate in documents. Users can change the exchange rate for VAT before document posting.

## VAT Identifier

VAT identifier extends VAT Posting Setup. User can add the same VAT Identifier to different lines of the VAT Posting Setup. This is useful for printing VAT Recapitulation on tax documents grouped by VAT Identifier.
The VAT Identifier is the part of the VAT Entry.

## Reverse charge statement

The amendment of VAT Law 235/2004 (§ 92a – 92e) introduced the VAT Reverse Charge calculation also for specific domestic fulfilments. A Reverse Charge Statement has to be submitted to the Tax Office electronically. 
This feature allows user to:

- Select combinations of VAT Business/Product posting group (VAT Posting Setup) to include into the Reverse Charge Statement
- Set the Tariff Number Statement Code and Unit of Measures for Reverse Charge Statement
- Input all information on Sales and Purchase documents needed for electronic file submission
- Print Reverse Charge Statement
- Export Reverse Charge Statement data into the file for electronic submission

## VAT Control report

[!INCLUDE[d365fin](../../includes/d365fin_md.md)] functionality has been extended by the VAT Control Report. Basic form is VAT Control Report Card. VAT items are loaded by the VAT Date or Posting Date (according to the general ledger setup) into the form for the selected period. The basic setup, i.e. distribution of combinations of VAT posting groups into the individual sections of control report, is determined in the VAT statement. To process the control report you have to setup VAT control report sections, tariff numbers, VAT statement, stat. reporting setup and extended the VAT posting setup. Functionality contains:

- VAT Control Report Card - allows you to select report period.
- Control report lines suggestion - loads control report lines of selected period.
- Control performance - VAT Control Report - test report - prints overview according to individual sections.
- Control report export - Export function exports control report to the file.
- Closing lines - Close lines function fills the Closed by document no. field in control report lines.

## VAT Reports

In order to achieve requirements in legislation reporting and local reporting practices of Czech companies, this feature provides the following reports:

- Calc. and Post VAT Settlement – standard report adjusted
- Documentation for VAT
- VAT Document List 
- VAT List on Sales Adv. Letter
- VAT List on Purch. Adv. Letter
- Reverse Charge Statement

## See Also

[Czech Local Functionality](czech-local-functionality.md)