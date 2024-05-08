---
title: Enquiry_Screen
description: 
published: true
date: 2024-01-17T13:38:18.350Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:35:59.637Z
---

This page is used to enter a Part Number to be Enquired

# When This Page Is Loaded
- Buttons are enabled

# Toolbar Items
## Help Button
This button can be used to show the help screen for scanning the [Part Number](#part-number)


# Controls
## Part Number
This control is used to enter a Part Number that the user wishes to Enquire the locations of


## Scan
This button is used to use the device's camera to scan a barcode containing a Part Number that is entered into the [Part Number](#part-number) control

### When This Button Is Tapped...
The camera scanning process is triggered
- Refer to [Camera Scanning](../../../Scanning.md#camera-scanning) for further information

The resulting barcode is then verified against the format `PARTNUM` and `PRT~` 
- If the Barcode contains `PRT~`, the string after `PRT~` is entered into [Part Number](#part-number)
- If the Barcode doesn't contain `PRT~`, the entire barcode is entered into [Part Number](#part-number)

Then the same logic behind the [Select](#select) button is triggered
- See the [Selection Button Logic](#when-this-button-is-tapped-1)


## Select
This button is used to submit the entered [Part Number](#part-number) and navigate to the [Results Screen](./Results_Screen.md)

### When This Button Is Tapped...
The value entered for [Part Number](#part-number) is validated against Epicor
- This is done via a REST call to `~/Erp.BO.PartSvc/Parts`
	- With `$filter` being used to filter on the [Part Number](#part-number)

If validation is unsuccessful:
- An error message is shown

If validation is successful:
- [Part Number](#part-number) will be saved within the application data
- The app will navigate to the [Results Screen](./Results_Screen.md)