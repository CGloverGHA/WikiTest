---
title: GHA_MIMS_Employees
description: 
published: true
date: 2024-01-17T13:34:50.893Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:19:00.036Z
---

This BAQ Returns a list of active employees assigned to use MIMS

# Criteria
- This BAQ returns **active** employees (`EmpStatus = 'A'`)
- This BAQ returns **MIMS employees** (`GHA_MIMS_MIMSUser_c = true`)

# Sorting
- Results are ordered by `EmpBasic.Name`

# Returned Fields
## `EmpBasic.EmpID`
The employee's identifier

## `EmpBasic.FirstName`
The employee's first name

## `EmpBasic.Name`
The employee's full name

## `EmpBasic.GHA_PIN_c`
A User Field that defines a PIN that the employee can use to secure / login to the app

## `EmpBasic.GHA_MIMS_Layout_c`
Stores the employee's user settings for MIMS
- See [User Preferences](../../User_Preferences.md) for more information

## `EmpBasic.MaterialHandler`
A Boolean to indicate if the employee is a Material Handle

## `EmpBasic.ShopSupervisor`
A Boolean to indicate if the employee is a Shop Supervisor

## `EmpBasic.ShipRecv`
A Boolean to indicate if the employee handles Shipping and Receiving

## `EmpBasic.WarehouseManager`
A Boolean to indicate if the employee handles Shipping and Receiving
