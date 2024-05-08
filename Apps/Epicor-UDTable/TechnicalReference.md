---
title: Technical Reference
description: 
published: true
date: 2024-01-19T15:00:56.007Z
tags: 
editor: markdown
dateCreated: 2023-04-04T13:43:38.994Z
---

# Epicor Ud Table Technical Reference


> If the rebuild fails it may generate errors in Epicor regarding Ice.Data.Model. (This occurred in testing though has been resolved.) The fix is to rebuild and recycle manually
{.is-danger}

## PreRequisites

....Epicor parameters set - write GHA_Misc User codes....

On the GHA's Parameter Screen navigate to the "Misc" section.

Under "Column Maintenance Rebuild" input the time frame when the columns can be rebuilt in the format "HH:MM" 

The automatic table regen will only run during those times unless other checks fail (users online, active tasks, scheduled tasks).

If the time at which the regen will happen doesn't matter the "Rebuild Database Any Time" checkbox can be checked, this will mean that at any point when all other checks pass, the table will regen.

## Process Flow
![flowchartepicortables_(4).png](/flowchartepicortables_(4).png)






## License Portal


The License Portal shows the history of the previous 30 days of requests. These requests are ordered by descending order in terms of the date it was requests. Meaning the top requests are the new ones. 

When adding a new request add the same details as on Epicor. However, the add request pop up contains drop down boxes and automatic filling in of some text boxes to make the process easier and more reliable.

If a request fails then it will be marked as failed and it will show a error message on the table.

On save it will save the information to ERPColumns table in SQL




## App Settings

- Global and customer

There settings for the ERP UD Column maintenance 

Global settings are stored in the SQL dtabase GHALicencePortal int he AppSettings table. The following columns are used - 

| Column Name | Description |
|---|---|
|ERPColumns - RefreshTimeWorker(ms)| The time the service loops before checking the ERP Columns table|
| ERPColumns - ActiveTaskTime | The time frame in which the last activity of an active task is checkedto see if iut is still running |
|ERPColumns - ScheduledTaskTime| The time frame in which an scheduled task is looked for as part of the checks|
|ERPColumns - RegenErrorEmail|Email address errors are sent to|



Customer settings are stored in Epicor and they are set on the Parameter Screen in Epicor. These options are:

> Fill these in
{.is-info}


| Column Name | Description |
|---|---|
|RebuildAny| Tick box to determine if time should be checked or ignored when rebuilding|
|RebuildFrm| If RebuildAny is false, this sets the time from which the rebuild can happen|
|RebuildTo| If RebuildAny is false, this sets the time to which the rebuild can happen|

##  Service

Windows service called running on....

### Schedule

The worker process runs continuously, checking the ERPColumns table at the interval defined in `ERPColumns - RefreshTimeWorker(ms)` for changes.

When a new row is added to the ERP Columns table and detected by the service, for each customer 

- test the epicor connection (each request has a checkbox indicating whether the column should be added to the test ot live environment)

- perform the following checks:
  - We are within the window defined by the customer app settings
  - There are no active sessions logged into Epicor
  - There have been no active tasks on the System Monitor sine the time defined in `ERPColumns - ActiveTaskTime`
  - There are no tasks scheduled for the the amount of time defined in `ERPColumns - CheckScheduledTask`

If any of these checks fail then they are attempted in the next loop

If a request was attempted for more that 3 days and the request has still not been processed then the request is marked as actioned and not successful. 


### Update Epicor

The new columns defined in the licence portal/ERPColumns table are added to the UD Column Maintenance table in Epicor (Ice.ZDataFields).

> If it fails then a message is added to the ERPColumns table for display on the License Portal
{.is-danger}


### Rebuild Epicor Database and Recycle

The Epicor database is rebuilt and the app pool is recycled

> If it fails then an email is sent to that defined in `ERPColumns - RegenErrorEmail`
> {.is-danger}

If all goes well, the Success column of ERPColumns is set to true and displayed on the license portal

