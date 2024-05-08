---
title: Home_Page
description: 
published: true
date: 2024-01-17T13:32:40.541Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:15:52.045Z
---

The Home Page acts as the main navigation hub for navigating to each of the Applets

# Applets
[Stock Take](./Stocktake/Stocktake.md)
[Bin Enquiry](./Bin_Enquiry/Bin_Enquiry.md)
[Part Enquiry](./Part_Enquiry/Part_Enquiry.md)
[Add & Issue Parts](./Add_%26_Issue_Parts/Add_%26_Issue_Parts.md)
[Move Stock](./Move_Stock/Move_Stock.md)
[Job Picking](./Job_Picking/Job_Picking.md)
[Job Returns](./Job_Returns/Job_Returns.md)
[Job Receipts](./Job_Receipts/Job_Receipts.md)
[Order Picking](./Order_Picking/Order_Picking.md)
[Tracking Number](./Tracking_Number/Tracking_Number.md)
[Reprint Labels](./Reprint_Labels/Reprint_Labels.md)
[Goods In](./Goods_In/Goods_In.md)
[NCRs](./NCRs/NCRs.md)
[Kanban Receipts](./Kanban_Receipts/Kanban_Receipts.md)

# When The Page Is Loaded...
The app will retrieve the [MIMS Parameters](../MIMS_Parameters.md)
- This is done by a REST call to `~\BaqSvc\GHA_MIMS_Parameters`
- See [GHA_MIMS_Parameters](../Epicor/BAQs/GHA_MIMS_Parameters.md) & [MIMS Parameters](../MIMS_Parameters.md) for more information

Then the app will retrieve details about the current Epicor installation
- The Advanced Material Management (AMM) license status is retrieved
	- This is done via a REST call to `~\Erp.BO.CompanySvc\JCSysts`
	- Refer to [AMM Handling](../AMM_Handling.md) for information on how this affects MIMS
- The status of `JCSyst.PreventPJChange` is retrieved
	- This is done via a REST call to `~\Erp.BO.CompanyLicenseInfoSvc\GetLicense`
	- Refer to [Prevent JP Changes] for information on how this affects MIMS


Then the app will retrieve the applets that that the given employee can use
- This is based on the **roles** that are assigned to the employee 
- Refer to [MIMS Applets Per Employee Role](../MIMS_Applets_Per_Employee_Role.md) for further information about employee roles


Then the app will apply the [User Preferences](../User_Preferences.md) to the applets
- This includes the order of the Applets


Then licensing is applied to the applets
- **As of 2022-12-15, all applets are licensed by default**


# Drag And Drop
This page implements drag and drop functionality for the applet buttons to change the order in which they appear

When the user drops the applet in a new position, the relevant order property of each applet is adjusted

The new layout is then saved via a REST call to `~/Erp.BO.EmpBasicSvc/EmpBasics(Company, EmpID)`
- Where `Company` is the current Company of the Epicor Connection
- Where `EmpID` is the logged in Employee ID

The new layout is also saved to the [Local Database](../Local_Database.md#mims-layout)


# Navigation
When an Applet is tapped, the app will navigate to the relevant applet to begin the relevant workflow

## Order Picking
When the tapped Applet is Order Picking:
- Application data pertaining to Order Picking is removed
- If the [Push](../MIMS_Parameters.md#dashboard-driven-picking) parameter is `True`, then it will navigate to the [Select Order Release Screen](./Order_Picking/Screens/Select_Order_Release_Screen.md)
	- Otherwise it will navigate to the [Select Order Type Screen](./Order_Picking/Screens/Select_Order_Type_Screen.md)

## Goods In
When the tapped Applet is Goods In:
- Application data pertaining to Goods In is removed