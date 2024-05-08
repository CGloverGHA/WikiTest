---
title: Create Call
description: Create Call
published: true
date: 2024-01-17T13:29:15.827Z
tags: 
editor: markdown
dateCreated: 2023-09-14T14:45:27.618Z
---

# Requirements

> **Requirement Specification**
> Date: 01/01/23
> Prepared By: Peter Roden
> Prepared for: Internal Development
{.is-info}

## Business Requirements

> **Why** are we making the change?
> This part of the ongoing MFS development
{.is-info}

<br/>

## Functional Requirements

### Preamble
<br/>
The sequence of events in handling a customer query is as follows:
  
- A call is taken fom a customer 
- Call details are entered
- If the call can be resolved over the phone/email then the resolution is entered and the call closed
- If a site visit is required then a job is raised to be scheduled as normal
- If a further visit is required then a new call needs to be created

<br/>

### 1 Call List Page
A new page is required which will list all the calls, this will need to be limited to the last x amount, as this will soon become unmanageble, suggest the last 1000, with an option to load the next 1000, and so on

The following columns will be displayed:

&nbsp;&nbsp;&nbsp;&nbsp;Customer, Call number, Part Number, Serial Number, Call Summary, Job number, Call/Job Status, Technician, Call received date

The calls will be filtered by:

&nbsp;&nbsp;&nbsp;&nbsp;Customer, Call number, Serial number, Job num, Technician, Status, Released.

The user will be able to release the job from this page.

> we will use the released flag as both engineered and released, as engineered serves no purpose to us.
{.is-info}

An option to jump from this list to the highlighted call is required
<br/>

### 2 New Call Page
The new call page will act as our version of case entry and call entry, the independant sections will be able to be turned on and off as per previously demonstrated. the user prefefences for which sections are on or off can be saved.

When this page is launched the call page will be empty (unless it is opened from the call list page)

Entering a call number will recall the details of that call or selecting the plus button will be created, this action can be cancelled by selecting cancel, which will remove the call number.

The date and time the call was created will be stored and displayed as well as the duration the call has been open.


#### 2.1 Customer Details Panel
The customer details panel will hold all the details of the customer that has instigated the call, the customer can be searched by the same method as AQS, or by entering the serial number (ever decreasing list) like the Versalift search.

>The four optional UD field searches are out of scope for this phase
{.is-warning}

#### 2.2 New Site Details Panel
The site details panel will allow the selection or creation of a new site. If a new site is to be created, it will be able to be entered directly into the form with no need for additional pop-ups.

A new contact will be able to be created which will be stored back against the customer, also without the need for any additional pop ups.

The save as option will give two options, save as new site or dont save.

If a new Site is created, and the customer has the advanced module, the Area field will need to be populated

#### 2.2 Service Contract Details Panel
>This is out of scope for this phase, however, the rectangle with the header should be displayed.
{.is-warning}

#### 2.3 Call Details Detail Panel
The call details will be pre populated if a serial number was entered in the customer details panel.
The user will be able to search for a serial number at this point as well, to return the part. 
A check will need to be performed to enure the serial number is linked to the correct customer.
>An option to update the serial number record with the correct details is out of scope for this phase
{.is-warning}

The user will be able to search for a part number, which will return the desctiption, if the part is serialised the serial number search will automatically appear.

The Parts Covered / Labour Covered will show if there is no GHA service contract for this part
>The warranty details and installation date is out of scope for this phase, however the text should remain and greyed out.
{.is-warning}

The issue should be recorded in the relevant field, if the user taking the call can resolve the issue, the resolution can be entered in the resolution field and the issue reolved button can be selected which will close the call with the status resolved no visit.

#### 2.4 Original BOM

This panel is to show the original BOM of th epart being serviced, along with history of the parts that have been swapped out.

>This is out of scope for this phase
{.is-warning}

#### 2.4 Site/Equipment Information	
The user will be able to enter any relevant notes in here for accessing the site, for example gate key codes, cherry picker required.

Future functionality on the tablet will display this.

#### 2.5 Site/Equipment availability
This will allow the user to record when the site/equipment is available, this will dispaly in the scheduling view.

> the scheduling view part of this is out of scope of this phase
{.is-warning}

#### 2.6 Call History

When the part has been selected the call history will display, this will mimic the call history on the tablet, complete with a date and keyword search,

#### 2.7 Site/Equipment availability
the user will be able to record when the site/equipment can be accessed, this will then show in the scheduling calendar and on the call details on the tablet.

>Entering this information should be available in this phase, but adding to the table and scheduler is not in scope
{.is-warning}

#### 2.8 Job Details
The user will entrer the call type (Service call header in Epicor) and the Issue type (Topic 1 in Epicor)
> We are only supporting 1 topic
{.is-info}

> The Tech type is going to be linked to our Technician Skills, this field should be visible with the label but not active as it is not in scope
{.is-warning}

The get details search will allow the user to search for a template service job to return the details

>Assigned template jobs to parts is out of scope for this phase
{.is-warning}

##### Job Tasks

The User will be able to add tasks by selecting add, where a pop up window will display all available tasks, a filter (just like the engineering section in Eicor) will reduce the list by ID or description.


Using ctrl or shift functionality, the tasks will be able to be dragged in

The tasks can be edited on the screen directly

The duration of the task will have three possible UOM's Minutes, Hours or Days. All tasks will be created in epicor as fixed time.

The tasks will be able to be deleted in the screen by highlighting the task (clicking on it) and hitting delete on the keyboard.

A slider will denote if the task is billable or not

The Operations should indicate if they have been completed

Each task has a skill, defaulted to the techncian type for the job details but can be altered for that specific task.

> Future functionality will allow the user to set different rates for different tasks
{.is-warning}

##### Job Materials

this will follow the same principles as operations

> Future functionality will allow the user to edit the material cost for different materials
{.is-warning}

The user will be able to select engineered / released and the date the customer would like the call ready for the scheduling.

Selecting "Create Job" will create the job
<span style="color:blue">PR - will have a save button fixed at the top of the screen. Possibility of auto save?<br/>
How will we update Epicor? Do not want to do this until the job has been completed. Should we update Epicor on release?
</span>

#### 2.8 Job Options

This will display the same options as per the Epicor page, this section will become read only once the job has been created.

#### 2.9 Call Progess

This will show the cumlative call costs, with totals, this will have to be configurable by user as not all customers will want everyone to see the costs.
>This is out of scope for this phase
{.is-warning}


## Technical Requirements

### Database

The following tables need to be added to the database:

| Table | Notes |
|---|---|
| Call | Main call table |
| CallType | Corresponding to Call type in Epicor |
| Issues | Corresponding to Topics in Epicor |
| Skills | Employee skills |
| JobTechnicians | Link to the technicians assigned to the job task (future functionality, allows multiple technicians) |
| EquipmentAvailability | Future functionality |

Extra fields need to be added to the following tables:

| Table | Notes |
|---|---|
| Job | Link to issues and skills |
| JobTask | Skills and UOM |

### API

Documented [here](/https://dev01.ghahosted.com/MobilePortalMoq/FieldServiceWeb/swagger/index.html) 

#### Page Layouts

There will be global Page setup which will turn on and off for all users. The user will also to be able to save their own preferences on top. The API will handle all this, the page layout can be handled per user by the following calls

The user ID etc will form part of the token so is not required by the REST request

**/Page/PageGet**
  
**/Page/PageUpdate**

**/Page/PageUserGet**

**/Page/PageUserUpdate**

<br/>

#### 1 Call List Page

**/Call/CallListFilters**

**/Call/Calls - gets the list of calls**

**/Call/JobRelease**

**/Call/Call**

<br/>

#### 2 New Call Page

**/Call/NewCallFilters**

**/Call/CallDefaults**

**/Call/SerialNumber**

**/Call/Customer**

**/Call/Site**

**/Call/Countries**

**/Call/Update**

**/Call/Tasks**

**/Call/Materials**

<br/>

#### 3 Settings page

**/Settings/Update**

<br/>

### Epicor Link

#### Epicor to Field Service

Add data import and directives to add:

- Service call types
- Topics

#### Epicor to Field Service

Add messages for the following actions

- Add call
- Create job
- Amend call
- Amend job
- Engineer and release job

The following need to be saved to Epicor

Topic/Issue link
Add call and job to Epicor
- How do we prevent an infinite loop as the job is updated?
- Do we need to get the costs from Epicor as we do on the tablet? What about when Epicor is not used?

<br/>

### Web front end

See balsamiq

- Will need to scroll down to see the job. Have save/cancel buttons fixed at the top.

- The New Contact and New Site buttons are not required as new contacts and sites can be added via the /Update API endpoint (see swagger doc)

- In Job options, when fixed costs are ticked Time Entry Methods defaults to 'Fixed Costs' and the all controls are disabled apart from the time and labour entry costs

<br/>


![dev_mfs_web-1_2_calls.png](/mfsassets/dev_mfs_web-1_2_calls.png)
![dev_mfs_web-1_2_call.png](/mfsassets/dev_mfs_web-1_2_call.png)





