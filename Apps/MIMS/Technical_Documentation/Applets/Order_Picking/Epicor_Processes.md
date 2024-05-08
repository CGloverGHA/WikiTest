---
title: Epicor_Processes
description: 
published: true
date: 2024-01-17T13:34:24.490Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:18:07.536Z
---

# Getting The Order Releases
The following API calls are made in the following order
```mermaid
flowchart 

A[BaqSvc/GHA_MIMS_OrderPicking]
```

See [GHA_MIMS_OrderPicking](../../Epicor/BAQs/GHA_MIMS_OrderPicking.md)

# Creating The Customer Shipment Entry
## Creating The Customer Shipment
The following API calls are made in the following order
```mermaid
flowchart

A[Erp.BO.CustShipSvc/CustShips]
```

A call is made to `~/Erp.BO.CustShipSvc/CustShips` to create a new Customer Shipment entry

## Adding The Lines To The Customer Shipment
The following API calls are made
```mermaid
flowchart

A[Erp.BO.CustShipSvc/GetByID]
B[Erp.BO.CustShipSvc/GetNewOrdrShipDtl]
C[Erp.BO.CustShipSvc/GetOrderLineInfo]
D[Erp.BO.CustShipSvc/GetOrderRelInfo]
E{If line is Kit Parent}
F[Erp.BO.CustShipSvc/GetQtyInfo]
G[Erp.BO.CustShipSvc/UpdateMaster]

A --> B
B --> C
C --> D
D --> E

E --> |Yes| F
E --> |No and loop is complete| G
E --> |No and loop is not complete| B

F --> |loop is not complete| B
F --> |loop is complete| G

```

An initial call to `~/Erp.BO.CustShipSvc/GetByID` is made to get the Customer Shipment
- If no Customer Shipment exists, a Customer Shipment will be created
	- See [Creating The Customer Shipment](#creating-the-customer-shipment)

Then each line will make the following API calls
- A call to `~/Erp.BO.CustShipSvc/GetNewOrdrShipDtl` is made to get a new line dataset
- A call to `~/Erp.BO.CustShipSvc/GetOrderInfo` is made to bring information over from the selected Order
- A call to `~/Erp.BO.CustShipSvc/GetOrderLineInfo` is made to bring information over from the selected Order Release's line
- A call to `~/Erp.BO.CustShipSvc/GetOrderRelInfo` is made to bring information over from the selected Order Release
- If the current Part is a Sales Kit Parent
	- A call to `Erp.BO.CustShipSvc/GetQtyInfo` is made to get the quantity for the Part

Finally, a call to `~/Erp.BO.CustShipSvc/UpdateMaster` is made to save the lines in Epicor

## Creating The Package
The following API calls are made in the following order
```mermaid
flowchart

A[Erp.BO.CustShipSvc/CustShips]
```

A call to `~/Erp.BO.CustShipSvc/CustShips` is made to update the package information with the selected package
# Completing The Customer Shipment
The following API calls are made in the following order
```mermaid
flowchart

A[Erp.BO.CustShipSvc/CustShips]
```

A call is made to `~/Erp.BO.CustShipSvc/CustShips` to set `ReadyToInvoice` to `true`

# Printing
## Packing Slips
A REST call is made to `~/Erp.Rpt.PackingSlipPrintSvc/SubmitToAgent`
- Where `PrintingOptions = 'S'`
- Refer to [How MIMS Creates Reports In Epicor](../../Printing.md#how-mims-creates-reports-in-epicor) for additional information about this REST call

## Shipping Labels
A REST call is made to `~/Erp.Rpt.PackingSlipPrintSvc/SubmitToAgent`
- Where `PrintingOptions = 'L'`
- Refer to [How MIMS Creates Reports In Epicor](../../Printing.md#how-mims-creates-reports-in-epicor) for additional information about this REST call

## Both
A REST call is made to `~/Erp.Rpt.PackingSlipPrintSvc/SubmitToAgent`
- Where `PrintingOptions = 'B'`
- Refer to [How MIMS Creates Reports In Epicor](../../Printing.md#how-mims-creates-reports-in-epicor) for additional information about this REST call