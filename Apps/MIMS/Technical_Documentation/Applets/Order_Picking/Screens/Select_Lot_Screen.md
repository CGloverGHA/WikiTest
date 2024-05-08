---
title: Select_Lot_Screen
description: 
published: true
date: 2024-01-17T13:38:05.416Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:35:05.109Z
---

This screen is used to select a Lot

# Flow
See [Part Flow](../Navigation.md#part-flow)

# When This Page Is Loaded
The lot numbers are retrieved from Epicor
- This is done via a REST call to `~/ERP.BO.LotSelectUpdateSvc/LotSelectUpdates`

# Controls
## Lot Number
This control is used to enter the Lot Number

## Scan
This control is used to scan the [Lot Number](#lot-number) with the device's camera

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)

## Select
This control validates the current selection and then navigates to the next screen as defined under [Flow](#flow)

### When This Button Is Tapped
The app checks that a Lot Number has been selected
- If no Lot Number has been selected, an error with the message "Please select a lot number" will be shown to the user

Otherwise, the app will follow the navigation logic as defined in the [Flow](#flow)


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