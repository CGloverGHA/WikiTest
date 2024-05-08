---
title: Print_Screen
description: 
published: true
date: 2024-01-17T13:39:05.139Z
tags: 
editor: markdown
dateCreated: 2023-02-01T17:12:25.400Z
---

This screen is used to reprint a Job Receipts transaction

# Flow
```mermaid
flowchart

A[Print Screen]
B[Main Menu Screen]

A --> B
```
# When This Page Is Loaded
The printers are retrieved from Epicor
- See [How MIMS Retrieves The Available Printers](../../../../Printing.md#how-mims-retrieves-the-available-printers)

The [Selected Printer](#printer) is set to the first default Printer

# Controls
## Printer
This control is used to select a Printer from the list of available Printers

## Print
This control is used to execute the selected Printing Option and complete the Customer Shipment

### When This Button Is Tapped
If no [Printer](#printer) has been selected
- An error with the message, "Please select a printer", is shown

The report is printed in the same way as in [Job Receipts](../../../Job_Receipts/Job_Receipts.md)
- See [Printing](../../../Job_Receipts/Epicor_Processes.md#printing)

The app then navigates to the [Home Page](../../../Home_Page.md)