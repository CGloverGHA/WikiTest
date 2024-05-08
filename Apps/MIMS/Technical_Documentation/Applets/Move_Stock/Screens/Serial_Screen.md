---
title: Serial_Screen
description: 
published: true
date: 2024-01-17T13:37:38.145Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:33:32.728Z
---

This screen is used to select the serials of the selected Part to move

# When This Page Is Loaded
The selected Part's Serials are retrieved from Epicor
- This is done via a REST call to `~/Erp.BO.SerialNoSvc/List`

# Controls
## Part Serial List
This control displays a list of Serial numbers that the User can select


## Select All
This control is used to select all of serials from the [Part Serial List](#part-serial-list)

### When This Button Is Tapped
Each Serial from the [Part Serial List](#part-serial-list) will be selected


## Done
This control is used to save the selection and navigate to the next screen

### When This Button Is Tapped
The selected Serials are saved to the [Application Storage](../../../Application_Storage.md)

Then the app will navigate to the previous screen


# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan the serials

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


# Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


# How The Scanned Barcode Is Handled
The barcode is validated against the defined [Serial Format](../../../Scanning.md#serial-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will attempt to find the scanned serial from the list of [Serials](#part-serial-list)

If no serial is found:
- A toast with the message, "Serial 'SERIALNUMBER' not found. Try again", will be shown to the user
	- `SERIALNUMBER` being the serial number interpreted from the scanned barcode

If a serial is found:
- The found serial number will be selected and checked within the list of [Serials](#part-serial-list)
* A toast with the message, "Serial 'SERIALNUMBER' scanned", will be shown to the user
	* `SERIALNUMBER` being the serial number interpreted from the scanned barcode
