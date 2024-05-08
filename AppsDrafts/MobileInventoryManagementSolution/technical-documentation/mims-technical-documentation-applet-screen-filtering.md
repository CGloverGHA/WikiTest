---
title: mims-technical-documentation-applet-screen-filtering
description: 
published: true
date: 2024-01-17T13:32:13.326Z
tags: 
editor: markdown
dateCreated: 2023-12-15T09:40:37.215Z
---

When the applet screen is loaded, the current Employee's roles are evaluated, and then applets that are not relevant to their role(s) are hidden.

The following table shows what applets are shown per each role

| Option              | Material Handler | Shop Supervisor | Shipping & Receiving | Warehouse Manager | None |
| ------------------- |:----------------:|:---------------:|:--------------------:|:-----------------:|:----:|
| Bin Enquiry       |        🟩        |       🟩        |          🟩          |        🟩         |  🟩  |
| Part Enquiry      |        🟩        |       🟩        |          🟩          |        🟩         |  🟩  |
| Stock Take        |        🟩        |       🟩        |          🟥          |        🟩         |  🟥  |
| Move Stock        |        🟩        |       🟩        |          🟥          |        🟩         |  🟥  |
| Job Picking       |        🟩        |       🟩        |          🟥          |        🟩         |  🟥  |
| Job Receipts      |        🟩        |       🟩        |          🟥          |        🟩         |  🟥  |
| Job Returns       |        🟩        |       🟩        |          🟥          |        🟩         |  🟥  |
| Add & Issue Parts |        🟩        |       🟩        |          🟥          |        🟩         |  🟥  |
| Order Picking     |        🟥        |       🟩        |          🟩          |        🟩         |  🟥  |
| Tracking Number   |        🟥        |       🟩        |          🟩          |        🟩         |  🟥  |
| Reprint Labels    |        🟥        |       🟩        |          🟩          |        🟩         |  🟥  |
| Goods In          |        🟥        |       🟩        |          🟩          |        🟩         |  🟥  |
| NCRs              |        🟩        |       🟩        |          🟩          |        🟩         |  🟥  |
| Kanban Receipts   |        🟩        |       🟩        |          🟩          |        🟩         |  🟥  |
| Cycle Count       |        🟩        |       🟩        |          🟥          |        🟩         |  🟥  |
| Transfer Orders   |        🟥        |       🟥        |          🟥          |        🟩         |  🟥  |