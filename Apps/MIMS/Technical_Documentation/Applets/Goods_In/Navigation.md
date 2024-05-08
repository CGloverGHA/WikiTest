---
title: Navigation
description: 
published: true
date: 2024-01-17T13:33:57.980Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:17:27.554Z
---

# Selection Flow
- The [Purchase Order Flow](#purchase-order) is followed, if the selected entry is a Purchase Order
- The [RMA Flow](#rma) is followed, if the selected entry is a RMA

## Purchase Order
If no Part Bin has been selected, and the selected PO Line's `TranType` is not equal to `PUR-UKN`
- The app will navigate to the [Select Warehouse & Bin Screen](./Screens/Select_Warehouse_%26_Bin_Screen.md)

If the selected PO Line's `TranType` is `PUR-UKN`
- The [Select Warehouse & Bin Screen](./Screens/Select_Warehouse_%26_Bin_Screen.md) is skipped
- The selected Part Bin is set to the default receiving Bin as defined in Epicor
	- This is retrieved via a REST call to `Erp.BO.PlantConfCtrlSvc/PlantConfCtrls(Company, Plant)`

If no lot number has been selected, and the selected PO Line's Part is lot-tracked
- The app will navigate to the [Select Lot Screen](./Screens/Select_Lot_Screen.md)

If no serial numbers have been selected, and the selected PO Line's Part is serial-tracked
- The app will navigate to the [Select PO Serials Screen](./Screens/Select_PO_Serials_Screen.md)

Otherwise, the app will navigate to the [Select Quantity Screen](./Screens/Select_Quantity_Screen.md)

## RMA
If no Part Bin has been selected
- The app will navigate to the [Select Warehouse & Bin Screen](./Screens/Select_Warehouse_%26_Bin_Screen.md)

If no lot number has been selected, and the selected PO Line's Part is lot-tracked
- The app will navigate to the [Select Lot Screen](./Screens/Select_Lot_Screen.md)

If no serial numbers have been selected, and the selected PO Line's Part is serial-tracked
- The app will navigate to the [Select RMA Serials Screen](./Screens/Select_RMA_Serials_Screen.md)

Otherwise, the app will navigate to the [Select Quantity Screen](./Screens//Select_Quantity_Screen.md)