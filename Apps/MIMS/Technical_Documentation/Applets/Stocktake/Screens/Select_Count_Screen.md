---
title: Select_Count_Screen
description: 
published: true
date: 2024-01-17T13:38:31.001Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:36:49.196Z
---

This screen is used to select a Count to use for the Stocktake process

# Flow
```mermaid
flowchart

A[Select Count Screen]
B[Select Warehouse Screen]

A --> B
```
When the user taps the [Select Button](#select)
- The app will navigate to the [Select Warehouse Screen](./Select_Warehouse_Screen.md)

# When This Page Is Loaded
The Counts are retrieved from Epicor
- This is done via a REST call to `~/Erp.BO.GHACountProcessingSvc/GHACountProcessings`

The list of [Counts](#count) is updated with these Counts

# Controls
## Count
This control is used to select a Count to use for the Stocktake process

## Select
This control is used to complete the selection and navigate to the next screen

### When This Button Is Tapped
The app will navigate to the next screen as defined under [Flow](#flow)
