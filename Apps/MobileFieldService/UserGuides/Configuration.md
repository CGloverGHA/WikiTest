---
title: Configuration
description: 
published: true
date: 2024-01-26T15:32:44.152Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:15:30.053Z
---

[Back To Contents](.)

# <div id="test"> Configuration </div>
The following narrative provides details on the various parameters that can be set prior to use of the Mobile Field Service application.



## Parameters
These parameters are set in Epicor. Navigate to GHA Modifications>Parameters>Setup>Parameter Maintenance. On this setup page select using GHA Parameters> Integrations Tab> Mobile Field Service Tab as shown below.

The parameters are split into two tabs, one for the default settings for Service calls and the mobile device, the second for default settings for the back office. Each of the parameters used in the Mobile Field Service configuration are created as User Codes in Epicor.

### Service Calls & Mobile Device Default Settings

![mfs_1.png](/mfsassets/mfs_1.png)

- The Company Code (<span style="color:blue">1</span>) is the Licence Key for the company’s Mobile Field Service, this can be found by logging in to the license portal @ www.ghasolutions.co.uk/mobileapps
- UD Codes (<span style="color:blue">2</span>), this is the name of the US codes that will be used to store the information for MFS
- Mileage Part (<span style="color:blue">3</span>) - this is the default part number for any mileage to be recorded that will be created against a service job during processing in MFS
	- The default rate to be used is set in the rate field 
	- As this is an Epicor Part standard Price List functionality applies
	- This part has to be non-quantity bearing with a primary bin set up for each vehicle
- Travel part (<span style="color:blue">4</span>) - this is the default part number for any travel time to be recorded that will be created against a service job during processing in default rate to be used is set in the rate field 
	- As this is an Epicor Part standard Price List functionality applies
	- This part has to be non-quantity bearing with a primary bin set up for each vehicle
- Expense Part (<span style="color:blue">5</span>) - this is the default part number for any expenses to be recorded that will be created against a service job during processing in MFS
	- This part has to be non-quantity bearing with a primary bin set up for each vehicle
- Job Pause (<span style="color:blue">6</span>) – this will search for a set of user codes, that will list the options the technician will be able to select from as reason types for pausing a job in MFS e.g., accident, breakdown, traffic
- Travel Pause (<span style="color:blue">7</span>) - this will search for a set of user codes, that will list the options the technician will be able to select from as reason types travel time in MFS e.g., traffic, comfort break
- Job Skip (<span style="color:blue">8</span>)  - this will search for a set of user codes, that will list the options the technician will be able to select from as reason types for pausing travel time in MFS
- Stock Adjust (<span style="color:blue">9</span>) – This will search for an Inventory adjustment reason code that is marked as a Count Discrepancy Reason
- Labour Rates (<span style="color:blue">10</span>)  – this will search for a set of user codes, that can hold various labour rates for the back office staff to pick for each call
- MFS Status (<span style="color:blue">11</span>)  – This will search for Parent Child UD table for recording any difficulties in communicating with Epicor
- MFS Log (<span style="color:blue">12</span>) – This will search for a single level UD table to record the status of data being sent to the MFS database
- Fixed Cost Part (<span style="color:blue">13</span>) – This will search for a non qty bearing part to be used in jobs where there is a fixed cost
	- This part has to be non-quantity bearing with a primary bin set up for each vehicle
- Test Environment (<span style="color:blue">16</span>) – This should be selected if the environment is not a live environment
- Hide Costs Page (<span style="color:blue">17</span>) – This is a global setting, which can be overwritten at a customer level, and when selected while hide the costs from the costs page of the app.
- Burden Settings (<span style="color:blue">18</span>) – Specifies how you want Epicor to handle the burden, the options are 
	- Burden = Labour
	- Burden = 0
	- Epicor uses standard functionality to set the Burden
- Default Time Entry method (<span style="color:blue">19</span>)– there are 3 options
	- Record time
	- Enter time
	- Fixed cost
- Default Travel Time Entry method (<span style="color:blue">20</span>) – there are 3 options
	- Record time
	- Enter time
	- Fixed cost
- Default Time Travel Cap (<span style="color:blue">21</span>) – this is the default value to cap the travel time on a service call
- Default Mileage Cap (<span style="color:blue">22</span>) – this is the default value to cap the mileage for each service call
- Default min Labour Period (<span style="color:blue">23</span>)  - this is the default minimum time period that will be charged to the customer
- Default Labour Increment (<span style="color:blue">24</span>) – if time increments are to be set or required, set the default value i.e., the value is 10, then following the Default Min Labour Period value being passed, each time increment will increase by the value here
> For example, if the Default Min Labour Period = 60 minutes and the Default labour increment is set to 10 and the technician spends 65 mins on a job task, then 70 minutes will be captured.
- Default Min Travel Time (<span style="color:blue">25</span>) - this is the default minimum travel time that will be charged to the customer
- Default Travel Time Increment (<span style="color:blue">26</span>) – if travel time increments are to be set or required, set the default value i.e., the value is 15, then following the Default Min Travel Time value being passed, each time increment will increase by the value here
> For example, if the Default Min Travel Time = 60 minutes and the Default Travel Time increment is set to 15 and the technician spends 65 mins on travel, then 75 minutes will be captured.
- Job Display settings (<span style="color:blue">14</span>) & (<span style="color:blue">15</span>) fields will control how many day(s) of scheduled work will be displayed to the technician on their job window in MFS e.g., days before 1 and days after 3 means the technician will see today’s jobs and 3 days after.
- Group Jobs by (<span style="color:blue"></span>),will determine how the jobs are displayed on the mobile device, the jobs can be grouped to make viewing easier, there are four options
	- Days
	- Weeks
	- Months
 	- Years
	- None
 
 - Start of Week(<span style="color:blue"></span>),will determine how the jobs are grouped into weeks, if selected.
- Image Settings (<span style="color:blue">29</span>) – Image size settings for pictures taken with the mobile application  
- Close Call Job on Approval (<span style="color:blue">27</span>) – if selected the service call and job will be closed ready for invoicing when the technician finishes the call
- Show Zero Stock Items (<span style="color:blue">28</span>) - If selected parts with zero stock will show on the technicians tablet

  
  ### Back Office Default Settings
  
![mfs_2.png](/mfsassets/mfs_2.png)
  
- Employee Filter (<span style="color:blue">1</span>) this is for filtering the list of technicians on the scheduling page – there are 3 options
	- Resource Group
	- Department
	- Shift
  
 # Expense Types
The expense options are set in the Purchasing Miscellaneous charge screen, all charges where the MFS expense option (<span style="color:blue">1</span>) is selected will be available on the app. This is found in GHA Modifications>GHA Mobile Field Service>Miscellaneous Charges
![mfs_3.png](/mfsassets/mfs_3.png)

# Warehouses
To select a warehouse go to GHA Modifications>GHA Mobile Field Service>Warehouse. Click the Warehouse button (<span style="color:blue">1</span>) to search for the warehouse you want to edit.
![mfs_4.png](/mfsassets/mfs_4.png)

- Mobile Warehouse (<span style="color:blue">1</span>) – When selected, this warehouse will be able to be selected as a vehicle in the mobile application and the stock will be visible

- Non Nettable Warehouse (<span style="color:blue">2</span>) – GHA suggest that all service vehicles are non-nettable and selecting this will ensure all bins created in this warehouse will be automatically selected as non-nettable
![mfs_5.png](/mfsassets/mfs_5.png)


# Terms
To select Payment Terms got to GHA Modifications>GHA Mobile Field Service>Terms. Click the Code button to search for the relevant entry.
![mfs_6.png](/mfsassets/mfs_6.png)
- Collect Payment (<span style="color:blue">1</span>) – when selected the mobile application will display collect payment on nearly every screen to remind the technician to collect a payment

# Customer
Hide Costs Page (<span style="color:blue">1</span>) – this is the customer level override to hiding the costs from the customer on the mobile device. Go to Customers, click the Customer button to search for relevant customer. Then select the Integrations tab, then GHA tab.
![mfs_7.png](/mfsassets/mfs_7.png)


# Employees
Employees need to be set up in the following manner
- On the Employee Maintenance screen, click ID to search for relevant employee
- The Employee must be selected as a service technician on Employee tab
- The Employee needs to have a department specified on the Production Info tab
- The desired way to link a resource to an Employee is to add the Resource Group, click save and allow Epicor to add the resource. This is on the Production Info tab.
- Password (<span style="color:blue">1</span>) – A password can be set against a technician which will need to be entered into the app upon logging in. Select Integrations tab then GHA tab to set this.
- Restrict Warehouse (<span style="color:blue">2</span>) – If required the technician can be confined to one warehouse by selecting the check box and then selecting the desired vehicle from the combo box (<span style="color:blue">3</span>)
![mfs_8.png](/mfsassets/mfs_8.png)


# Parts
There are two flags to set on the part entry page, navigate to the Integrations > Field Service Tab.

![part_config_11.png](/mfs-2/part_config_11.png)

 - Mobile Part (<span style="color:blue">1</span>) indicates that the part will become part of the vehicle stock.
  - Service Part (<span style="color:blue">1</span>) indicates that the part is servicable in the back office suite.
  
>   For the part to show on the mobile device when there is zero stock on hand, it will need a primary bin in the applicable warehouse.
{.is-info}


[Back To Contents](.)


