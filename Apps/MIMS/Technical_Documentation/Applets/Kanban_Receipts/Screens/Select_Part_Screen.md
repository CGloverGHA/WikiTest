---
title: Select_Part_Screen
description: 
published: true
date: 2024-01-17T13:37:10.723Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:32:02.856Z
---

This screen is used to select a Part for the Kanban Receipts process

# Flow
See [Selection Flow](../Navigation.md#selection-flow)

# When This Screen Is Unloaded
The following properties will be removed from the [Application Storage](../../../Application_Storage.md)
- `SelectedPartRevision`
- `SelectedPartBin`
- `SelectedLotNumber`
- `SelectedSerials`
- `KanbanJobNum`

# Controls
## Part Number
This control is used to enter a Part Number to use for the Kanban Receipts process

## Scan
This control is used to scan the [Part Number](#part-number) using the device's camera

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)

## Select
This control is used to validate the selection and navigate to the next screen

### When This Button Is Tapped
The app will validate the selection

The app will try to get the selected Part from Epicor
- This is done via a REST call to `~/Erp.BO.PartSvc/GetByID`

If this does not return a result
- An error with the message, "The entered part could not be found", is shown

The app will then validate the Part's revisions, by the following criteria
- `Approved = true`
- `EffectiveDate < Today`

The app will then navigate to the next screen as defined under [Flow](#flow)

# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed

## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed

## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Part Format](../../../Scanning.md#part-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will set the [Selected Part Number](#part-number) to the value of the barcode

Then the [Select Button Logic](#when-this-button-is-tapped-1) is followed