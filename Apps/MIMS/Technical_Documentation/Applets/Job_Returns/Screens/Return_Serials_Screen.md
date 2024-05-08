---
title: Return_Serials_Screen
description: 
published: true
date: 2024-01-17T13:36:45.267Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:30:39.855Z
---

This screen is used to return serials of a serial-tracked part

In this screen, the user can select from a list of existing serial numbers for the selected part. The user may then return however many of these serials as they wish

This screen will display the selected Part's Issued Quantity as the amount to return


# Flow
```mermaid
flowchart

A[Return Serials Screen]
B[Select Part Bin Screen]
C[Main Menu Screen]
D[Job Details Screen]
E[Entire Job Screen]

A --> B
A --> C
A --> D
A --> E
```
- If the Job Material was partially returned, the app will navigate to the [Select Warehouse & Bin Screen](./Select_Warehouse_%26_Bin_Screen.md)
- If the Job is entirely returned, the app will navigate to the [Home Page](../../Home_Page.md)
- If all Job Material's under the selected operation have been returned, the app will navigate to the [Job Details Screen](./Job_Details_Screen.md)
- If the Job Material was fully returned, the app will navigate to the [Entire Job Screen](./Entire_Job_Screen.md)


# When This Page Is Loaded
The app will retrieve the part's serials from Epicor'
- This is done via a REST call to `~/Erp.BO.SerialNoSvc/List`

If no serials are found
- An error with the message, "Could not find any serials to return", will be shown
- The app will navigate to the previous page


# Controls
## Issued Complete
This controls whether the material transaction should be marked as Issued Complete or not


## Part Serials
This list shows all of the available serials that can be selected to be issued

The user may select any of the serials in and order they please


## Scan
This button is used to scan the serials to select them

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)


## Return
This button will perform the material transaction, moving the chosen serials from the selected warehouse bin to the selected job

### When This Button Is Tapped
The selection is validated

If no serials have been selected:
- An error with the message, "Please choose at least one serial", will be shown to the user

Otherwise, the material transaction will be performed
- This is done via a REST call to `~/IssueReturnSvc/PerformMaterialMovement`

This call will return the selected Serials:
- From the selected Job Material
- To the selected Warehouse
- To the selected Part Bin
- To the selected Lot
- Using the chosen [Issued Complete](#issued-complete) value

#### Advanced Material Management
**If [AMM](../../../AMM_Handling.md) is not licensed**
- The `FromWarehouseCode` and `FromBinNum` parameters will not be set

**If [AMM](../../../AMM_Handling.md) is licensed** 
- The `FromWarehouseCode` and `FromBinNum` parameters will be set to the selected Warehouse and Part Bin


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
* A toast with the message, "Serial 'SERIALNUMBER' scanned", will be shown to the user
	* `SERIALNUMBER` being the serial number interpreted from the scanned barcode
