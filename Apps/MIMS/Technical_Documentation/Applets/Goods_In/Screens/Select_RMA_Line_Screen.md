---
title: Select_RMA_Line_Screen
description: 
published: true
date: 2024-01-17T13:35:46.790Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:27:29.055Z
---

This screen is used to select a line from the selected RMA

# Flow
See [Selection Flow](../Navigation.md#selection-flow)

# When This Page Is Loaded
If the number of valid releases is less than `0`
- The app will navigate to the [Goods In Entry Screen](./Goods_In_Entry_Screen.md)

# Controls
## RMA Lines
This control is used to display the lines of the selected RMA

### When A RMA Line Is Tapped
The following properties are removed from [Application Storage](../../../Application_Storage.md)
- `SelectedLotNum`
- `SelectedSerials`
- `SelectedPartBin`

The [Flow](#flow) is followed