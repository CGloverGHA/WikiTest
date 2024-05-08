---
title: 1.4 Create & Edit Labour Rates
description: 1.4 Create & Edit Labour Rates
published: true
date: 2024-01-18T11:17:03.919Z
tags: 
editor: markdown
dateCreated: 2023-09-21T16:26:46.380Z
---

# Create & Edit Labour Rates


> **Requirement Specification**
> Date: 01/01/23
> Prepared By: Peter Roden
> Prepared for: Internal Development
{.is-info}

## Business Requirements

> **Why** are we making the change?
> Part of the Ongoing MFS development
{.is-info}

<br/>

## Functional Requirements

> **What** is the change?
> This is filled in by the business analyst for the project
{.is-info}

### Labour Rates

Labour rates will work differently depending on if service contracts are in use.
the logic for when serice contracts are in use will be covered under the service contract section

#### Operation Upload from Epicor
When the operation is uplaoded from Epicor, the following additinal fields are required
- Estimated Time
- Hourly Rate
- Operation Type

#### Adding an Operation to the Web page
when the add task option is selected a screen similar to the below will appear:
![adding_a_task.jpg](/adding_a_task.jpg)

The ID (1), is only 8 characters and the description (2) is a maximum of 30.

The Rate (3) will be copied in from the operation and will be editable in this screeen
The Labour time will display in Hours (4) and Minutes (5), rounded up to the nearest 15 minutes, this will also come from the operation and can be edited in this screen, using the same controls as on the web page.

The billable flag (6) will set to true by default unless any of the following are true.
- The part being serviced is flagged as labour covered
- The default job type is not fixed cost labour

![web_display_1.jpg](/web_display_1.jpg)

The Hours (1) and minutes (2) will display, the rate (3) will display and can be edited, the value (4) will be the rate x hours, this will not be editable.

If the job is fixed cost labour the value will show zero and be flagged as non billable.

#### Web Page Display

The web page will display similar to the below



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
