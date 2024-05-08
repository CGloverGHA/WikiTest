---
title: mims-technical-documentation-epicor-baq-GHA_MIMS_Employees
description: 
published: true
date: 2024-01-17T13:32:15.831Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:40:40.673Z
---

This BAQ returns a list of Employees to be shown on the login page in MIMS ordered by name.

This BAQ provides greater performance than the standard REST methods.

## Tables
The following tables are queried:
- `Erp.BO.EmpBasic`

## Criteria
The following criteria is applied to the `EmpBasic` table
- `EmpBasic.EmpStatus = 'A'`
- `EmpBasic.GHA_MIMS_MIMSUser_c = true`

## Fields
It returns the following fields

| Epicor Field                 | Description                                 |
| ---------------------------- | ------------------------------------------- |
| `EmpBasic.EmpID`             | Employee ID                                 |
| `EmpBasic.FirstName`         | Employee's First Name                       |
| `EmpBasic.Name`              | Employee's Name                             |
| `EmpBasic.GHA_PIN_c`         | Employee's MIMS PIN                         |
| `EmpBasic.GHA_MIMS_Team_c`   | Employee's Team for the Material Queue      |
| `EmpBasic.GHA_MIMS_Layout_c` | Employee's MIMS Preferences                 |
| `EmpBasic.MaterialHandler`   | *Is this user a Material Handler?*          |
| `EmpBasic.ShopSupervisor`    | *Is this user a Shop Supervisor?*           |
| `EmpBasic.ShipRecv`          | *Is this user handle Shipping & Recieving?* |
| `EmpBasic.WarehouseManager`  | *Is this user a Warehouse Manager?*         |

