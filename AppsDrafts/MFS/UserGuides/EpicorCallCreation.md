---
title: Epicor Call Creation
description: 
published: true
date: 2024-01-17T13:31:45.291Z
tags: 
editor: markdown
dateCreated: 2023-09-14T12:48:05.391Z
---

[Back To Contents](.)

# <div id="test"> Creating Service Calls </div>

When a call is required for a customer/site, it will be necessary to create a Service Call and associated Service Job in Epicor.  Once the service call and job have been created, these are automatically broadcast to the Mobile Field Service for the technician(s).

## Service Calls
To create a Service Call, either create a case in CRM and create a service call from there, or open the service call screen directly.

![create_servce_call_1.png](/create_servce_call_1.png)
- Assign the customer and the relevant site address as per standard (<span style="color:blue">1</span>) and the ship to if required (<span style="color:blue">2</span>)
- The scheduled date can be entered here (<span style="color:blue">3</span>) if required, it can also be set by scheduling the job against the correct resource, or by using the GHA Back-Office solution *
- Assign the Call Type from the drop-down (<span style="color:blue">4</span>)
- Save
- Select the Line tab
- Select File>New Line

![create_servce_call_2.png](/create_servce_call_2.png)
- Search or enter the part that is to be the subject of the service call e.g., air conditioning unit, burglar alarm, CCTV in the Part field (<span style="color:blue">1</span>)
- If the part is a serial tracked item, search or enter the serial number in the Serial Number field (<span style="color:blue">2</span>)
- Enter a description/narrative in the Description field (<span style="color:blue">3</span>)
- Using the Topic drop down list, select a relevant topic (<span style="color:blue">4</span>)
- The default parameter settings for the company are shown in Job Options (5)These can be changed as required and these will apply for the service call/job only 
- Templates can be identified here to create a call from a template.
- Save.
- Service calls can be assigned to technician at this stage, by scheduling the job in Epicor, or by using the GHA Back-Office solution.
>Note:
Only one line per Service Call is supported by GHA’s Mobile Field Service

![create_servce_call_3.png](/create_servce_call_3.png)
- From the list in the Technicians (<span style="color:blue">1</span>) select the required technician.
- Select Assign (<span style="color:blue">2</span>)  
- The next step is to generate a service call

![create_servce_call_4.png](/create_servce_call_4.png)
- From the menu, select Actions>Create Service Call Job 
- The Service Job Entry will open

[The Call Can Now Be Scheduled](/AppsDrafts/MFS/UserGuides/EpicorCallScheduling)

[Back To Contents](.)





