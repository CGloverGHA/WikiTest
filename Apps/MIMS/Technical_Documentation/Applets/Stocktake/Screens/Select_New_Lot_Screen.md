---
title: Select_New_Lot_Screen
description: 
published: true
date: 2024-01-17T13:38:39.312Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:37:07.894Z
---

This screen is used to create a new Lot

# Flow

# Controls
## Lot Number
This control is used to enter the Lot Number of the Lot to create

## Scan
This control is used to scan the new Lot Number using the device's camera

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)
## Select
This button is used to create the new Lot in Epicor

### When This Button Is Tapped
The app will validate the selection

If the [Entered Lot Number](#lot-number) is empty
- An error with the message, "You need to enter a Lot Number", is shown

The app will validate the selected Lot Number
- This is done via a REST call to `~/Erp.BO.LotSelectUpdateSvc/LotSelectUpdates`

If no lot is returned
- A prompt with the message, "Lot not on file, create new?", is shown

If the User selects "Yes"
- The app will create the Lot
	- See [Creating A New Lot](../Epicor_Processes.md#creating-a-new-lot)

If the User selects "No"
- Nothing will happen

Given that a lot is returned

The app will add the Part to the selected Lot
- See [Adding A Part To The Lot](../Epicor_Processes.md#adding-a-part-to-the-lot--stocktake)

The app then navigates to the [Select Lot Screen](./Select_Lot_Screen.md)

# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Lot Format](../../../Scanning.md#lot-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will set the [Selected Lot Number](#lot-number) to the value of the barcode

Then the [Select Button Logic](#when-this-button-is-tapped-1) is followed