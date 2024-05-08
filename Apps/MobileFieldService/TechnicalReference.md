---
title: Mobile Field Service Technical Documentation
description: 
published: true
date: 2024-02-08T14:05:36.533Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:15:18.726Z
---

# Mobile Field Service Technical Documentation



GHA Mobile Field Service (MFS) has been designed as a stand alone application. However initially it is designed to integrate fully with Epicor.

MFS consists of a mobile application and a back office website. These two application talk to an API layer which then talks to a database where all the data is stored. As this is stand alone all the data for the app and web site to function is stored in this database.

![mfs-intro.png](/Apps/MobileFieldService/techref/mfs-intro.png)

The integration to Epicor is achieved by using a message queue to communicate between the two applications (MFS and Epicor). Any changes made to one application produces a 'message' which is then processed and updates the other application.

![mfs-messagequeue.png](/Apps/MobileFieldService/techref/mfs-messagequeue.png)

The method should enable integration to other ERP/financial systems possible.

Each customer has their own message queue and all transactions are processed synchrnonously, on a FIFO basis. Note that data imports and Vehicle Part syncs are on a separate queue in order not to interfere with normal day to day operations.

### Terminology

The following terminology is used in the Technicial Reference

* MFS App - The mobile application. Available on iOS and android, designed to run on tablets only, not phones. Used by Field Service technicians
* MFS Back Office - The web application which the back office staff to support the mobile technicians.
* MFS Application - The cloud based API layer written by GHA in order for the MFS App, back office and Epicor to communicate with
* MFS Database - A database stored on the cloud which the MFS Application talks to directly
* MFS MQ/Message Queue - the mechanism by which the MFS Application communicates with external application, eg Epicor. 

Epicor update MFS by calling an API which is part of the MFS Application, which interprets the Epicor data and adds it to the MFS MQ for processing

If the MFS Application needs to update Epicor it does so by adding a message to the MFS MQ. The message is then processed to update the appropriate Epicor instance.

> Note any reference to Epicor will be displayed as callout text

# Epicor Link

## Pre-requisites

## Epicor

In order for GHA Mobile Field Service to integrate with Epicor the following customisations are made

### Fields

|Table Name | Field Name | Description |
|---|---|---|
|Company_UD	|GHA_MFS_UserCodeType_c	|Global User Code type used for MFS. Can be overridden by the Plant/Site record|
|CustCnt_UD	|GHA_MFS_KnownAs_c	|Approved requestor - not currently implemented|
|	|GHA_MFS_KnownAs_c	|Known as - not currently implemented|
|Customer_UD	|GHA_MFS_HideCosts_c	|Hides the costs for this customer when the job is completed on the app|
|	|GHA_MFS_HideCostsPage_c	|Hides the cost page when a job is complete on the app - not currently implemented|
|EmpBasic_UD	|GHA_MFS_CurrentJob_c	|The job this employee is currently logged into/working on|
||GHA_MFS_CurrVehicle_c|The vehicle this employee is currently logged in with|
||GHA_MFS_DefaultWarehouse_c	|The default warehouse/vehicle this employee uses. This will be displayed when logging into the app|
||GHA_MFS_Language_c	|The language this employee will see when logged into the tablet|
||GHA_MFS_LastLocated_c	|The last time the app wrote the location (latitude and longitude) of the employee|
||GHA_MFS_LastLoggedIn_c	|The last time the employee logged into the app|
||GHA_MFS_Latitude_c	|The latitude of the employee (logged at time recoded in GHA_MFS_LastLocated_c)|
||GHA_MFS_Longitude_c	|The longitude of the employee (logged at time recoded in GHA_MFS_LastLocated_c)|
||GHA_MFS_Password_c	|The pin/password of the employee, stored as plain text so make sure the appropriate security levels are given to this field|
||GHA_MFS_RestrictWarehouse_c	|This employee can only log in with this vehicle/warehouse on the app|
||GHA_MFS_Status_c	|Flag to state whether the user is currently logged in (true) or not (false) on the tablet|
| FSCallDt_UD | GHA_MFS_CollectPayment_c | Denotes whether the employee should collect payment when on site. Appears as a banner on the app. |
||GHA_MFS_Engineered_c	|Auto engineers the job on creation|
||GHA_MFS_FixedCost_c	|If true the whole job is fixed costs|
||GHA_MFS_FixedLabourRate_c	|The cost of the fixed job is marked as fixed cost, or the cost of the labour if the Labour entry method is set to fixed costs|
||GHA_MFS_HideCosts_c	|Hides the costs for this customer when the job is completed on the app. Takes the value by default from the customer but can be overridden at individual call/job level|
||GHA_MFS_HideCostsPage_c	|Hides the costs page for this customer when the job is completed on the app. Takes the value by default from the customer but can be overridden at individual call/job level. Not yet implemented|
||GHA_MFS_LabourEntryMethod_c	|Time entry method for service calls. Can be set to RT (record time) ME (manual entry) or FC (fixed costs). Defaults from the value stored in the parameter screen.|
||GHA_MFS_LabourIncrement_c	|The rounding factor for labour. Defaults from the value stored in the parameter screen.|
||GHA_MFS_LabourRate_c|The rate for labour. Defaults from the value stored in the parameter screen.|
||GHA_MFS_LabourRateValue_c	|The rate value for labour. Defaults from the value stored against the labour rate|
||GHA_MFS_MileageCap_c	|The mileage cap. Above this value no extra miles will be charged for. Defaults from the value stored in the parameter screen.|
||GHA_MFS_MinimumLabourPeriod_c	|The minimum labour period, if an employee clocks time less than this value this value will be charged for as a minimum. Defaults from the value stored in the parameter screen.|
||GHA_MFS_MinimumTravelTime_c	|Minimum travel time, if an employee clocks less time than this value then this value will be charged as a minimum. Defaults from the value stored in the parameter screen.|
||GHA_MFS_Released_c|Auto releases the job on creation|
||GHA_MFS_TemplateJob_c	|When a job is created it will use this template job to get job details|
||GHA_MFS_TemplateQuote_c|When a job is created it will use the fist line of this quote to get the job details|
||GHA_MFS_TravelFixedCost_c	|The cost of the travel time if the Travel Time Entry method is set to fixed costs|
||GHA_MFS_TravelTimeCap_c|Travel time cap. Above this value no extra travel time will be charged for. Defaults from the value stored in the parameter screen.|
||GHA_MFS_TravelTimeEntryMethod_c	|Travel time entry method for service calls. Can be set to RT (record time) ME (manual entry) or FC (fixed costs). Defaults from the value stored in the parameter screen.|
||GHA_MFS_TravelTimeIncrement_c	|The rounding factor for travel time. Defaults from the value stored in the parameter screen.|
|FSCallhd_UD	|GHA_MFS_ContactNum_c	|The contact number for the customer or customer/ship to combination associated with the job|
|JobHead_UD|GHA_MFS_ApprovedBy_c	|The printed name of the person on site signing off the job on the app|
||GHA_MFS_Arrived_c	|Flag to denote the employee has arrived on the job on the app|
||GHA_MFS_Clear_c	|Flag to denote the employee has cleared on the job on the app. Not yet implemented|
||GHA_MFS_Complete_c	|Flag to denote the employee has completed on the job on the app|
||GHA_MFS_DateComplete_c	|The date the job was completed|
||GHA_MFS_DateLastViewed_c	|The time the job was viewed (expanded on the app) by the employee in GHA_MFS_TechLastViewed_c|
||GHA_MFS_JobType_c	|The type of job used for field service if the Epicor job type is set to MFS. INST (Installation job) or PROD (Production job). Default is production job, only installation jobs appear on the app.|
||GHA_MFS_Paused_c	|Flag to denote the employee has paused on the job on the app|
||GHA_MFS_RevisitNotes_c	|Notes associated with a revisit requested on the app|
||GHA_MFS_RevisitRequired_c	|Flag to denote if a revisit is required, as requested on the app|
||GHA_MFS_Signature_c	|The signature of the customer recorded in the app, stored as a Base64 string and viewable on the MFS Dashboard|
||GHA_MFS_Skipped_c	|Flag to denote the employee has skipped the job on the app|
||GHA_MFS_Started_c|Flag to denote the employee has skipped on the job on the app|
||GHA_MFS_TechLastViewed_c	|The employee who last viewed the job. The time of the view is recorded in GHA_MFS_DateLastViewed_c|
||GHA_MFS_Travelling_c|Flag to denote the employee is travelling to the job on the app|
|JobMtl_UD	|GHA_MFS_Comment_c	|MFS comments entered on the app. Usually a concatenation of the task notes, but can be edited when a job is complete.|
||GHA_MFS_LinkID_c	|External link to GHA MFS|
|JobOper_UD	|GHA_MFS_Cancelled_c	|Denotes the operation/task has been cancelled in the MFS app|
||GHA_MFS_Complete_c	|Denotes the operation/task has been completed in the MFS app|
||GHA_MFS_LinkID_c	|External link to GHA MFS|
||GHA_MFS_Paused_c	|Denotes the operation/task has been paused in the MFS app|
||GHA_MFS_Started_c	|Denotes the operation/task has been started in the MFS app|
|Part_UD	|GHA_MFS_VehicleStock_c	|Denotes the part is to be stocked in a field service vehicle|
|Plant_UD	|GHA_MFS_UserCodeType_c|Global User Code type used for MFS|
|PurMisc_UD	|GHA_MFS_Expense_c	|Denotes a miscellaneous charge is used for a field service expense|
|QuoteHed_UD|GHA_MFS_ContractQuote_c	|Service contract quote|
||GHA_MFS_ServiceQuote_c	|Service call quote|
|Warehse_UD	|GHA_MFS_MobileWarehouse_c	|Denotes the warehouse is a Field Service vehicle|
||GHA_MFS_NonNettable_c	|Indicates if the warehouse will be entirely non nettable|

### BAQs

The BAQs added are primarily used for the initial data import. The results are exported to a csv file and imported into MFS via the license portal.

| BAQ Name            | Corresponsing table in MFS |
|---------------------|----------------------------|
| GHA_MFS_AppSettings | AppSettings                |
| GHA_MFS_Expenses    | mfs.ExpenseTypes           |
| GHA_MFS_EmpBasic    | mfs.Technicians            |
| GHA_MFS_EmpFilter   | mfs.TechnicianFilters      |
| GHA_MFS_WareHses    | mfs.Vehicles               |
| GHA_MFS_Countries   | mfs.Countries              |
| GHA_MFS_Customers   | mfs.Customers              |
| GHA_MFS_ShipTos     | mfs.Sites                  |
| GHA_MFS_RoleCds     | mfs.Roles                  |
| GHA_MFS_Contacts    | mfs.Contacts               |
| GHA_MFS_Parts       | mfs.Parts                  |
| GHA_MFS_PartLots    | mfs.PartLots               |
| GHA_MFS_ReasonCodes | mfs.Reasons                |
| GHA_MFS_Jobs        | mfs.Jobs                   |
| GHA_MFS_Operations  | mfs.Tasks                  |
| GHA_MFS_JobOper     | mfs.JobTasks               |
| GHA_MFS_JobMtl      | mfs.JobMaterials           |
| GHA_MFS_WhseBins    | mfs.VehicleParts           |
| GHA_MFS_PartBin     | mfs.VehicleBins            |
| GHA_MFS_PartSerials | mfs.PartSerials            |
| GHA_MFS_Equipment   | mfs.Equipment              |
| GHA_MFS_Users       | Users                      |

There is a set of BAQs used for the Vehicle Bin sync functionality

|BAQ Name|
|---|
|GHA_MFS_PartBinSync|
|GHA_MFS_PartBinSyncZero|
|GHA_MFS_PartBinMisc|
|GHA_MFS_PartSerials|


Other BAQs are also used by dashboards within Epicor


| BAQ Name                    | Dashboard          |
|-----------------------------|--------------------|
| GHA_MFS_Dashboard           | GHA_MFS            |
| GHA-MFSTasks                | GHA_MFS            |
| GHA-MFSMaterials            | GHA_MFS            |
| GHA_MFS_Images              | GHA_MFS            |
| GHA_MFS_Status_Combo        | GHA-MFSStatus      |
| GHA_MFS_Status_Transactions | GHA-MFSStatus      |
| GHA_MFS_Errors              | GHA_MFS_Errors     |
| GHA_MFS_Directives          | GHA_MFS_Directives |

And finally these BAQs are used for Field Service functionality

| BAQ Name |
|---|
| GHA_MFS_JobLabour |
| GHA_MFS_JobPlants |
| GHA_MFS_Version |

### Link BPMs and Functions

The following BPMS act as triggers to update the field service database. When data is changed in Epicor, a link BPM is fired. Each BPM then calls Epicor functions which

a) call an API within the MFS Application whose purpose is to add a message to the message queue with the data that has been updated
b) add a 'sent' entry to a UD table (defined on the parameter screen) which can be observed in the GHA-MFSStatus Dashboard. This is a parent/child UD table, the child table showing all the transactions and the parent table showing the result of the last transaction.

For completeness, when the record sent from Epicor has updated in MFS a call is sent back to Epicor to add an 'Received' entry to the UD table. Hence each update to Epicor should have a corresponding handshake (message sent to MFS, message received from MFS).

The handshakes can be observed in MFS by viewing the mfs.MessageLogs table which show the message received from Epicor and the corresponding handshake sent back.

| Directive Type | Business Process Method | Description |
|----------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Data Directive | Country     | GHA MFS Country Link                                                                                                                                                                                                                                                                                 |
| Data Directive | CustCnt     | GHA MFS Contact Link                                                                                                                                                                                                                                                                                   |
| Data Directive | Customer    | GHA MFS Customer Link                                                                                                                                                                                                                                                                                  |
| Data Directive | EmpBasic    | GHA MFS Employee Link                                                                                                                                                                                                                                                                                  |
| Data Directive | FSCallDt    | GHA MFS FS Call Detail Link                                                                                                                                                                                                                                                                            |
| Data Directive | FSCallHd    | GHA MFS FS Call Header Link                                                                                                                                                                                                                                                                            |
| Data Directive | FSCallHd    | GHA MFS FS Call OTS Link                                                                                                                                                                                                                                                                               |
| Data Directive | FSTech      | GHA MFS FS Technician Link                                                                                                                                                                                                                                                                             |
| Data Directive | JCShift     | GHA MFS Shift Link (Employee filters)                                                                                                                                                                                                                                                                  |
| Data Directive | JobHead     | GHA MFS Job Head Link (Service Jobs)                                                                                                                                                                                                                                                                   |
| Data Directive | JobHead     | GHA MFS Job Head Link (Installation Jobs)                                                                                                                                                                                                                                                              |
| Data Directive | JobMtl      | GHA MFS Job Material Link (Service Jobs)                                                                                                                                                                                                                                                               |
| Data Directive | JobMtl      | GHA MFS Job Material Link (Installation Jobs)                                                                                                                                                                                                                                                          |
| Data Directive | JobOpDtl    | GHA MFS Job Resource Link (Service Jobs)                                                                                                                                                                                                                                                               |
| Data Directive | JobOpDtl    | GHA MFS Job Resource Link (Installation Jobs)                                                                                                                                                                                                                                                          |
| Data Directive | JobOper     | GHA MFS Job Operation Link (Service Calls)                                                                                                                                                                                                                                                             |
| Data Directive | JobOper     | GHA MFS Job Operation Link (Installation Jobs)                                                                                                                                                                                                                                                         |
| Data Directive | OpMaster    | GHA MFS Operation Link                                                                                                                                                                                                                                                                                 |
| Data Directive | OpMaster    | If an operation type is changed to service go though all open service jobs with the operation and send them up to field service.<br><br>If an operation type is changed to manufacturing go though all open service jobs with the operation and send them up to field service with the delete flag set |
| Data Directive | Part        | GHA MFS Part Link                                                                                                                                                                                                                                                                                      |
| Data Directive | PartBin     | GHA MFS Part Bin Link                                                                                                                                                                                                                                                                                  |
| Data Directive | PartBinInfo | GHA MFS Part Bin Info Link                                                                                                                                                                                                                                                                             |
| Data Directive | PartLot     | GHA MFS Part Lot Link                                                                                                                                                                                                                                                                                  |
| Data Directive | PartWhse    | GHA MFS Part Warehouse Link                                                                                                                                                                                                                                                                            |
| Data Directive | PlantWhse   | GHA MFS Plant Warehouse Link                                                                                                                                                                                                                                                                           |
|Data Directive	|PurMisc	|GHA MFS Purchase Terms Link|
|Data Directive	|Resource	|GHA MFS Resource Link|
|Data Directive	|ResourceGroup	|GHA MFS Resource Group Link|
|Data Directive	|RoleCd	|GHA MFS Role Code Link|
|Data Directive	|SerialNo	|GHA MFS Serial Number Link|
|Data Directive	|ShipTo	|GHA MFS Ship To Link|
|Data Directive	|UserFile	|GHA MFS User Link|
|Method Directive|Warehse	|GHA MFS Warehouse Link|
|Data Directive|Warehse	|GHA MFS Warehouse Link (add warehouse to all parts)|
|Data Directive	|WhseBin	|GHA MFS Warehouse Bin Link|
|Data Directive	|SysCompany	|GHA MFS Timezone Link|
|Data Directive|UDCodes|GHA MFS Misc Parts Link|
|Data Directive	|UDCodes	|GHA MFS Expense Type Link|
|Data Directive	|UDCodes	|GHA MFS Reason Code Link|
|Data Directive	|UDCodes	|GHA MFS Parameter Screen Link|
|Data Directive	|UDCodes	|GHA MFS Employee Filter Link|

The functions are found in the GHA-MFS Function group

|Function	|Purpose|
|---|---|
|CallFieldService|Send message to MFS|
|GetSync	|Write the 'sent' record to the status UD table|

***Special note about job operation and job material links***

Because Epicor operation and material sequences are changeable, and to accomodate offline functionality (eg if changes are made when the app is offline and therefore has no knowledge of the new sequence), each task and material in the MFS database is given a unique identifier (`GHA_MFS_ERPLinkID`). When an operation or material is added in Epicor the Link ID is updated by the MFS Application. All subsequent updates (both MFS > Epicor and Epicor > MFS) use this Link ID.

If the Link ID is not set when the operation or material is added unexpected results can occur. This is often because changes are made before the link is properly set up, or if Epicor cannot communicate with the MFS Application.

See [here](/Apps/MobileFieldService/TechnicalReference/JobLinks) for an in depth discussion about handshaking jobs and calls between field service and Epicor

### Other BPMs and Functions

Other than change log data directives which moinitor all the added MFS fields, there arer the following business process methods:

| Directive Type       | Business Process Method                | Description                                                                                                            |
|----------------------|----------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Method Directive     | EmpBasic.Update                        | Restricted warehouse/vehicle logic                                                                                     |
| Data Directive       | EmpBasic                               | Sets the resource active flag to match the employee                                                                    |
| Data Directive       | FSCallDt                               | Sets defaults on service line call from parameter page                                                                 |
| Data Directive       | FSCallHd                               | Prevent voiding of started jobs                                                                                        |
| Method Directive     | JobEntry.GetNewJobHead                 | Set jobtype to 'PROD' by default                                                                                       |
| Method Directive     | JobEntry.GetNewJobMtl                  | If job is fixed cost default material billing to false                                                                 |
| Method Directive     | JobEntry.GetNewJobOper                 | If job is fixed cost default operation billing to false                                                                |
| Method Directive     | JobEntry.InsertOperationOP             | Copy costs from job header to operation                                                                                |
| Method Directive     | JobEntry.Update                        | Prevent job being unreleased if job has already started on the app                                                     |
| Method Directive     | JobEntry.Update                        | Display a warning message if job is fixed costs but material or operation billing is set to true                       |
| Method Directive     | JobEntry.Update                        | Display a warning message if jjob has material and/or laboour covered but material or operation billing is set to true |
| Data Directive       | JobHead.Update                         | Set the default job type to MAIN for maintenenace jobs and SERV for service jobs                                       |
| Data Directive       | JobOper.Update                         | Copy labour rates fom service call                                                                                     |
| Data Directive       | LaborDtl.Update                        | Fix burden costs according to parameter screen                                                                         |
| Data Directive	Part | Update                                 | Add vehicles to part when it is marked a a field service part                                                          |
| Method Directive     | Quote.GetNewQuoteDtl                   | Mark new quote line as a template so it can be picked up in the service call line                                      |
| Method Directive     | ServiceCallCenter.CreateServiceCallJob | Populate resource from technician                                                                                      |
| Method Directive     | ServiceCallCenter.CreateServiceCallJob | Create job from template                                                                                               |
| Method Directive     | ServiceCallCenter.CreateServiceCallJob | Create job from quote                                                                                                  |
| Method Directive     | Warehse.Update                         | Add parts to warehouse if warehouse marked as field service vehicle                                                    |
| Data directive       | Warehse.Update                         | Update all bins in warehouse with custom non nettable flag                                                             |
| Method Directive     | WhseBin.CommitGeneratedBins            | Update all bins in warehouse with custom non nettable flag                                                             |
| Method Directive     | WhseBin.Update                         | Update bin with custom non nettable flag from warehouse                                                                |


### Dashboards

The following dashboards are installed

|Name	|Description|
|---|---|
|GHA_MFS	|Main dashboard showing service calls and information recorded on the app
|GHA-MFSStatus	|Status dashboard showing the sync transactions between Epicor and Field Service
|GHA_MFS_Errors	|Errors recorded in Field Service when using the app are posted to a UD table in Epicor and displayed here
|GHA_MFS_Directives	|Updatable dashboard of MFS method and data directives allowing them to be enaled/diabled (does not appear on the menu)


### Menus

Custom forms have been created displaying the UD fields added for MFS. These are available on the menus under GHA Modifications > GHA Mobile Field Service along with the dashboards


### Parameters

The GHA Parameter screen records the parameters set in the UD codes. These parameters are also synchronised to the MFS database.

The important parameter is the Company Code. This is used as an API key to allow Epicor to synchronise with MFS. Until this code is entered (and the link BPMs enabled) nothing will synchronise correctly.

The sync logs will not start until the MFS Status parameter is set.

## License Portal

The customer needs to be set up in the GHA License Portal and the Mobile Field Service application added

### Epicor Links

In order for MFS to update Epicor (via Epicor REST calls) connection details need to be entered into the license portal

There are two connection to set up, one for live and one for test. For the difference see the next section. The connection requires the following:


| Parameter                 | Description                                                                                                   |
|---------------------------|---------------------------------------------------------------------------------------------------------------|
| Application Pool Host     | Epicor https server                                                                                           |
| Application Pool Instance | The name of the Epicor application pool                                                                       |
| Company                   | The Epicor company this license pertains to (licensing is done by Epicor company, not Epicor instance)        |
| User name                 | Epicor user name - see below                                                                                  |
| Password                  | Epicor password                                                                                               |
| License Type              | If purchased the customer may wish to use Web Service licenses - these are cheaper than normal user licenses. |

The REST calls do not open an Epicor Session and only last as long as the call is being made.

The Epicor username is used to make the REST calls from the app and should have permissions to Company, Site, Service Jobs ...need to verify and expand

All transactions (eg job issuing, stock movements) are made with a reference to the employee that is logged into the app.

The MFS back end is authenticated using Epicor so transactions are made against the logged in user.

### Test and Live Databases

There are two environments for each customer, the live environment and a test environment.

Devices running the app are connected to the live database by default. In order to connect to the test environment, within the license portal the device should be marked as a test device.

To sync a test Epicor environment to the test MFS environment, tick the Test Environment flag in Epicor on the Parameter screen.

To sync the test MFS environment to a test Epicor environment, fill in the test Epicor connection details in the license portal

*By default Epicor 'talks' to the live MFS application. It is possible to connect Epicor to a different application (eg development, test, staging).*

## Initial Data Load

Loading data from Epicor to MFS is a three step process.

1. Extract the data from Epicor via BAQs
2. Import the data into MFS

Note that the import can be done at any time but will update existing data. It is possible for GHA to clear the data completely, but a full import will then be required.

### Extract the data from Epicor via BAQs

There is a set of BAQs that have been provided for exporting data from Epicor to initially populate MFS, listed above.

The standard way of extracting data using the BAQ Export Process to generate a file for import, followed by Server File Download in Epicor to retreive the generated file.

### Import the data into MFS

The files generated from Epicor are imported into MFS using the license portal.

The license portal parses the file into batches of 500 rows.

Each batch is then uploaded to the MFS Application which converts the data into messages and adds them to the synchronisation MFS MQ.

Data which is in an unexpected format will return an error which will be displayed on the License Portal.

Sometimes the data may be in a format which cannot be parsed and the License Portal does not receive a response from the MFS Application and the web page will get 'stuck, ie the wait cursor will display and the page will not respond. If this occurs send the offending file to GHA for further investigation.

## Real Time Synchronisation from Epicor to MFS

Real time synchronisation is achieved by data directives monitoring the relevant tables in Epicor and calling

The mechanism is discussed above under Link BPMs

# Mobile Application

## Tablet/App management

### Register device

A device is registered by scanning a barcode, the barcode format should be:

`{license key for application}~{license key for customer}`

eg 1034-9896-0081-1266-4452-4496-7774-2451~0582-3567-0379-2478-7659-3757-7088-6028

```qrcode-complex
	{
		"text": "1034-9896-0081-1266-4452-4496-7774-2451~0582-3567-0379-2478-7659-3757-7088-6028",
		"width": 200,
		"margin": 2,
		"dark": "#000",
		"light": "#FFF",
		"errorCorrectionLevel": "M"
	}
```

When a device is registered this key is sent up along with a unique device id. The following steps then occur to register the device

- the combination of application licence key and customer licence key are validated against the settings in the MFS
- check the customer and/or application has not been suspended by GHA
- check the device does not already exist
- check whether there are any licences available

If all the above criteria are met the device is registered successfully

If a device is reregistered it will have no effect, ie the server side application will recognise the device has already been registered, and a message saying as much will be displayed on the device.

However...

The device id is a UID (Unique Identifier) which is assigned by the mobile device for a specific application. If the application, ie MFS is removed from the device and reinstalled a new device id is generated. This means that reregistering the device will take an additional licence.

### Device security and token validation

Every call from the tablet has a JWT (JSON Web Token) attached with the following information:

- Device ID
- Application Key
- Customer Key
- Customer Application Key
- Date

Each token is validated against the customer database in the MFS application.

The first checks are similar to those when the device is registered:

- the combination of application licence key and customer licence key are validated against the settings in the MFS
- check the customer and/or application has not been suspended by GHA
- check the device has not been suspended or deleted

The Date is used against the device as a NONCE (Number Once) to make sure it is valid - if a token is used twice it is ignored and a token must be later than the previous date stored.

If the token is valid the call is diverted to the correct customer database to update and retreive data. If the device is marked as a test device the API call is diverted to the TEST database, other wise the live one.

The application version on the device is displayed on the license portal.

### Language

The MFS Database stores a list of language files which can be used to display the text of the MFS Application in different languages

Currently only English is supported

When a technician opens the app the language list appears on the log in screen. The current language selected depends on a heirarchy:

1. English
2. The language stored against the customer (cannot be set anywhere but should be on the license portal)
3. The language stored against the technician.

> The default language is also stored in Epicor in the EmpBasic.GHA_MFS_Language_c field. It can be updated here using a iso 2 character code, provided the language is supported by the MFS application, and will be passed back to the MFS application.

### Saving the language default for the technician

If the technician changes the language on the login screen, this language will be saved on the MFS Application

> The language is subsequently passed to Epicor to be stored in the EmpBasic.GHA_MFS_Language_c field as above.

### Language management

Languages are updated using language files. Currently only the English language file is part of MFS, any further languages would need to be translated by a competent speaker of the target language.

## Technician Management

### Retrieve technicians and vehicles

When the MFS App is first opened it displays the log in page.

Normally a full list of active technicians and vehicles is displayed.

> The technician list is uploaded from Epicor. To be treated as valid technicians they need to be active and marked as Service Technicians on the Employee screen

The last logged on technician is remembered on the log in screen, but you can choose another should a different technician be using the tablet.

---

It is possible to put in a default vehicle for each technician, and optionally to force the technician to only use a particular vehicle.

> The default vehicle is managed in Epicor on the custom MFS Employee screen. The fields affected are:
> 	GHA_MFS_DefaultWarehouse_c
> 	GHA_MFS_RestrictWarehouse_c

---

It is also possible to set a password for the technician, though there is no way to change this through the app.

> The password can only be set in the custom MFS Employee form, updating the field GHA_MFS_Password_c.
> Note the password is stored in the Epicor table as plain text, so the appropriate security should be set up on this field.


### Login

Checks the technician/vehicle/password are correct.

**Note** a technician is not allowed to log in if they are already logged in on another device.

The version of the app is sent which can be used in the license portal to ensure the devices are up to date.

> On a successful log in the employee record is Epicor is updated 
> 
> Updates Epicor using the `EmpBasicSvc.EmpBasics` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Status_c` to true
> 	`GHA_MFS_LastLoggedIn_c` to the time the technician logged in at

Checks to see if the technician has an active job or task, and if so logs the login time against that job/task.

> The pause flag job record in epicor is cleared. This is because logging into a job  resumes a paused job.
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Paused_c` to false	

### Company/Technician/Device settings

After logging various settings are downloaded from the MFS Application.

***Company Settings***

- Mileage Required - if true the mileage is requested on the app on arrival
- Currency String - the currency symbol displayed on the app
- Original BOM - not used
- Default Zoom - the default zoom for the map on the app
- Enable Photos - enable photos to be taken during a task
- Photo Resolution - photo resolution low/med/high
- Enable Expenses - enable expenses to be entered
- Enable Expense Photo - enable a photo to be taken of an expense receipt
- ERP Link - whether the app is linked to an ERP system (if true allow a vehicle part sync)
- Hide Costs - hide the costs from the job approval screen when the job is finished
- Monitor Keys - whether or not to monitor all key presses
- Hide Utilities - whether or not to display the utilities button
- Enable Revisit - whether or not to enable the revisit site button
- Enable Vehicle Part Sync - whether or not to enable vehicle part sync
- Enable Skip And Clear - whether or not to enable skip and clear

***Technician Settings***

- Language(if it has been set against the technician record (see [Language](#Language) section above))

***Device Settings***

- Test device (as discussed in [Test and Live Databases](### Test and Live Databases) above)

### Tracking the Technicians Location

Every 15 seconds ***while the MFS application is running, and providing location services have been enabled for the app, and location services are running on the device*** the app will send the location of the device to the application.

> The location is forwarded onto Epicor and stored in the employee table. The location is not displayed anywhere but can be used eg in a dashboard
> 
> Updates Epicor using the `EmpBasicSvc.EmpBasics` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Latitude_c`
> 	`GHA_MFS_Longitude_c` 

### Log out

Validates the technician

> On a successful log out the employee record is Epicor is updated 
> 
> Updates Epicor using the `EmpBasicSvc.EmpBasics` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Status_c` to false
> 	`GHA_MFS_LastLoggedIn_c` to the time the technician logged out at

Checks to see if the technician has an active job or task, and if so logs the logout time against that job/task.

> The pause flag job record in epicor is set. This is because logging out of a job  pauses a job.
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Paused_c` to true	

## Home Page

### Job List

The list of jobs on the front page is displayed from the jobs in the MFS application with the following criteria:

- Assigned to the logged in technician
- The scheduled date of the job is within the defined window
- Not void
- Open (not complete)

> The window for the scheduled dates is set on the parameter screen in Epicor as Days Before and Days After

### Vehicle Parts

All parts are shown for the vehicle selected

Serial numbers are displayed if applicable

'Miscellaneous' parts (expenses, mileage, travel, fixed costs) are filtered out

If the vehicle parts are being synced from ERP then a flag shows this - when the sync has finished the flag is cleared.

### Viewing a job

Displays all fields and sections of a job

## Attending a Job

### Travelling

Travelling only displays if the travel entry method on a job is set to Record time
The job travelling status is set and the time is saved against the job

If travelling has already been started it ignores any subsequent key presses, ie does not start the travel time again from the time of the second key press

> The travelling flag job record in epicor is set. The skipped flag is cleared as any skipped job has been resumed.
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Skipped_c` to false	
> 	`GHA_MFS_Travelling_c` to true	


### Arriving

The job arrived status is set and the time is saved against the job.

***Travel time***

If Travel Entry is set to Record Time the time for travelling is calculated from the start travel time and arrive time and recorded against the job.

If Travel Entry is set to Enter Time then the time for travelling is entered from the app.

If Travel Entry is set to Fixed Costs then the time is set to 1 (ie the cost only is recorded).

After the travel time has been calculated it is added as a material line to the job. Only one instance of travel is allowed per job, and changing the travel time updates the existing entry.

> The arrived flag job record in epicor is set. The skipped flag is cleared as any skipped job has been resumed.
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Skipped_c` to false	
> 	`GHA_MFS_Arrived_c` to true	

> Travel is added to the job in Epicor using the mechanism described in [Add and Issue Material from Vehicle](#Add and Issue Material from Vehicle)

***Mileage***

How mileage is requested depends on the type of job. For jobs which Record Time a box pops up when arriving on site. For Manula Entry jobs a separate button appears to log mileage and travel time. Fixed Cost jobs do not request mileage.

> For mileage to be requested there should be a milesge part number defined on the Epicor parameer screen, which should be marked as active

After the travel time has been calculated it is added as a material line to the job. Only one instance of mileage is allowed per job, and changing the mileage updates the existing entry.

> Mileage is added to the job in Epicor using the mechanism described in [Add and Issue Material from Vehicle](#Add and Issue Material from Vehicle)

## Arriving on site

### Call/equipment history

The equipment history list is displayed according to the following criteria:

- If the job has a serial number then only jobs with that serial number are displayed.

- If the job has a valid part number but is not serial tracked that only jobs with that part number are displayed.

- if the job has an invalid part number (ie one that is not in the part records) then all jobs performed on that site are displayed.

### Update Location

Saves the current location of the app/tablet against the customer site.

### Start a job

The job started status is set and the time is saved against the job.

> The started flag job record in epicor is set. The skipped flag is cleared as any skipped job has been resumed.
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Skipped_c` to false	
> 	`GHA_MFS_Started_c` to true	

### Skip Job

Clears the job travelled, arrived and started flags

Sets the job skipped flag and records the reason and time against the job.

> The skipped flag job record in epicor is set. The started flag is cleared.
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Skipped_c` to true
> 	`GHA_MFS_Started_c` to false

### Update Travel and Mileage

The travel time and mileage can be altered after the job has started. It follows the same logic as [Arriving](#Arriving) above.

## Performing a job

### Pause

The job paused status is set and the time is saved against the job with a reason.

> The paused flag job record in epicor is set. 
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Paused_c` to true

### Resume

The job paused status is cleared and the time is saved against the job.

> The paused flag job record in epicor is cleared. 
> 
> Updates Epicor using the `JobEntrySvc.JobEntries` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Paused_c` to false

### Add/Edit Task

Adds or updates the task on the job

If adding a task the task sequence number is the next incremental

> Adds the task as an operation to the job in Epicor
> 
> Retreives the `OpMaster.BillLaborRate` for the added task/operation (to use in the subsequent REST call)
> 
> Adds a new task using the `JobEntrySvc.JobOpers` REST call
> 
> Sets the following fields in Epicor:
> 	`AssemblySeq` - always set to 0 as job assemblies are not supported
> 	`OprSeq` - set to 0 so it adds a new task
> 	`OpCode` - the task id/operation code
> 	`EstProdHours` - the estimated time for the task entered on the app 	`ProdStandard` - the estimated time for the task entered on the app 	`EstLabHours` - the estimated time for the task entered on the app 
> 	`StdFormat` - 'HR' - production standard fixed hours
> 	`QtyPer` - 1
> 	`DocLaborRate` - the BillLaborRate from the operation
> 	`LaborRate` - the BillLaborRate from the operation
> 	`DocBillableLaborRate` - the BillLaborRate from the operation
> 	`BillableLaborRate` - the BillLaborRate from the operation
> 	`Billable` - the billable flag set on the app
> 	`Instructions` - the detail notes written on the app
> 	`GHA_MFS_LinkID_c` - the unique identifier of the task in the MFS database

### Start Task

The task started status is set and the time is saved against the task.

### Finish Task

The task ended status is set and the time is saved against the task.

If Labour Entry is set to Enter Time, the task times are recorded as a list from each entry.

If Labour Entry is set to Record Time the task times are calculated from the job time list.

- Calculate the time between the start and end of the task in minutes
- Calculate the time between pauses in minutes
- Subtract the pauses from the total time

If Labour Entry is set to Fixed Cost no entry is made (the fixed costs for a job are entered as material)

The labour time is then rounded
- Check the time is more than the minimum Job Time
- Round the time to the next Labour Increment

Book labour flag??? Fixed costs

> Job Times and Labour Increments are set in Epicor from the defaults on the parameter screen. The can be overwritten on the service call screen.

> In Epicor the comments added to the task are saved in `JopOper.CommentText`
> 
> If the Labour Entry is set to Fixed Cost, the operation is marked as complete without booking labour by setting the `GHA_MFS_OpComplete` flag

> Labour is booked in Epicor. If the labour record for the employee on the day the task was performed does not exist it is created.
> 
> Adds a new labour entry using the `LabourSvc.LaborDtls` REST call
> 
> Sets the following fields in Epicor:
> 	`LaborType` - P - Production
> 	`LaborTypePseudo` - 'V' for service tasks, 'P" for production/installation
> 	`LaborQty` - 1
> 	`JobNum` - the estimated time for the task entered on the app 	`AssemblySeq` - 0, subassemblies on jobs are not supported
> 	`OprSeq` - the operation sequence from Epicor
> 	`OpCode` - the operation code from Epicor
> 	
> 	The following three fields are taken from the employee and read from the BAQ GHA_MFS_EmpBasic. They are required fields for labour to book
> 	`JCDept` - the technician's/employee's department
> 	`ResourceGrpID` - the technician's/employee's resource group
> 	`ExpenseCode` - the technician's/employee's expense code
> 	
> 	`BillServiceRate` - the Labour Rate which came from the operation in Epicor when the task was created
> 	`ClockInDate` - the date the task was performed on
> 	`ClockinTime` - the time the task was started
> 	`ClockOutTime` - the time the task was completed
> 	`LaborHrs` - the calculated hours for the task (considering pauses entered on the app, and minimum job time and rounding from the parameter screen)
> 	`TimeStatus` - A - Approved
> 	`FSComplete` - whether the operation is completed (true for non fixed cost jobs)
> 	`Complete` - whether the operation is completed (true for non fixed cost jobs)
> 	`FSComplete` - the unique identifier of the task in the MFS database
> 	`FSComplete` - the unique identifier of the task in the MFS database
> 	`OpComplete` - whether the operation is completed (true for non fixed cost jobs)
> 	Burden hours are set according to the setting on the parameter screen
> 	`BurdenHrs` - 
> 		Burden = Labour - forces the burden hours to equal the labour hours
> 		Burden = Zero - forces the burden hours to be zero
> 		Epicor Sets Burden - burden hours are not added to the call and Epicor calculates as normal

### Delete a task

Sets the cancelled flag on the task, which it hides it from all subsequent displays and calculations

> The cancelled flag on the j operation record in epicor is set. 
> 
> Updates Epicor using the `JobEntrySvc.JobOpers` REST call
> 
> Changes the following field in Epicor
> 	`GHA_MFS_Cancelled_c` to true

### Task Notes

Updates the notes on the task

> Update Epicor using the same logic as [Add/Edit Task](#Add/Edit Task)

### Issue Material

This section covers both adding and returning material from the job. The MFS Application is only concerned with the differences between the saved job materials and the state of the materials when the app processes the changes.

Each line of material is processed separately.

Serial numbers are marked as either 'JOB' if they have been issued on the job or 'INVENTORY' if they have been returned. Serial numbers issued to a job are linked against the appropriate job material.

The vehicle part quantity is updated.

Transactions are recorded against both the part and the job.

The quantity material record of the job is updated.

> Material is issued from the job using `IssueReturnSvc.PerformMaterialMovement`
> 
> Material can be returned too using the same call


### Add and Issue Material from Vehicle

Material which is added from the Vehicle Parts screen on the app is added to the job materials in the MFS Database.

> Material is added in Epicor using the following business method calls:
> 	JobEntrySvc.GetNewJobMtl
> 	JobEntrySvc.ChangeJobMtlPartNum
> 	JobEntrySvc.ChangeJobMtlQtyPer
> 	JobEntrySvc.Update
> 	
> ***Costs***
> Epicor will calculate the cost of the material. 
> 
> If the material is non billable the following fields are set to zero:
> 	`JobMtl.UnitPrice`
> 	`JobMtl.BillableUnitPrice`
> 	`JobMtl.DocUnitPrice`
> 	`JobMtl.DocBillableUnitPrice`
> 	
> If the material added is one of the special parts, ie Travel, Mileage, Expenses or Fixed Costs, the following fields are set to the value as defined on the parameter screen or the service call:
> 	`JobMtl.UnitPrice`
> 	`JobMtl.BillableUnitPrice`
> 	`JobMtl.DocUnitPrice`
> 	`JobMtl.DocBillableUnitPrice`
> 	
>   ![pasted_image_20230118094126.png](/Apps/MobileFieldService/techref/pasted_image_20230118094126.png)
> 	
> For expenses the following fields are set to the expense amount in Epicor:
> 	`JobMtl.EstMtlUnitCost`
> 	`JobMtl.EstUnitCost`
> 	`JobMtl.MaterialMtlCost`
> 	
> 	![pasted_image_20230118094055.png](/Apps/MobileFieldService/techref/pasted_image_20230118094055.png)
> 	


After this it is issued as in [Issue Material](#Issue Material) above.

### Manage Expenses

Expenses are added, edited and deleted and stored against the job.

### Take Picture

Photos are stored against the job

> Photos (and signatures) are stored in the FileStore table as Base64 strings. 
> 
> Adds a new file store entry using the `FileStoreSvc.Create` REST call
> 
> Sets the following fields in Epicor:
> 	`bytes` - the image converted to a Base 64 string
> 	`foreignSysRowID` - the SysRowID of the job the image relates to
> 	`relatedToSchemaName` - 'Erp'
> 	`relatedToTable` - 'JobHead'
> 	`fileName` - a sequential number for the file on the job, starting at 00001
> 
> There is a BAQ in Epicor (GHA_MFS_Images) which will pull the image strings from the table and a dashboard customisation (GHA_MFS, MFS Dashboard) which will convert these into images for display

## Utilities

### Resync Vehicle Stock

> This only works if MFS is linked to an ERP system, eg Epicor
> 
> Data from the following BAQs is obtained from Epicor:
> 	GHA_MFS_PartBinSync
> 	GHA_MFS_PartBinSyncZero
> 	GHA_MFS_PartBinMisc
> 	GHA_MFS_PartSerials
> Filtered for the vehicle which is being synchronised
> 
> Every vehicle stock record sets a flag against the vehicle to say it is being synchronised, apart from the last record which clears the flag. This mechanism allows app to report the stock is being synced.

## Finishing a job

### Finish job screen

Displays all the data from the job

If the Hide Costs flag is set then the costs are not shown

> When material is added and issued it retreives the costs from Epicor. This may take a few seconds especially if a lot of material has been added (it waits for the material to be added to and issued from the job and retreives the cost calculated by Epicor). If the costs are still updating a message saying so is displayed on the app. There is a CostUpdated flag on each job material.


### Edit Report

Updates the comments on the job.

### Cash Payment

Adds a payment record to the job.

### Approve and Finish

The job approved and complete flags are set and the time the job has completed recorded.

The signature and approved by name are recorded against the job

Any revisit notes (and the required flag) are recorded against the job

Expenses are converted into job materials

> For each expense a material line is added to the job using the mechanism described in [Add and Issue Material from Vehicle](#Add and Issue Material from Vehicle)

Set close job flag

> The job header in Epicor is updated using the `LabourSvc.LaborDtls` REST call
> 
> Sets the following fields in Epicor:
> 	`LaborType` - P - Production
> 	
> 	> 
> > Adds a new labour entry using the `JobEntrySvc.JobEntrySvc` REST call
> 
> Sets the following fields in Epicor:
> 	`CommentText` - the job comment/notes from the app approval screen
> 	`GHA_MFS_Signature_c` - the sigature written on the app, stored as Base64 string in the file store table (see [Photos](#Photos))
> 	`GHA_MFS_ApprovedBy_c` - the print name field from the app
> 	`GHA_MFS_Complete_c` - flag to say the job has been completed on the app
> 	`GHA_MFS_DateComplete_c` 
> 	`GHA_MFS_RevisitRequired_c` 
> 	`GHA_MFS_RevisitNotes_c` 
> 	
> If the Close Call Job on Approval flag is set on the Epicor parameters screen then the service call is closed on Epicor using the `ServiceCallCenterSvc.CloseServiceCall` REST call
> 
> Intallation/production are never closed by the app (only the GHA_MFS_Complete_c flag is set)
> 	

## Miscellaneous

### Timings

If the app is online the current time of the device is sent

If the app is offline the time the transaction is stored and sent when the app is resynchronised

Times are stored in UTC but are displayed according to the timezone set in the company settings.

> Times are sent to Epicor using the timezone set in the company settings in the MFS Application
> 
> The timezone can be set in the Company Maintenance screen in Epicor

### Offline Functionality

If the device is offline then the transaction are stored within the app. When connectivity iss restored the transactions are uploaded to the MFS application in the order they were made, using the original time

### Synchronise device

The app will synchronise the following

- Job list (for the currently logged in techncian)
	- tasks
	- materials
	- times
	- costs
	- expenses
	- history 
- Reason codes (for job pausing and job skipping)
- Expense types
- Task type
- Vehicle parts (for the currently logged vehicle)

This will download all changes since the last sync

The app will do a full download/sync to the MFS Database...

### Monitor Key Strokes

If the Monitor Keys flag is set agains the company then every key stroke is logged in the MFS Database, for debugging purposes.

### Logs

There are four types of logging:

- Change Logs - changes to the data written into the MFS database tables
- Error Logs - errors trapped within the application
- Key Logs - key strokes from the app
- Message Logs - messages both to and from the ERP application

Logs are set to clear after 60 days
