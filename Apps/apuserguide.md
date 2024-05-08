---
title: AP Automation User Guide
description: AP User
published: true
date: 2024-01-19T15:07:38.289Z
tags: 
editor: markdown
dateCreated: 2023-12-21T14:11:25.526Z
---

[Back to AP Automation Home](/Apps/ap-automation)

# AP Automation User Guide

## AP Automation
To use the AP automation, navigate to GHA Modifications> AP Automation> General Operations> AP Automation Dashboard

•	When the dashboard opens, there are options to review or retrieve the invoices/PO data. See images below.
•	Selecting the  supplier – (<span style="color:blue">1</span>), will retrieve invoices only for that supplier
•	Selecting the Creation Date From and/or Creation Date To (<span style="color:blue">2</span>) will retrieve invoices between those dates.
•	Once any selection criteria have been set, select the Retrieve button (<span style="color:blue">3</span>).   NB Selecting the retrieve button without any predefined criteria will retirive ALL invoices awaiting processing.
•	Once the retrieve has completed, the invoice will be displayed in the Invoices panel – (<span style="color:blue">4</span>)
•	The lines are displayed in the Invoice Lines panel -(<span style="color:blue">5</span>)
•	The scanned invoice can be seen in the Invoice side panel – (<span style="color:blue">6</span>)
### Classic
![ap4.png](/apautomation/ap4.png)

### Kinetic
![ap5.png](/apautomation/ap5.png)

•	Select the Invoice (<span style="color:blue">1</span>) below and then view the Match type (<span style="color:blue">2</span>). This will prepopulate based on the Parameters or supplier settings. If nothing is populated, then this can be selected or left blank
•	Select Process All – (<span style="color:blue">3</span>)
### Classic
![ap6.png](/apautomation/ap6.png)

### Kinetic
![ap7.png](/apautomation/ap7.png)

•	Once the invoices have been processed, the Invoices panel is updated – (<span style="color:blue">1</span>) below.
•	If the invoice and PO has been successfully matched the Status will update to processed and the Match Status will update to Fully Matched - (<span style="color:blue">2</span>)
•	If the invoice has not been matched, the Match Type will show as No Match (<span style="color:blue">3</span>).
•	If required, the Override Match button can be selected – (<span style="color:blue">4</span>). Selecting the Override Match allows the matching to be manual
### Classic
![ap8.png](/apautomation/ap8.png)
### Kinetic
![ap9.png](/apautomation/ap9.png)

•	If the invoice is matched (<span style="color:blue">1</span>) below, then the AP Invoice group is automatically created which can be seen in the Group field (<span style="color:blue">2</span>), along with the AP Invoice
![ap10.png](/apautomation/ap10.png)

•	This can also be seen by opening AP Invoice Entry, where the corresponding group and invoice(s) are displayed – see below
![ap11.png](/apautomation/ap11.png)

## Override Match
### Classic
•	Select the Invoice Details (<span style="color:blue">1</span>) below and the amount will be updated in the Matched Amount field – (<span style="color:blue">2</span>)
•	Once completed, select save Matches – (<span style="color:blue">3</span>)
![ap12.png](/apautomation/ap12.png)

### Kinetic
•	Select the Override Match (<span style="color:blue">1</span>) and the Override Match screen will open.
•	Select the invoice lines (<span style="color:blue">2</span>) and the amount will be updated in the Matched Amount field – (<span style="color:blue">3</span>)
•	A visual representation of the invoice can be seen (<span style="color:blue">4</span>) – *NB this is only in Kinetic*
•	Once completed, select save Matches – (<span style="color:blue">5</span>)
![ap13.png](/apautomation/ap13.png)

## Errors
The invoice may have failed to match because of an error not related to the invoice/PO match – for example, if the purchasing terms code is missing. 
These can be seen on the Invoices panel by scrolling across to find the Error – (<span style="color:blue">1</span>) below.
**Classic**
![ap14.png](/apautomation/ap14.png)
**Kinetic**
![ap15.png](/apautomation/ap15.png)

## Reviewing by Document ID
Once the invoices have been processed, the details can be reviewed by using the document ID retrieval.

**Classic**
•	Select Document ID (<span style="color:blue">1</span>) below and the search window will open
•	Select Search - (<span style="color:blue">2</span>)
•	The previous created results are shown – (<span style="color:blue">3</span>)
•	Select row(s) – (<span style="color:blue">4</span>) and then select OK - (<span style="color:blue">5</span>)
![ap16.png](/apautomation/ap16.png)
•	The rows are retrieved and can be seen – (<span style="color:blue">1</span>) below
![ap17.png](/apautomation/ap17.png)

**Kinetic**
•	Select Document ID (<span style="color:blue">1</span>) below and the search window will open
•	Select Search - (<span style="color:blue">2</span>)
![ap18.png](/apautomation/ap18.png)
•	The previous created results are shown – (<span style="color:blue">1</span>) below
•	Select row(s) – and then select OK - (<span style="color:blue">2</span>)
![ap19.png](/apautomation/ap19.png)

