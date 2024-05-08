---
title: mims-technical-documentation-logging-in
description: 
published: true
date: 2024-01-17T13:31:06.796Z
tags: 
editor: markdown
dateCreated: 2023-10-06T14:17:37.332Z
---

When the Login Page is loaded, a REST call is made to `/BaqSvc/GHA_MIMS_Employees`. This executes the [`GHA_MIMS_Employees`](mims-technical-documentation-epicor-baq-GHA_MIMS_Employees.md) BAQ.

When the user selects an employee, a REST call is made to `/Erp.BO.EmpBasicSvc/EmpBasics` with the following parameters:
```json
{
	// {Company} is the company as defined in the License Portal
	// {EmpID} is the ID of the selected Employee
	"$filter": "Company eq '{Company}' and EmpID eq '{EmpID}'"
}
```

The resulting `EmpBasic.GHAPlants_c` field is read to retrieve the Employee's sites.

Then a REST call is made to `Erp.BO.PlantSvc/Plants` with the following parameters:
```json
{
	"$select": "Plant1, Name",
	// {Company} is the company as defined in the License Portal
	// {PlantFilter} is the value of GHAPlants_c in the format
	// Plant1 = 'plant' or Plant1 = 'plant2'...
	"$filter": "Company eq '{Company}' and ({PlantFilter})",
	"$orderby": "Name",
}
```

If no data is returned from either REST call, a default site will be returned
- `SiteId = 'MfgSys'`
- `SiteName = 'Main'`

When the User logins in, the app will validate the PIN against the `EmpBasic.GHA_PIN_c` field. If it matches, the main menu page is shown. Otherwise a relevant message is shown.