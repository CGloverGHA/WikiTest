---
title: Select_PO_Line_Screen
description: 
published: true
date: 2024-01-17T13:35:39.476Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:27:04.735Z
---

This screen is used to select a line from the selected Purchase Order

# Flow
See [Selection Flow](../Navigation.md#selection-flow)

# When This Page Is Loaded
If the number of valid releases is less than `0`
- The app will navigate to the [Home Page](../../Home_Page.md)

# Controls
## PO Lines
This control is used to display the lines of the selected Purchase Order

### When A PO Line Is Tapped
The following properties are removed from [Application Storage](../../../Application_Storage.md)
- `SelectedLotNum`
- `SelectedSerials`
- `SelectedPartBin`

The [Flow](#flow) is followed