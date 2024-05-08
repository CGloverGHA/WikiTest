---
title: Concurrent Licenses
description: 
published: true
date: 2024-01-17T13:29:12.941Z
tags: 
editor: markdown
dateCreated: 2023-04-21T18:53:35.159Z
---

# Concurrent Licensing

> **Requirement Specification**
> Date: 21/04/23
> Prepared By: Andy Wilson
> Prepared for: Internal Development
{.is-info}

## Business Requirements

In order to maximise software value over split shifts, job shares and different time zones, a concurrent licensing model is required.

The customer can have as many users registered for the application as they require, however, only the licensed qty can be active at any one time. The customer should be able to set the time out window in the settings, we should impose a minimum and maximum time, for example a minimum of five minutes and a maximum of 60

What we need to avoid is the customer having to wait for one of the other users to be timed out, they need a mechanism for logging out a user if required.

The server needs to record how many times a license was not available, this needs to be recorded as a date/time, this data will be stored on a rolling sixty days.



<br/>

## Functional Requirements
Once a user logs in the user experience should be seamless, and not keep having to log back in. After a period of inactivity, the license will become available to others. 


If the user comes back after the license has become available and there are no available licenses, an informational message should display 'No available licenses, please contact IT' 



### Process Flow and Details
![concurrent_license_flow.png](/ProcedureHome/concurrent_license_flow.png)
<br/>

### Business Rules and Data Requirements
<br/>

### Interfaces to External Systems
<br/>

### Security
<br/>

### Audit Trail
<br/>

> Anything out of spec should be shown as a warning
{.is-warning}


## Technical Requirements

> **How** are the changes implemented?
> This is fllled by the developer and discusses the changes made, design patterns and decisions
{.is-info}

### Database
<br/>

### API
<br/>

### Front End
<br/>

#### Web Pages
<br/>

#### Mobile App Pages
<br/>

### Services
<br/>

### Epicor
