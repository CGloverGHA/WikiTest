---
title: Epicor_Processes
description: 
published: true
date: 2024-01-17T13:33:53.150Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:17:20.653Z
---

# Getting The RMA
The following REST calls are made in the following order
```mermaid
flowchart

A[Erp.BO.RMAProcSvc/GetByID]
```

Then the unfinished lines are filtered, using the following criteria
- The total receipted quantity is less than the remaining `ReturnQty`
	- The total receipt quantity is calculated by summing the `ReceivedQty` of each receipt under the `Receipts` object
- `OpenRMA == true`
- `OpenDtl == true`

# Getting The PO
The following REST calls are made in the following order
```mermaid
flowchart

A[Erp.BO.POSvc/GetByID]
```

Then the valid releases are filtered, using the following criteria
- `RelQty - ArrivedQty - ReceivedQty > 0`
- `OpenRelease == true`
- `DropShip == false`

# Creating The PO Receipt
Given that the PO Receipt already exists, [Creating A New PO Receipt](#creating-a-new-po-receipt) can be skipped

## Creating A New PO Receipt
The following REST calls are made in the following order
```mermaid
flowchart

A[Erp.BO.ReceiptSvc/GetPOInfo]
B[Erp.BO.ReceiptSvc/GetRvcHeadFromPONum]
C[Erp.BO.ReceiptSvc/UpdateMaster]

A --> B --> C
```

A call to `~/ERP.BO.ReceiptSvc/GetPOInfo` is made to get default information from the selected Purchase Order

A call to `~/Erp.BO.ReceiptSvc/GetRvcHeadFromPONum` is made to get additional information from the Purchase Order

A call to `~/Erp.BO.ReceiptSvc/UpdateMaster` is made to create the receipt

## Adding A Line To The PO Receipt
The following REST calls are made in the following order
```mermaid
flowchart

A[Erp.BO.ReceiptSvc/GetByID]
B[Erp.BO.ReceiptSvc/GetNewRcvDtl]
C[Erp.BO.ReceiptSvc/GetPOLineInfo]
D[Erp.BO.ReceiptSvc/SetReceiptAsReceived]
E[Erp.BO.ReceiptSvc/UpdateMaster]

A --> B --> C --> D --> E
```

A call to `Erp.BO.ReceiptSvc/GetByID` is made to get the receipt

A call to `~/Erp.BO.ReceiptSvc/GetNewRcvDtl` is made to get a new dataset for the receipt line

A call to `~/Erp.BO.ReceiptSvc/GetPOLineInfo` is made to get default information for the selected Purchase Order Line

A call to `~/Erp.BO.ReceiptSvc/SetReceiptAsReceived` is made to mark the receipt as receieved

A call to `~/Erp.BO.ReceiptSvc/UpdateMaster` is made to save the changes

# Creating The RMA Receipt
## Adding A Line To The RMA Receipt
The following REST calls are made in the following order
```mermaid
flowchart

A[Erp.BO.RMAProcSvc/GetByID]
B[Erp.BO.RMAProcSvc/GetNewRMARcpt]
C[Erp.BO.RMAProcSvc/PreUpdate]
D[Erp.BO.RMAProcSvc/Update]

A --> B --> C --> D
```

A call to `~/Erp.BO.RMAProcSvc/GetByID` is made to get the receipt to amend

A call to `~/Erp.BO.RMAProcSvc/GetNewRMAReceipt` is made to get a new dataset for the receipt line

A call to `~/Erp.BO.RMAProcSvc/PreUpdate` is made to get default information from Epicor

A call to `~/Erp.BO.RMAProcSvc/Update` is made to add the RMA Receipt line and save the changes

# Printing
## PO Receipts
The following API calls are made in the following order
```mermaid
flowchart

A[Erp.Rpt.RcvLabelSvc/SubmitToAgent]
```
- Refer to [How MIMS Creates Reports In Epicor](../../Printing.md#how-mims-creates-reports-in-epicor) for additional information about this REST call

## RMA Receipts
The following API calls are made in the following order
```mermaid
flowchart

A[Ice.LIB.SessionModSvc/SetEmployee]
B[Erp.Rpt.RMAFormSvc/SubmitToAgent]
```
- Refer to [How MIMS Creates Reports In Epicor](../../Printing.md#how-mims-creates-reports-in-epicor) for additional information about this REST call