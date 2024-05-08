---
title: AP Automation Configuration
description: AP Configuration
published: true
date: 2024-01-19T15:07:34.537Z
tags: 
editor: markdown
dateCreated: 2023-12-21T12:08:41.549Z
---

[Back to AP Automation Home](/Apps/ap-automation)

# AP Automation Configuration

The AP automation process works by having supplier invoices sent to a central email repository, where a process then runs to ‘capture’ the invoice.

### Parameters
Within Epicor there are parameters that can be set to support the AP automation process.
To add or review the parameters, search under GHA Modifications> Parameters> Setup> Parameter Maintenance
![ap1.png](/apautomation/ap1.png)

•	Select Integrations> AP automation -  (<span style="color:blue">1</span>)
•	A number of Default settings can be assigned. 
&nbsp;&nbsp;&nbsp;&nbsp;o	The Matching Type  can be assigned – these are PO Only, PO and Receipt and no matching
&nbsp;&nbsp;&nbsp;&nbsp;o	The Group frequency  can be assigned - these are Monthly (default), Fornightly, Weekly or Daily – (<span style="color:blue">2</span>)
&nbsp;&nbsp;&nbsp;&nbsp;o	Header  and  line  tolerances -  (<span style="color:blue">3</span>).  These can be a % or a value.  For example, if the company default tolerance for a PO to be matched is 5% and this is set, then any PO received and matched will be automatically processed if the total PO value falls within this limit.
&nbsp;&nbsp;&nbsp;&nbsp;o	Setting the Default Review AP Group Prefix and Default Matched AP Group Prefix will put the value in front of the AP group during the AP Automation process – (<span style="color:blue">4</span>)
&nbsp;&nbsp;&nbsp;&nbsp;o	Setting the above will use these as defaults when using the AP automation but these will be overridden if there settings specific to a supplier (covered further down in this document).

### Suppliers
If the supplier is to have specific parameters, these can be set on the Supplier.
To add or review the parameters, search under GHA Modifications> AP Automation> Setup> Supplier

**Classic**
![ap2.png](/apautomation/ap2.png)
•	Select the Supplier> AP Automation tab – (<span style="color:blue">1</span>)
•	The default Matching type can be assigned – (<span style="color:blue">2</span>). These are PO Only, PO and Receipt and no matching and setting tat this level will override any set at the company level in Parameter Maintenance
•	Header  and  line  tolerances -  (<span style="color:blue">3</span>).  These can be a % or a value.  For example, if the company default tolerance for a PO to be matched is 5% and this is set, then any PO received and matched will be automatically processed if the total PO value falls within this limit.
•	Setting the Default Review AP Group Prefix and Default Matched AP Group Prefix will put the value in front of the AP group during the AP Automation process – (<span style="color:blue">4</span>)

**Kinetic**
![ap3.png](/apautomation/ap3.png)
•	Select the supplier to change from the main list.
•	Select the Supplier> AP Automation card – (<span style="color:blue">1</span>)
•	The default Matching type can be assigned – (<span style="color:blue">2</span>). These are PO Only, PO and Receipt and no matching and setting tat this level will override any set at the company level in Parameter Maintenance
•	Header  and  line  tolerances -  (<span style="color:blue">3</span>).  These can be a % or a value.  For example, if the company default tolerance for a PO to be matched is 5% and this is set, then any PO received and matched will be automatically processed if the total PO value falls within this limit.
•	Setting the Default Review AP Group Prefix and Default Matched AP Group Prefix will put the value in front of the AP group during the AP Automation process – (<span style="color:blue">3</span>)

