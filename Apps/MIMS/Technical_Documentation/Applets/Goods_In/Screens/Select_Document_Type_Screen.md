---
title: Select_Document_Type_Screen
description: 
published: true
date: 2024-01-17T13:35:34.725Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:26:49.117Z
---

This screen is used to select between the retrieved PO and RMA, if both were returned from Epicor

# Flow
```mermaid
flowchart

A[Select Document Type Screen]
B[Select PO Line Screen]
C[Select RMA Line Screen]

A --> B
A --> C
```

# Controls
## Purchase Order
This control is used to display the retrieved Purchase Order

### When This Button Is Tapped
The app will navigate to the [Select PO Line Screen](./Select_PO_Line_Screen.md)

## RMA
This control is used to display the retrieved RMA

### When This Button Is Tapped
The app will navigate to the [Select RMA Line Screen](./Select_RMA_Line_Screen.md)