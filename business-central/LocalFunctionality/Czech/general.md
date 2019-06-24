---
title: Czech Local Functionality - General function | Microsoft Docs
description: This section describes local functionality - General function
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, General function, Finance, CZ, Cash
ms.date: 15/05/2019
ms.author: 
---

# General function

## EXTENDED USER CONTROL
The majority of companies in the Czech Republic request the following improvements to be imple-mented in User Setup and Control. 

This feature in User Setup in combination with new User Setup Lines table allows to set and provide the following control:
- Assigning user to Employee No.
- Set Cash Resp. Ctr. Filter for Cash desk operations
- Check Document Date at posting against work date or system date
- Check Posting Date at posting against work date or system date
- Check access to Payment Orders – checks allowed Bank Accounts for payment orders (set in lines)
- Check access to Bank Statements – checks allowed Bank Accounts for bank statements (set in lines)
- Check Bank Accounts allowed for posting (set in lines)
- Check access to Journal Templates – check allowed Journal Templates for all Journal types (set in lines)
- Check Dimension Values allowed for posting (set in lines)
- Check Location Code allowed for posting separately for quantity increase and quantity decrease (set in lines)
- Check Location Code allowed for document release separately for quantity increase and quantity decrease (set in lines)
- Check usage of Whse. Net Change Templates at posting in Item Journals
- Allow Posting to Closed Period
- Allow Complete Job
- Allow Item Unapply functionality

## NO. SERIES ENHANCEMENTS
The majority of companies in the Czech Republic request the following improvements to be implemented in No. Series setup. 
### No. Series Mask
New field for No. Series structure mask added to the No. Series table where the user defines a position structure of the number generated in this No. Series. This feature makes creating new No. Series lines for new fiscal year easy and decreases the amount of mistakes. 
This Mask creates a new No. Series line using the new No. Series Mask Generator function.
### No. Series Links
New No. Series Link table added. The table contains setup of No. Series links for various system functions:
- Linked No. Series – what No. Series are to be used in linked activity if the source document has No. Series defined (e.g. Order Created from Quote, Order Created from Blanket Order, etc.)
- Posting No. Series – what No. Series are to be used for posted document if the source document has No. Series defined (e.g. for posted sales/purchase document (Invoice, Credit Memo) posted from sales/purchase document (Order, Return Order, Invoice, Credit Memo), issued reminder from reminder, etc.)
- Shipping No. Series – what No. Series are to be used for posted shipment if the source document has No. Series defined (e.g. posted Sales Shipment from Sales Order or Invoice, Transfer Shipment from Transfer Order, etc.)
- Receiving No. Series – what No. Series are to be used for posted receipt if the source document has No. Series defined (e.g. posted Purchase Receipt from Purchase Order or Invoice, Transfer Receipt from Transfer Order, etc.)
- Shipping Wh. No. Series – what No. Series are to be used for Warehouse Shipment if the source document has No. Series defined (e.g. Warehouse Shipment from Transfer Order)
- Receiving Wh. No. Series – what No. Series are to be used for Warehouse Receipt if the source document has No. Series defined (e.g. Warehouse Receipt from Transfer Order)

## Certificate Management
Certificate management is designed as a general module for managing security certificates for communication and integration with other applications and web services. It can be used in various implementations (eg the EET solution within the application uses this module for communication with the financial management server).

Examples of using a certificate:
- Electronic signing of documents (pdf, xml, etc.)
- Electronic signature verification
- Encryption
- Decryption,
- Another possible use according to the nature of the certificate.

## See Also
[Czech Local Functionality](czech-local-functionality.md)  
