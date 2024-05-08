---
title: Login_Screen
description: 
published: true
date: 2024-01-17T13:32:43.093Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:15:55.510Z
---

After registration, this is the default screen the app will open to.

# When The Page Is Loaded...
When this page is loaded, the customer's ERP connection is retrieved via the License Portal API
* Dev example: `https:\\dev01.ghahosted.com\ghalicenseportal\api\ERP`
* Live example: `https:\\mobileapps.ghahosted.com\licenseportal\api\ERP`

This connection is then tested via a rest call to `Erp.BO.CompanySvc\List`

If retrieving the ERP connection or the test is unsuccessful, an error message will be displayed to the user

Next, the app will retrieve the list of employees by calling `BaqSvc\GHA_MIMS_Employees`
- Refer to [GHA_MIMS_Employees](../Epicor/BAQs/GHA_MIMS_Employees.md) for further information about this BAQ

If the employees are successfully retrieved, they are then saved to the [Local Database](../Local_Database.md)

The [Employee ID](#employee-id) field will be set to the value of [Last Employee](../Local_Database.md#last-employee) if it is valid, otherwise it will be set to empty

The [Site](#site) field will be set to the value of [Plant](../Local_Database.md#plant) if it is valid, otherwise it will be set to empty

# Controls
## Employee ID
This form control allows the user to select from a list of Employee IDs retrieved from Epicor

### When An Employee Is Chosen...
A call to `Erp.BO.EmpBasicSvc\EmpBasics(Company, EmpID)` is made where `Company` is the current company and `EmpID` is the chosen [Employee ID](#employee-id)

This is done to retrieve the [EmpBasic.GHA_Plants_c](../Epicor/User_Fields/EmpBasic/GHA_Plants_c.md) User Field

Then for each of these sites, a call to `Erp.BO.PlantSvc\Plants` is made to retrieve the:
- `SiteId`
- `SiteName`

If the [EmpBasic.GHA_Plants_c](../Epicor/User_Fields/EmpBasic/GHA_Plants_c.md) field is empty or doesn't exist, the default site `MfgSys` is returned

This data is then used to update the [Site](#site) control with the list of sites

## Site
This control allows the user to select from a list of Sites that the selected employee can access

## PIN
This control allows the user to enter the PIN for the currently selected Employee

The user may enter a value in this field, even if the selected Employee does not have a PIN
- The entered PIN will be ignored in this case

If the Employee does have a PIN, it will be validated when the [Login](#login) button is tapped

## Login
This control logs the User into MIMS once tapped

## When This Button Is Tapped...
The selected [Employee](#employee-id) is retrieved from the [Employees](../Local_Database.md#employees) and the [PIN](#pin) is validated:
- If the employee does not have a PIN, validation is successful
- If the PINs do not match, validation is unsuccessful

On unsuccessful validation:
- A message is displayed to the user

On successful validation:
- The selected [Employee ID](#employee-id) is saved to [Last Employee](../Local_Database.md#last-employee)
- The selected [Site](#site) is saved to [Plant](../Local_Database.md#plant)
- The app navigates to the [Home Page](./Home_Page.md)