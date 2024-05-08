---
title: Job_Details_Screen
description: 
published: true
date: 2024-01-17T13:36:02.231Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:28:18.313Z
---

This screen is used to show details about the current job

This information includes:
- Job Number
- Part Number
- Part Description
- Quantity
- Job Type
- Start Date
	- **Or Required By Date if Start Date is not defined**
- Materials To Issue

# Controls
## Entire Job
This button is used to navigate to the [Entire Job Screen](./Entire_Job_Screen.md)

### When This Button Is Tapped...
The `Selected Operation` and `Selected Assembly` is cleared in the application data

The app navigates to the [Entire Job Screen](./Entire_Job_Screen.md)


## Selection
This button is used to filter the materials by Assembly and or Operation

This button is disabled if the job contains no valid assemblies or operations

A valid assembly is defined by the following criteria:
- The main assembly `(AssemblySeq = 0)` contains at least one material that
	- Aren't Issued Complete `(IssuedComplete == False)`
	- The material requires issuing `(RequiredQty - IssuedQty > 0)`

A valid operation is defined by the following criteria:
- The operation must be under the main assembly `(AssemblySeq = 0)`
- The operation isn't complete `(Complete == False)`
- The operation contains at least one material that:
	- Aren't Issued Complete `(IssuedComplete == False)`
	- The material requires issuing `(RequiredQty - IssuedQty > 0)`

## When This Button Is Tapped...
The `Selected Operations` and `Selected Assembly` is cleared in the application data

The app navigates to the [Selection Home Screen](./Selection_Home_Screen.md)
