---
title: Results_Screen
description: 
published: true
date: 2024-01-17T13:38:20.724Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:36:10.478Z
---

This page will show the locations for the Part Number entered in the [Enquiry Screen](./Enquiry_Screen.md)

# When This Page Is Loaded...
The Part Locations are retrieved from Epicor
- This is done by a REST call to `~/Erp.BO.PartBinSearchSvc/GetFullBinSearch`
	- Where `partNum` is the value of [Part Number](./Enquiry_Screen.md#part-number)
	- **Locations that aren't within the current Site are removed**

# Lot Tracked Parts
Lot Tracked parts will display an additional field `Lot Number`

# Not-Lot Tracked Parts
Parts without a Lot Number will not display the `Lot Number` field