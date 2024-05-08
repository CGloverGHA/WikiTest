---
title: Edit Travel Time & Mileage
description: Edit Travel Time & Mileage
published: true
date: 2024-01-17T13:29:31.135Z
tags: 
editor: markdown
dateCreated: 2023-09-28T14:04:01.116Z
---

# Edit Travel Time & Mileage & Return Mileage

> **Requirement Specification**
> Date: 28/09/23
> Prepared By: Peter Roden
> Prepared for: Internal Development
{.is-info}

## Business Requirements

> **Why** are we making the change?
> This is part of the ongoing MFS development, this solution is to allow the technician to edit the mileage or travel after the event, in case of errors.
>Also actual mileage and travel time neds to be recorded, regardless of billable time and mileage.
{.is-info}

<br/>

## Functional Requirements


See Balsamic for pictures

New partnumbers are required on the parameters screen for return travel and return mileage, these will be used for the retun travel option

Clicking on the Costs panel on the final page will launch a new panel, for editing travel time and mileage.

![edit_travel_-1.jpg](/edit_travel_-1.jpg)


The Time entry method will be displayed at the top, and a slider will toggle between travel to and return travel.

![edit_travel_2.jpg](/edit_travel_2.jpg)

The user will be able to edit the times using a nuumeric keypad, that appears when the edit buttons are pressed.

The original time is to be recorded as well as the change.

### Record Time
For record time the entered time and mileage will be used to calulate the new travel costs


### Enter Time
For enter time the entered time and mileage will be used to calulate the new travel costs

### Fixed Cost
For Fixed costs jobs, the cost will not be updated, just the change recorded

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
