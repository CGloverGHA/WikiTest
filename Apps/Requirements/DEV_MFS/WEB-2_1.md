---
title: Technician Areas
description: Technician Areas
published: true
date: 2024-02-23T14:19:02.496Z
tags: 
editor: markdown
dateCreated: 2023-09-25T10:51:44.233Z
---

# Requirements Template

> **Requirement Specification**
> Date: 01/01/23
> Prepared By: Peter Roden
> Prepared for: Internal Development
{.is-info}

## Business Requirements

> **Why** are we making the change?
> Technician Areas is to allow the easier scheduling of technicians by asssigning them an area
{.is-info}

<br/>

## Functional Requirements

### Technician Areas Set Up
A new area is required on the settings page to enter, maintain and delete technician areas.
(See Balsmaiq)
The technician Area will be an ID and a Description, with no logic required for any geographical data.

### Customer Config
A new page is required to enter, maintain and delete technician areas associated with the customer and customer Site.
(See Balsmaiq)

The Area can be designated at customer or site leve, site will have priority in the hierarchy.

> Adding, editing and deleting other customer information is out of scope at this time
{.is-warning}

### Technician Config
A new page is required to enter, maintain and delte technician areas associated with the  technicians.
A technician can be in multiple areas and multiple technicians can be in the same areas.
(See Balsmaiq)

A technician will be able to be added to an area temporarily with an expiry date, for technicians covering holidays etc.

The expiry date will be inclusive and the row will be removed once the date has expired

> Adding, editing and deleting other technician information is out of scope at this time
{.is-warning}

### Expected Logic

#### Scheduling
When the user selects a job on the scheduling board, the calendar row for the technicians who are not in the same area will be removed.

#### Editing Areas
If the user want to delete an area that is currently against a customer, then a warning should display, along the lines off. This Area is currently in use, and cannot be removed.

#### Where Used
the user should be able to see which customers have this area assigned to them, so a where used list is required, this can either be dynamic once an area has been highlighted or a recall button to populate the list. 





### Process Flow and Details
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


## Technicial Requirements

> Not finished - need to determine Epicor link
{.is-danger}


### Database

Add **Area** Table (AreaCode, AreaDescription)

Add **AreaID** field to Technician table
Add **AreaID** field to Site table

<br/>

### API

Change DataImport Service to import Area table
Change DataImport Service to import Area field against Technician
Change DataImport Service to import Area field against Site (Customer?)

Technician/Get - read technician record
Technician/Update - update technician Area field *only*
Customer/Update - read Customer record
Customer/Update - update customer Area field *only*

<br/>

### Front End

Areas section on global settings
Customer page
Technician page

<br/>

### Services

Add new import for Area
Add Area to customer and technician import

<br/>

### Epicor

> Do we update Epicor or even store this information in Epicor?
> How does the sync work? One way? Two way?
> Would we use Sales Regions in Epicor as a basis for service areas? Customers may want to. Or do we just allow an open ended import for the customer to decide with respect to field service?
{.is-warning}

