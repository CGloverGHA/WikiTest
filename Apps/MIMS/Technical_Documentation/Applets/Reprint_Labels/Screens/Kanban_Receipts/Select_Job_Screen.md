---
title: Select_Job_Screen
description: 
published: true
date: 2024-01-17T13:39:15.215Z
tags: 
editor: markdown
dateCreated: 2023-02-01T17:12:57.280Z
---

This screen is used to select the Job created from [Kanban Receipts](../../../Kanban_Receipts/Kanban_Receipts.md)

# Flow
```mermaid
flowchart

A[Select Job Screen]
B[Print Screen]

A --> B
```

# Controls
## Job Number
This control is used to enter the Job Number

## Scan
This control is used to scan the [Job Number](#job-number)

### When This Button Is Tapped
See [Camera Scanning](#camera-scanning)

## Select
This control is used to validate the selection and navigate to the next screen

### When This Button Is Tapped
The selection is validated

If no [Job Number](#job-number) has been entered
- An error with the message, "Please enter a Job Number", is shown

The app then navigates to the [Print Screen](./Print_Screen.md), as defined under [Flow](#flow)

# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../../Scanning.md#camera-scanning) is triggered to allow the user to scan a barcode

Then logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed

## Data Wedge Scanning
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed

## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Job Format](../../../../Scanning.md#job-number)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../../Scanning.md#barcode-validation-errors) will be shown to the user

Then the app will set the [Selected Job Number](#job-number) to the value of the barcode

Then the [Select Button Logic](#when-this-button-is-tapped-1) is followed