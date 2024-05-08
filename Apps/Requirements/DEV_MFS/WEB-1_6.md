---
title: User Settings
description: 
published: true
date: 2024-01-17T13:29:23.481Z
tags: 
editor: markdown
dateCreated: 2023-04-05T08:50:53.904Z
---

# Company Settings & User Preferences
> **Requirement Specification**
> Date: 05/04/23
> Prepared By: Peter Roden
> Prepared for: Internal Development
{.is-info}

## Business Requirements

When a user logs into any device/pc to view the mobile field service back office they should be able to view with all their settings

> The company settings and user preferences will be added to during the life of this project
{.is-info}


### User Preferences

The following settings need to be saved on our DB for the logged in user, so any machine they log into will mirror the settings

- Language
	- Default language
- Job Scheduling
  - Map
    - Default map zoom level
    - Map location (left or bottom of screen)
    - Map filter days history to show
    - Map filter days in the future
  - Calendar
    - Default employee rows
    - Job Colours
    	- Started
      - In progress
      - Finished
      - Late
      - On contract
      - Urgent
    - Days history of jobs on the schedule grid
    - Technician filter
    - Job Filter
    
   

### Company Settings

The following settings need to be saved on our DB for the company.


Refer to the Balsamiq Located at
https://ghasolutions.sharepoint.com/:u:/s/Development/ETYSdLqTtFZOsHJzELsC_usB9YhtL9Yn3W8Ih1_5YLQLTA?e=5PzsB7

- Language
  -	Default language
- Licensing
  - Concurrent licensing timeout


- Scheduling Settings
	- Job Colours
  	- Started
  	- In Progress
  	- Finished
  	- Late
  	- On Contract
  	- Urgent
	- Calendar Colours 
  	- Working Day
  	- Overtime
  	- Availability
  	- Vehicle Availability
  - Allow users to change colours
- Call Settings
	- Starting call number
    
## Technical Requirements

### API

For user settings use the endpoints
`/api/FieldServiceWebSvc/Settings/UserSettings` to read 
`/api/FieldServiceWebSvc/Settings/UserSettingsUpdate` to save

For global settings use the endpoints
`/api/FieldServiceWebSvc/Settings/GlobalSettings` to read 
`/api/FieldServiceWebSvc/Settings/GlobalSettingsUpdate` to save

Note the following endpoints will contine to work but will be made obsolete i a future version:
`/api/FieldServiceWebSvc/UserSettings/UserSettings` to read 
`/api/FieldServiceWebSvc/UserSettings/UserSettingsUpdate` to save


The endpoint
`/api/FieldServiceWebSvc/Settings/UserSettings` 
Will display all user and global settings so that all settings can be retrieved by a single rest call. The `GlobalSettings` endpoint is intended to be used for settings page


<br/>


### Web Pages

Torchbearer to implement, see Balsamiq referred to above

