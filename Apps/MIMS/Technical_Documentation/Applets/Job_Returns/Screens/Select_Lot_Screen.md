---
title: Select_Lot_Screen
description: 
published: true
date: 2024-01-17T13:36:50.196Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:30:57.258Z
---

This screen is used to select a Lot to return to

This screen is only shown if the part is Lot tracked


# Flow
```mermaid
flowchart

A[Select Lot Screen]
B[Return Serials Screen]
C[Return Quantity Screen]

A --> B
A --> C
```
- If the material's part **is Serial Tracked**, the app will navigate to the [Return Serials Screen](./Return_Serials_Screen.md)
- If the material's part **is not Serial Tracked**, the app will navigate to the [Return Quantity Screen](./Return_Quantity_Screen.md)


# When This Page Is Loaded...
The Lot Numbers, for the selected Part, are retrieved from Epicor
- This is done via a REST call to `~/Erp.BO.LotSelectUpdateSvc/LotSelectUpdates`

Then the app will retrieve the Lot Numbers from the most recent Part Transactions for the selected Part
- This is done via a REST call to `~/Erp.BO.PartTranHistSvc/PartTranHists`

These Lot Numbers are then combined into one list with the most Part Transactions appearing first


# Controls
## Lot Number
This picker contains a list of Lot Numbers, for the selected Part, that the user can select from


## Scan
This button will allow the user to scan a Lot Number using the device's camera

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)


## Next Lot
This button will generate the next lot number for the selected Part and automatically select it

### When This Button Is Tapped...
A REST call is made to `~/Erp.BO.LotSelectUpdateSvc/GenerateNewLotNum` to generate the next Lot Number

This new Lot Number is then set as the selected [Lot Number](#lot-number)


## Select
This button will validate the selection and navigate to either the [Return Quantity Screen](./Return_Quantity_Screen.md) or the [Return Serials Screen](./Return_Serials_Screen.md) based on if the selected Part is Serial Tracked

### When This Button Is Tapped
The app checks that a Lot Number has been selected
- If no Lot Number has been selected, an error with the message "Please select a Lot Number" will be shown to the user

Otherwise, the app will follow the navigation logic as defined in the [Flow](#flow)


# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Lot Format](#lot-number)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will attempt to find the scanned Lot Number from the list of [Lot Numbers](#lot-number)

If no Lot Number is found:
- An error with the message "Could not find the scanned lot number", will be shown to the user

If a Lot Number is found:
* The [Select Button Logic](#when-this-button-is-tapped-2) is followed