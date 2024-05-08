---
title: Technician Skills
description: Technician Skills
published: true
date: 2024-02-23T14:16:32.310Z
tags: 
editor: markdown
dateCreated: 2023-09-28T12:37:59.194Z
---

# Technician Skills

> **Requirement Specification**
> Date: 28/09/2023
> Prepared By: Peter Roden
> Prepared for: Internal Development
{.is-info}

## Business Requirements

> **Why** are we making the change?
> This is part of the ongoing MFS development, and is designed to allow the scheduling of technicians with the correct skills to a service call
{.is-info}

<br/>

## Functional Requirements

### Creating Technician Skills
A new section of the settings page will be required where the user can enter, maintain and delete the skills
(See Balsamiq)
The Skils will have an ID and a Description

### Assigning Skills to a Service Call
A template job, currently residing in Epicor will need to have a UD field for storing the Skill.

> Currently we will only hallow one skill per job
{.is-info}


> When we get onto multiple technicians on one job we will need to be able to set skills at an operational level
{.is-warning}

When a call is created, if a template job is used, the required skill will be displayed, and will be able to be changed. If there is no template job, the user will need to set the Skill required, however it will not be mandatory.

### Expected Logic
when the user selects a job, the tooltip will show the skill that is required, the list of available technicians will be reduced to show only the technicians with the required skills.

If the user tries to delete a skill from the settings that is currently stored against a live job, or template job, a message should display, stating' This skill is in use on Template and live jobs, removing this record may result in an unsuitable technician being deployed, are you sure?'

if the user selects Ok to Proceed, then we ned to record the logged in user, time and date.

### Where Used
On the settings page, the user will be able to see a list of what template jobs use the selected skill.



> We can add a call/job in Epicor and it flows through to MFS. 
> What about when we add a call/job via MFS? Are we allowing skills here as well? 
> We will need to keep skills in sync between MFS and Epicor
> Multiple skills? Against technician? Against job?
{.is-danger}


## Technicial Requirements

> Need to determine the Epicor sync process before can complete this section
{.is-warning}

### Database

Skill table
Technicial skill table
Job skill table (if multiple)


<br/>

### API



<br/>

### Front End
<br/>

### Services
<br/>

### Epicor

Utilise a UD table for skills
Utilise a UD table for job/operation skills
Utilise a UD table for employee skills
(parameter screen change)

Custom technician and job (service call?) form

Imports and data directives as usual








