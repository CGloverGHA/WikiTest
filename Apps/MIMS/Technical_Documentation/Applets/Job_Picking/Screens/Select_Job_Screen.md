---
title: Select_Job_Screen
description: 
published: true
date: 2024-01-17T13:36:04.830Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:28:26.527Z
---

This screen is used to enter the Job Number of the Job to issue materials to

# When This Page Is Loaded...

# Toolbar
## Home Button
This button is used to navigate back to the [Home Page](../../Home_Page.md)


# Controls
## Job Number
This control is used to input the Job Number


## Scan
This control is used to scan the Job Number

### When This Button Is Tapped...
See [Camera Scanning](#camera-scanning)


## Select
This control is used to submit the Job Number and navigate to the [Job Details Screen](./Job_Details_Screen.md)

### When This Button Is Tapped...
If the [Job Number](#job-number) is empty:
- A message is shown to the User
- This process ends

Then the Job is retrieved from Epicor
- If unsuccessful, a message is shown to the User
	- Then this process will end
- **If successful, all materials with a `RelatedOperation` of `0` will be set to `10`** 

Then the Job is checked to see if there are any materials to issue
- If there aren't a message is shown to the User

Then the Job is checked to see if it has been released
- It if hasn't been release, a message is shown to the User

Then the Job is checked to see if it has been completed
- If the job has been completed, a message is shown to the User

Given that all of the above was successful:
- The app will navigate to the [Job Details Screen](./Job_Details_Screen.md)


# Scanning
## Camera Scanning
The [Camera Scanning Process](../../../Scanning.md#camera-scanning) is started to retrieve the barcode

Then the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## Data Wedge Scanning Process
When a barcode is scanned by a data wedge, the logic defined under [How The Scanned Barcode Is Handled](#how-the-scanned-barcode-is-handled) is followed


## How The Scanned Barcode Is Handled
The barcode is validated against the defined [Job Number Barcode Format](../../../Scanning.md#job-number)

If the barcode is invalid:
- The relevant [Barcode Validation Error](../../../Scanning.md#barcode-validation-errors) will be shown to the user

If the barcode is valid:
* The [Select Button Logic](#select) is Followed