---
title: GHA_MIMS_JobMaterials
description: 
published: true
date: 2024-01-17T13:34:53.118Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:19:05.127Z
---

This BAQ returns additional information about Job Materials for use in [Job Picking](../../Applets/Job_Picking/Job_Picking.md)

This information includes
- The first Warehouse Bin that has on-hand quantity for the material
	- The Warehouse Bin must be marked as a picking location for MIMS
		- This is determined by the user field [GHA_MIMS_PickLoc_c](../../Epicor/User_Fields/Warehse/GHA_MIMS_PickLoc_c.md)
	- The Bin Number, Warehouse Code, Dim Code, Bin Sequence and [GHA_MIMS_SequenceNo_c](../../Epicor/User_Fields/Warehse/GHA_MIMS_SequenceNo_c.md) are retrieved
- Whether the material Part is Quantity Bearing or not