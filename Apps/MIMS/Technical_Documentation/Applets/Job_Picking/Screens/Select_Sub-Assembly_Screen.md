---
title: Select_Sub-Assembly_Screen
description: 
published: true
date: 2024-01-17T13:36:15.269Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:28:58.442Z
---

This screen is used to select a sub-assembly to filter the materials shown on the [Entire Job Screen](./Entire_Job_Screen.md)

This screen also show the following details of the current job:
- Job Number
- Part Number
- Part Revision Number


# Flow
```mermaid
flowchart

A[Select Sub-Assembly Screen]
B[Select Operation Screen]
C[Entire Job Screen]

A --> B
A --> C
```


# When This Page Is Loaded...
The job's sub-assemblies are filtered by the following criteria:
- The assembly is not the main assembly `(AssemblySeq != 0)`
- The assembly contains at least one material that meets the following criteria:
	- The material is not Issued Complete `(IssuedComplete = False)`
	- The material needs to be Issued `(IssuedQty - RequiredQty > 0)`

If there is only one sub-assembly after the filtering, the app will navigate to the [Select Operation Screen](./Select_Operation_Screen.md)

# Controls
## Assembly
This controls allows the user to select a sub-assembly to filter the materials on


## Scan
This button allows the user to scan a sub-assembly

### When This Button Is Tapped...
See [Camera Scanning](#camera-scanning)

The Selected [Assembly](#assembly) is updated to the value of the barcode

Then the [Selection Button Logic](#when-this-button-is-tapped-1) is followed


## Select
This button will validate the [Selected Assembly](#assembly) and navigate to the [Select Operation Screen](./Select_Operation_Screen.md)

### When This Button Is Tapped
The app will navigate to the [Select Operation Screen](./Select_Operation_Screen.md)


# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Assembly Format](../../../Scanning.md#assembly-format)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will attempt to find the scanned assembly from the list of [Assemblies](#assembly)

If no assembly is found:
- An error with the message "The scanned barcode does not match any assemblies for this job" will be shown to the user

If an assembly is found:
* The [Select Button Logic](#when-this-button-is-tapped-1) is followed