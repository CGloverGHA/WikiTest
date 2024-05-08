---
title: Navigation
description: 
published: true
date: 2024-01-17T13:34:26.842Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:18:13.318Z
---

# Part Flow
If the selected Order Release is a Sales Kit Parent
- Determined by `KitFlag = P`
- The app will navigate to the [Pack Screen](./Screens/Pack_Screen.md)

If the selected Warehouse Bin has not been chosen
- The app will navigate to the [Select Warehouse Bin Screen](./Screens/Select_Warehouse_%26_Bin_Screen.md)

If the selected Order Release's Part is lot-tracked and no lot has been chosen
- The app will navigate to the [Select Lot Screen](./Screens/Select_Lot_Screen.md)

If the selected Order Release's Part is serial-tracked an no serials have been selected
- The app will navigate to the [Select Serials Screen](./Screens/Select_Serials_Screen.md)

Otherwise
- The app will navigate to the [Pack Screen](./Screens/Pack_Screen.md)

