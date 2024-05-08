---
title: Select_Order_Release_Screen
description: 
published: true
date: 2024-01-17T13:38:07.968Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:35:16.259Z
---

This screen is used to select an Order Release to create a Customer Shipment for

# Flow
See [Part Flow](../Navigation.md#part-flow)

# When This Page Is Loaded
If no Order Releases have been retrieved previously
- The app will retrieve the Order Releases from Epicor
	- See [Getting The Order Releases](../Epicor_Processes.md#getting-the-order-releases)

Then the app will filter the Order Releases

If the [Dashboard Driven Picking Parameter](../../../MIMS_Parameters.md#dashboard-driven-picking) is `true`
- The app will not filter the Order Releases

If the [Picking Type Parameter](../../../MIMS_Parameters.md#picking-type) is `SHIPTO`
- The app will filter the Order Releases by
	- The `ShipToNum` field, if defined
	- Otherwise the `CustNum` field

If the [Picking Type Parameter](../../../MIMS_Parameters.md#picking-type) is `ORDER`
- The app will filter the Order Releases by
	- The `OrderNum` field, if defined

If the [Display Next Pick Only Parameter](../../../MIMS_Parameters.md#display-next-pick-only) is `true`
- The app will only show the first Order Release

Otherwise, the resulting Order Releases will be filter by
- `ReqQty != 0`

And ordered by
- `PickingSeq`
	- See [GHA_MIMS_PickingSeq_c](../../../Epicor/User_Fields/OrderRel/GHA_MIMS_PickingSeq_c.md)
- `BinSeq`
- `PrimaryWarehouse`
- `PrimaryBin`

# Controls
## Order Release List
This control is used to select an Order Release to pick

### When An Order Release Is Tapped
The app will clear the following properties from the [Application Storage](../../../Application_Storage.md)
- `SelectedLotNumber`
- `SelectedPartSerials`
- `SelectedWarehouseBin`
- `SelectedQuantity`

The app will then navigate to the next screen as defined under [Part Flow](../Navigation.md#part-flow)