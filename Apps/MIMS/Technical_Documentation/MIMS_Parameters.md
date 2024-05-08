---
title: MIMS_Parameters
description: 
published: true
date: 2024-01-17T13:26:54.303Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:14:07.451Z
---

The MIMS parameters are settings that will affect the functionality of MIMS globally

The parameters are stored as User Codes against the `GHA_MIMS` User Code Type

These parameters can be modified using the GHA Parameters Screen within Epicor
- Under `Integrations > MIMS`

# Parameters
The following section will detail each parameter defined within the GHA Parameters Screen

## No Keyboard
This parameter determines if the keyboard should be globally disabled throughout the app

## MIMS Parameters
This section details the parameters under the "MIMS Parameters" group

### Picking Options
> This parameter currently has no affect in MIMS


### Material Queue
> This parameter currently has no affect in MIMS


### Putaway
> This parameter currently has no affect in MIMS


## Order Picking
The following section details the parameters defined within the "Order Picking" section

### Picking Type
This parameter changes how the Orders should be grouped within [Order Picking](Applets/Order_Picking/Order_Picking.md) on the [Select Order Type Screen](Applets/Order_Picking/Screens/Select_Order_Type_Screen.md)
- It is stored against the User Code `PullType` which will be set to one of the following values
	- `SHIPTO`
	- `SHIPVIA`
	- `ORDER`

This parameter can be set to
- Ship To
- Ship Via
- Order

> *Please note that Ship Via has no affect within MIMS currently*


### Dashboard Driven Picking
Controls dashboard-driven picking for [Order Picking](Applets/Order_Picking/Order_Picking.md)
- This is stored against the User Code 

Orders will be shown as defined within the [Order Picking Dashboard](./Order_Picking_Dashboard.md)

If this option is enabled, the app will skip the [Select Order Type Screen](./Applets/Order_Picking/Screens/Select_Order_Type_Screen.md)
- As the only first available Order Release will be shown

If this option is disabled, the app will always show the [Select Order Type Screen](./Applets/Order_Picking/Screens/Select_Order_Type_Screen.md)
- As all assigned Order Releases will be shown


### Display Next Pick Only
When enabled, only the first Order Release will be shown on the [Select Order Release Screen](./Applets/Order_Picking/Screens/Select_Order_Release_Screen.md)
- This is stored against the User Code `NextOnly`

### Default Report Style
This parameter is used to define the default Report Style to use for printing Pack Slips
- This is stored against the User Code `PackSlip`


### Staging Options
> This parameter is currently unused and has no functionality 


## Goods In
The following section describes the parameters defined under the "Goods In" section


### Force Scan of Receipt Location
This parameter determines if manual input of controls should be disabled in [Goods In](./Applets/Goods_In/Goods_In.md), forcing the User to scan each input
- This is stored against the User Code `GIScan`


### Use Primary Bin As Default
This parameter determines if the Primary Bin should be the default bin to receive into
- This is stored against the User Code `GIPrim`

> This parameter currently has no affect in MIMS


### Default Report Style (PO)
This parameter defines the default report style to use for printing Purchase Orders
- This is stored against the User Code `PORecipt`


### Default Report Style (RMA)
This parameter defines the default report style to use for printing RMA Receipts
- This is stored against the User Code `RMAReceipt`


## Job Receipting
The following section describes the parameters defined under the "Job Receipting" section


### Force Scan of Receipt Location
This parameter determines if manual input of controls should be disabled in [Job Receipts](./Applets/Job_Receipts/Job_Receipts.md), forcing the User to scan each input
- This is stored against the User Code `JobScan`


### Default Report Style (Stk)
This parameter defines the default report style to use for printing Job To Stock Receipts
- This is stored against the User Code `JobRctStk`


### Default Report Style (Job)
This parameter defines the default report style to use for printing Job To Job Receipts
- This is stored against the User Code `JobRctJob`


## Move Stock
The following section describes the parameters defined under the "Move Stock" section


### Force Scan of Receipt Location
This parameter determines if manual input of controls should be disabled in [Move Stock](./Applets/Move_Stock/Move_Stock.md), forcing the User to scan each input
- This is stored against the User Code `MSScan`

> This parameter currently has no effect in MIMS


### Default Report Style
This parameter defines the default report style to use for printing Move Stock Receipts
- This is stored against the User Code `StkReceipt`

> This parameter currently has no effect in MIMS


## Kanban Receipts
The following section describes the parameters defined under the "Kanban Receipts" section


### Force Scan of Receipt Location
This parameter determines if manual input of controls should be disabled in [Kanban Receipts](./Applets/Kanban_Receipts/Kanban_Receipts.md), forcing the User to scan each input
- This is stored against the User Code `KBScan`


### Default Report Style
This parameter defines the default report style to use for printing Kanban Receipts
- This is stored against the User Code `KBReceipt`


## Non Conformance
The following section describes the parameters defined under the "Non Conformance" section


### Force Scan of Receipt Location
This parameter determines if manual input of controls should be disabled in [NCRs](./Applets/NCRs/NCRs.md), forcing the User to scan each input
- This is stored against the User Code `NCRScan`


### Default Report Style
This parameter defines the default report style to use for printing Non Conformance transactions
- This is stored against the User Code `NCRTags`


### Stored Image Settings
This parameter defines the quality for the images that are saved as part of Non Conformance
- This is stored against the User Code `NCRImag` accepting the following values
	- `HIGH`
	- `MED`
	- `LOW`

This will affect the size of the files that will be taken up in Epicor

> This parameter currently has no effect in MIMS
