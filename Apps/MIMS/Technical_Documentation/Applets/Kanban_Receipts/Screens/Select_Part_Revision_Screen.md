---
title: Select_Part_Revision_Screen
description: 
published: true
date: 2024-01-17T13:37:08.047Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:31:54.736Z
---

This screen is used to select a Part Revision for the selected Part

# Flow
See [Selection Flow](../Navigation.md#selection-flow)

# When This Screen Is Loaded
If there is only one Part Revision
- The app will set the [Selected Revision](#revision) to that Revision

# When This Screen Is Unloaded
The following properties will be removed from the [Application Storage](../../../Application_Storage.md)
- `SelectedPartBin`
- `SelectedLotNumber`
- `SelectedSerials`
- `KanbanJobNum`

# Controls
## Revision
This control is used to select the Part's Revision

## Scan
This control is used to scan the [Part Revision](#revision) using the device's camera

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)

## Select
This control is used to validate the selection and navigate to the next screen

### When This Button Is Tapped
The app will navigate to the next screen as defined under [Flow](#flow)

# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed

## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed

## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Part Revision Format](../../../Scanning.md#part-revision-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will attempt to find the scanned Part Revision in the [Revision List](#revision)

If no Revision is found
- An error with the message, "Could not find the scanned part revision. Please try again", is shown

If a Revision is found
- The app will set the [Selected Revision](#revision) to the value of the barcode
- Then the [Select Button Logic](#when-this-button-is-tapped-1) is followed