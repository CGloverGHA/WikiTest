---
title: MIMS_Applets_Per_Employee_Role
description: 
published: true
date: 2024-01-17T13:26:51.687Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:14:03.882Z
---

These are the following Applets available per employee role

These roles include:
* Material Handler
* Shop Supervisor
* Shipping Receiving
* Warehouse Manager

Roles are defined against the employee in the `Employee Maintenance` form in Epicor

> [!NOTE] Note
> These roles are **additive**, meaning employees with multiple roles will be able to access the Applets defined in all roles

# Role Matrix
| Applet            | Material Handler | Shop Supervisor | Shipping Recieving | Warehouse Manager | Default Order |
| ----------------- |:----------------:|:---------------:|:------------------:|:-----------------:|:-------------:|
| Stock Take        |        🟩        |       🟩        |         🟥         |        🟩         |       1       |
| Bin Enquiry       |        🟩        |       🟩        |         🟩         |        🟩         |       2       |
| Part Enquiry      |        🟩        |       🟩        |         🟩         |        🟩         |       3       |
| Add & Issue Parts |        🟩        |       🟩        |         🟥         |        🟩         |       4       |
| Move Stock        |        🟩        |       🟩        |         🟥         |        🟩         |       5       |
| Job Picking       |        🟩        |       🟩        |         🟥         |        🟩         |       6       |
| Job Returns       |        🟩        |       🟩        |         🟥         |        🟩         |       7       |
| Job Receipts      |        🟩        |       🟩        |         🟥         |        🟩         |       8       |
| Order Picking     |        🟥        |       🟩        |         🟩         |        🟩         |       9       |
| Tracking Number   |        🟩        |       🟩        |         🟩         |        🟩         |      10       |
| Reprint Labels    |        🟩        |       🟩        |         🟩         |        🟩         |      11       |
| Goods In          |        🟥        |       🟩        |         🟩         |        🟩         |      12       |
| NCRs              |        🟩        |       🟩        |         🟩         |        🟩         |      13       | 
| Kanban Receipts   |        🟩        |       🟩        |         🟩         |        🟩         |      14       |

> [!NOTE] Note
> If an employee **has no roles assigned**, then **Part Enquiry** and **Bin Enquiry** will be shown