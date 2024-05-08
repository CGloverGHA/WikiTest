---
title: Select_Serials_Screen
description: 
published: true
date: 2024-01-17T13:37:50.432Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:34:13.475Z
---

This screen is used to select the Serials for the selected Part

In this screen, the user can select from a list of existing serial numbers for the selected part

'../../../../Technical Documentation/Applets/NCRs/Screens'# Flow
```mermaid
flowchart

A[Select Serials Screen]
B[Select Quantity Screen]

A --> B
```


# When This Page Is Loaded
The selected Part's serials are retrieved from Epicor
- This is done via a REST call to `~/SerialNoSvc/SerialNoes`


# Controls
## Part Serials
This list shows all of the available serials that can be selected

The user may select any of the serials in and order they please


## Scan
This button is used to scan the serials with the device's camera

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)


## Select
This button will validate the selection and navigate to the next screen

### When This Button Is Tapped
The selection is validated

If no serials have been selected
- An error with the message, "Please choose at least one serial", will be shown to the user

The app will then follow the navigation logic defined under [Flow](#flow)


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

Then the app will attempt to find the scanned serial from the list of [Serials](#part-serials)

If no serial is found:
- A toast with the message, "Serial 'SERIALNUMBER' not found. Try again", will be shown to the user
	- `SERIALNUMBER` being the serial number interpreted from the scanned barcode

If a serial is found:
- The found serial number will be selected and checked within the list of [Serials](#part-serials)
- A toast with the message, "Serial 'SERIALNUMBER' scanned", will be shown to the user
	- `SERIALNUMBER` being the serial number interpreted from the scanned barcode
