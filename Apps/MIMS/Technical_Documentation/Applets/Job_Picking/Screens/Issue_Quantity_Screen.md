---
title: Issue_Quantity_Screen
description: 
published: true
date: 2024-01-17T13:35:57.049Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:28:01.817Z
---

This screen allows the user to select the quantity of the part '../../../../Technical Documentation/Applets/Job Picking/Screens'they wish to issue

This screen cannot be accessed by serial tracked parts


# Flow
```mermaid
flowchart

A[Issue Quantity Screen]
B[Select Part Bin Screen]
C[Main Menu Screen]
D[Job Details Screen]
E[Entire Job Screen]

A --> B
A --> C
A --> D
A --> E
```
- If the Job Material was partially issued, the app will navigate to the [Select Part Bin Screen](./Select_Part_Bin_Screen.md)
- If the Job is entirely issued, the app will navigate to the [Home Page](../../Home_Page.md)
- If all Job Material's under the selected operation have been issued, the app will navigate to the [./Job Details Screen](./Job_Details_Screen.md)
- If the Job Material was fully issued, the app will navigate to the [Entire Job Screen](./Entire_Job_Screen.md)


# When This Page Is Loaded
The app will automatically determine a default quantity to select

The selected quantity will be set to the Quantity that is required

If the previously selected Part Bin has a quantity on hand that is less than the required quantity, the selected quantity will be set to the quantity on hand of the Part Bin


# Controls
## Selected Quantity
This control allows the user to enter a quantity of the part that they wish to issue

This entry uses a numerical keyboard


## Issued Complete
This control allows the user to choose if they want to mark the transaction as Issued Complete


## Back
This control allows the user to navigate to the previous screen

### When This Button Is Tapped
The app will navigate to the previous screen, which is the [Select Part Bin Screen](./Select_Part_Bin_Screen.md)


## Issue
This button performs the material movement for the selected part

### When This Button Is Tapped
#### Validation
If the user has entered a quantity that is **less than zero**
- An error with the message, "You cannot issue a negative quantity", is shown to the user

If the user has entered a quantity **of zero**
- An error with the message, "Please choose a quantity greater than 0", is shown to the user

*If the user has chosen a **non quantity bearing part** or **[Advanced Material Management](../../../AMM_Handling.md) is not licensed**, the following validation will be skipped*

If the user has chosen a quantity that exceeds an additional 20% of the selected Part Bin's quantity
- An error with the message, "You cannot issue more than {CALCULATED_MAX}", is shown to the user
	- Where `CALCULATED_MAX` is `Selected Part Bin Quantity + (Selected Part Bin Quantity / 100)`

#### Issue Material Transaction
After the selection has been successfully validated, the part is then issued to the Job Material
- This is done via a REST call to `~/Erp.BO.IssueReturnSvc/PerformMaterialMovement`

This call will issue the selected Part:
- To the selected Job Material
- From the selected Warehouse
- From the selected Part Bin
- From the selected Lot Number
- Using the selected [Issued Complete](#issued-complete) value

**If [AMM](../../../AMM_Handling.md) is not licensed**
- The `ToWarehouseCode` and `ToBinNum` parameters will not be set

**If [AMM](../../../AMM_Handling.md) is licensed** 
- The `ToWarehouseCode` and `ToBinNum` parameters will be set to the selected Warehouse and Part Bin

Once the material has been issued, the app will navigate to a screen based on the following logic 