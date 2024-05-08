---
title: Navigation
description: 
published: true
date: 2024-01-17T13:34:15.127Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:17:50.362Z
---

# Selection Flow
```mermaid
flowchart

A[Current Page]
B[Select Part Revision Screen]
C[Select Warehouse & Bin Screen]
D[Select Lot Screen]
E[Select Serials Screen]
F[Select Quantity Screen]

A --> B
A --> C
A --> D
A --> E
A --> F
```

If the selected Part Revision has not been chosen
- The app will navigate to the [Select Part Revision Screen](./Screens/Select_Part_Revision_Screen.md)

If the selected Warehouse & Bin has not been chosen
- The app will navigate to the [Select Warehouse & Bin Screen](./Screens//Select_Warehouse_%26_Bin_Screen.md)

If the selected Part is lot-tracked and a lot number has not been chosen
- The app will navigate to the [Select lot Screen](./Screens/Select_Lot_Screen.md)

If the selected Part is serial-tracked and no serial numbers have been chosen
- The app will navigate to the [Select Serials Screen](./Screens/Select_Serials_Screen.md)

Otherwise
- The app will navigate to the [Selected Quantity Screen](./Screens//Select_Quantity_Screen.md)