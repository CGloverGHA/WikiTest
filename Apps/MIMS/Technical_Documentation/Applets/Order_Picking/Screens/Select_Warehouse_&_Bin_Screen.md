---
title: Select_Warehouse_&_Bin_Screen
description: 
published: true
date: 2024-01-17T13:38:15.731Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:35:48.692Z
---

This screen is used to select a Warehouse & Bin to pick the selected Order Release's Part from

This page will display the following information about the current selection
- The selected Order
- The selected Order's Part
- The Required Quantity

# Flow
See [Part Flow](../Navigation.md#part-flow)

# When This Page is Loaded
The bins are retrieved from Epicor
- This is done via a REST call to `~/Erp.BO.PartBinSearchSvc/GetFullBinSearch` and a subsequent call to `~/Erp.BO.WarehseSvc/Warehses` for each Bin
- Supplier Managed bins are ignored here

# Controls
## Warehouse Bin List
This control is used to select a Warehouse Bin containing the selected Order Release's Part

### When A Warehouse Bin Is Tapped
The app will save the selected Warehouse Bin to [Application Storage](../../../Application_Storage.md)

Then the app will navigate to the next screen as defined under [Part Flow](../Navigation.md#part-flow)

# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Warehouse Bin Format](../../../Scanning.md#warehouse-bin-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

If the User scanned a barcode for a Supplier Managed Bin
- An error with the message, "Not allowed, scanned bin is supplier managed", is shown

Then the app will set the [Selected Warehouse Bin](#warehouse-bin-list) to the value of the barcode

Then the [Warehouse Bin Tap Logic](#when-a-warehouse-bin-is-tapped) is followed