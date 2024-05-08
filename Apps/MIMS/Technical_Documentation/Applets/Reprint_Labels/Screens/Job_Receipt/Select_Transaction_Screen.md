---
title: Select_Transaction_Screen
description: 
published: true
date: 2024-01-17T13:39:10.134Z
tags: 
editor: markdown
dateCreated: 2023-02-01T17:12:41.704Z
---

This screen is used to select a Transaction found from the select Job Number and Transaction Type

# Flow
```mermaid
flowchart

A[Select Transaction Screen]
B[Print Screen]

A --> B
```

# When This Page Is Loaded
The Transactions are retrieved from Epicor
- This is done via a REST call to `~/Erp.BO.PartTranSvc/PartTrans`

The transactions are then filtered by the selected Transaction Type
- If the selected Transaction Type is `Job to Inventory`
	- The transactions are filtered by `TranType = MFG-STK`
- If the selected Transaction Type is `Job to Job`
	- The transactions are filtered by `TranType = MFG-WIP`

# Controls
## Transactions
This control is used to select the Transaction to reprint

### When A Transaction Is Tapped
The selected Transaction is saved to the [Application Storage](../../../../Application_Storage.md)

The app navigates to the [Print Screen](./Print_Screen.md)