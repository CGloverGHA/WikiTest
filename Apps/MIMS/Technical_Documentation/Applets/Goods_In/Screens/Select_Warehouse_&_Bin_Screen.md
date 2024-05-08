---
title: Select_Warehouse_&_Bin_Screen
description: 
published: true
date: 2024-01-17T13:35:51.838Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:27:45.178Z
---

This page is used to select the Warehouse and Bin to send the received Parts to

# Flow
See [Selection Flow](../Navigation.md#selection-flow)

# When This Page Is Loaded
The Warehouses and Bins are retrieved from Epicor
- This is done via a REST call to `~/Erp.BO.PartWhseSearchSvc/PartWhseSearches

The primary Warehouse is retrieved from Epicor
- This is done via a REST call to `Erp.BO.PartPlantSearchSvc/PartPlantSearches(Company, PartNum, Plant)`

The [Selected Warehouse](#warehouse) is set to the result (if any)

The primary Bin is retrieved from Epicor
- This is done via a REST call to `Erp.BO.PlantWhseSearchSvc/PlantWhseSearches(Company, Plant, PartNum, WarehouseCode)`

The [Select Bin](#bin) is set to the result (if any)

# Controls
## Warehouse
This control is used to select a Warehouse

### When A Warehouse Is Selected
The Bins from that Warehouse are retrieved from Epicor
- Initially, this will be done via a REST call to `~/BaqSvc/GHA_MIMS_Bins`
- As a fallback, this will be done via a REST call to `~/Erp.BO.WhseBinSvc/WhseBins`
	- This method will be used if the BAQ doesn't exist or the BAQ request fails

If the selected Entry is a PO
- All bins are returned, including Supplier Managed Bins, that match the Vendor on the PO Line

If the selected Entry is a RMA
- All but Supplier Managed Bins are returned

## Bin
This control is used to select a Bin from the selected Warehouse

## Scan
This control is used to scan the Warehouse and Bin using the device's camera

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)

## Select
This control is used to validate the selection and navigate to the next screen, following the logic defined under [Flow](#flow)

### When This Button Is Tapped
The app checks if a Warehouse has been selected

If no warehouse has been selected
- An error with the message, "Please select a warehouse", is shown
- Further execution halts

Then the app checks if a Bin has been selected
- An error with the message, "Please select a bin", is shown
- Further execution halts

Then the app saves the [Selected Warehouse](#warehouse) and the [Selected Bin](#bin) to the [Application Storage](../../../Application_Storage.md)

Then the app navigates to the next screen, following the logic defined under [Flow](#flow)

# Scanning
## Camera Scanning
The [Camera Scanning Process](#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scan-result-is-handled) is followed

## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scan-result-is-handled) is followed

## How The Scan Result Is Handled
### If The [Warehouse Control](#warehouse) Is Focused
The app will try to find the first [Warehouse](#warehouse) where the  `WarehouseCode` is equal to the barcode

If no Warehouse is found
- An error with the message, "Could not find Warehouse '{barcode}'", is shown
	- Where `{barcode}` is the value of the scanned barcode

### If The [Bin Control](#bin) Is Focused
The app will try to find the first [Bin](#bin) where the `BinNum` is equal to the barcode

if no Bin is found
- An error with the message, "Could not find '{barcode}' in '{warehouse}'", is shown
	- Where `{barcode}` is the value of the scanned barcode
	- Where `{warehouse}` is the description of the [Selected Warehouse](#warehouse)

### If No Control Is Focused
The barcode is validated against the defined [Warehouse Bin Format](../../../Scanning.md#warehouse-bin-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

The app will try to find the first [Warehouse](#warehouse) and [Bin](#bin)

If the [Warehouse](#warehouse) could not be found
- An error with the message, "Could not find Warehouse '{warehouse}'", is shown
	- Where `{warehouse}` is the interpreted Warehouse Code from the barcode

If the [Bin](#bin) could not be found
- An error with the message, "Could not find Bin '{bin}' in '{warehouse}'", is shown
	- Where `{bin}` is the interpreted Bin Number from the barcode
	- Where `{warehouse}` is the Warehouse Code of the scanned Warehouse

If the [Warehouse](#warehouse) and [Bin](#bin) is found:
* The [Select Button Logic](#when-this-button-is-tapped-1) is followed