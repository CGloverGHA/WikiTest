---
title: MFS Release Notes
description: 
published: true
date: 2024-01-19T15:02:03.378Z
tags: 
editor: markdown
dateCreated: 2023-04-12T06:23:35.089Z
---

- ## Change Log

<br/>

### Epicor Link 20231115.1

> Released 15/11/2023
{.is-success}

- The data from Epicor used the hostmane/instance from the connection strings to ascertain whether it should go to the live or test database. Changed to exclusivel use the Epicor parameter screen setting

<br/>

### Application API20231013.1

> Released 13/10/2023
{.is-success}

- Fixed issue where a test device no longer connected to the test database

<br/>

### Application API20230929.1

> Released 29/09/2023
{.is-success}

- Only allow technicians to log in on one device
- Enable concurrent licensing (as an alternative to currently implemented named licensing)

<br/>

### Application API 20230523.1

> Released 23/05/2023
{.is-success}

- Added device checks for grouping the job list on the home screen by none, day, week, month or year. Set on the GHA parameter screen in Epicor.

- Maintenance jobs

<br/>

### Application API Version 1.3.013 Release 5

> Released 12/04/2023
{.is-success}

- Record app version against device on the license portal

<br/>

### Application API Version 1.3.012 Release 4

> Released 12/04/2023
{.is-success}

- ***Bug fix*** - The job history list showed the history for all parts across all customers, changed so it only shows the parts installed on the customer site referred to by the current job
- ***Bug fix*** The job time/labour time was not calculated correctly if the job was paused or skipped

