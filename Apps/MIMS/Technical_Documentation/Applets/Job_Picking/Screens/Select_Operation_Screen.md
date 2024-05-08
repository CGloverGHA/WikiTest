---
title: Select_Operation_Screen
description: 
published: true
date: 2024-01-17T13:36:10.185Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:28:42.569Z
---

This screen is used to filter the materials shown on the [Entire Job Screen](./Entire_Job_Screen.md)

This page will also show the following details about the current job & selected assembly:
- Job Number
- Part Number
- Part Revision Number
- Selected Assembly Description

If the user had previously selected a sub-assembly on the [Select Sub-Assembly Screen](./Select_Sub-Assembly_Screen.md), the sub-assembly operations will be shown

If the user had navigated to this screen from the [Selection Home Screen](./Selection_Home_Screen.md), then the operations of the main-assembly will be shown


# Flow
```mermaid
flowchart

A[Select Operation Screen]
B[Entire Job Screen]

A --> B
```


# When This Page Is Loaded...
The Selected Assembly's operations are filtered by the following criteria:
- The operation must not be complete
- The operations must contain at least one material that meets the following criteria:
	- The material must not be Issued Complete `(IssuedComplete = False)`
	- The material must require issuing `(IssuedQty - RequiredQty > 0)`

After the operations have been filtered:
- If there are 0 operations, the app will navigate to the [Entire Job Screen](./Entire_Job_Screen.md)
- If there is 1 operations, the app will:
	- Set the Selected Operation to the only operation, in the application data
	- Navigate to the [Entire Job Screen](./Entire_Job_Screen.md)

# Controls
## Operation
This control is used to select an operation for filtering the materials on the [Entire Job Screen](./Entire_Job_Screen.md)


## Scan
This button is used to allow the user to scan an operation

### When This Button Is Tapped...
See [Camera Scanning](#camera-scanning)


## Select
This button is used to validate the selection and navigate to the [Entire Job Screen](./Entire_Job_Screen.md)

### When This Button Is Tapped...
If no operation has been selected, the following error message is displayed to the User

Then the app will navigate to the [Entire Job Screen](./Entire_Job_Screen.md)


# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


# Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


# How The Scanned Barcode Is Handled
The barcode is validated against the defined [Operation Format](../../../Scanning.md#operation-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will attempt to find the scanned operation from the list of [Operations](#operation)

If no operation is found:
- An error with the message "Operation not found" will be shown to the user

If an assembly is found:
* The [Select Button Logic](#when-this-button-is-tapped-1) is followed