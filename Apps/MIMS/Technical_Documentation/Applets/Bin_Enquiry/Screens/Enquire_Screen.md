---
title: Enquire_Screen
description: 
published: true
date: 2024-01-17T13:35:24.869Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:26:16.530Z
---

This screen is used to enter the Warehouse and Bin to enquire


# When This Page Is Loaded...
All Warehouses, from the selected Site, are retrieved from Epicor
- This is done via the REST call `~/Erp.BO.WarehseSearchSvc/GetList`

These warehouses can then be selected from the [Warehouse](#warehouse) control


# Toolbar
## Help Button
This button is used to show the help screen for scanning the Warehouse and Bin


# Controls
## Warehouse
This control contains a list of all Warehouses, on the selected Site, that the user can select from

### When A Warehouse Is Picked...
The selected Warehouse is saved to the application data

The Warehouse Bins are retrieved from Epicor:
- Initially, this will be done via a REST call to `~/BaqSvc/GHA_MIMS_Bins`
- As a fallback, this will be done via a REST call to `~/Erp.BO.WhseBinSvc/WhseBins`
	- This method will be used if the BAQ doesn't exist or the BAQ request fails

These Warehouse Bins are then displayed in the [Bin](#bin) control

Then the [Bin](#bin) control is enabled


## Bin
This control is disabled until the user selects a [Warehouse](#warehouse)

When the user selects a [Warehouse](#warehouse), this control will be updated with a list of Bins within that Warehouse

### When A Bin Is Picker
The selected Bin is saved to the application data


## Scan
This button is used to scan a Warehouse and Bin using [Camera Scanning](../../../Scanning.md#camera-scanning)

## When This Button Is Tapped...
The Scanner Page is shown to the user

Once the barcode is scanned, it is validated against the following criteria:
- The barcode format must be `WAREHOUSECODE~BINNUM`
- The barcode must not be empty
- The `WAREHOUSECODE` must be the code of an existing Warehouse
- The `BINNUM` must be the number of an existing Warehouse Bin

If any of these criteria isn't met, an error message will be shown to the user

On successful, validation:
- The same logic is followed as described within [When This Button Is Tapped](#when-this-button-is-tapped-1)


## Select
This button is used to submit the selected [Warehouse](#warehouse) and [Bin](#bin) and navigate to the [Results Screen](./Results_Screen.md)

### When This Button Is Tapped...
The selected [Bin](#bin) is saved to the application data

The app navigates to the [Results Screen](./Results_Screen.md)