---
title: User Guide
description: User Guide
published: true
date: 2024-01-19T15:07:49.983Z
tags: 
editor: markdown
dateCreated: 2023-12-07T10:11:13.800Z
---

[Simple Stock Take Menu](/Apps/simplestocktake)

# Stock Take Process Guide

Once all the setup steps have been completed you can start performing Stock Take operations following this user Guide.

### Count Selection

Navigate to Menu – GHA Modifications – Simple Stock Take – General Operations – Count Selection
![stocktake_7.png](/simplestocktake/stocktake_7.png)
Count Selection will show you Warehouse(s) / Bin(s) which are:
1.	Due
2.	Overdue
3.	Other (everything else, each row specifies a relevant Status):
a.	Counting	- Currently being counted
b.	Excluded	- No Count Frequency can be determined for the bin
c.	Not Due	- Not currently due for counting
d.	Not Counted	- Bin has never been counted (no Last Counted Date)

Count Selection uses a calculated Due and Overdue date to determine which tab will show the bin. Click Refresh (<span style="color:blue">1</span>) to update the table results.

Due date is based on the Last Counted date and Count Frequency assigned to the Warehouse Bin. If either is not specified, no Due date is calculated (the Warehouse Bin will never be Due or Overdue).

The Overdue date is calculated based on a parameterised number of weeks from the calculated Due date (Count Parameters – Due Weeks). 

Note: 	Count Selection will adjust the Calculated Due and Overdue date to ensure they are Working Days. This only occurs if a valid Production Calendar is entered.

### Starting A Count

To start a Count, select some Warehouse Bin(s) in one of the Count Selection tabs and choose Start Count from the Actions Menu:
![stocktake_8.png](/simplestocktake/stocktake_8.png)
Note: 	You will not be able to start a Count for any Warehouse Bin which exists in an Open Count.

The Start Count screen will appear:
![stocktake_9.png](/simplestocktake/stocktake_9.png)
A unique Count ID is generated automatically based on the current date. It can be overridden if required but will be validated unique before a Count can be started.

Press OK to start the Count.
If a Count was started, the Warehouse Bin Count Report screen will appear if there are any items (Parts) in any of the Warehouse Bin(s) to be Counted:
![stocktake_10.png](/simplestocktake/stocktake_10.png)
Note: 	The Warehouse Bin Count Report screen will not appear if all 
Warehouse Bin(s) specified the Manual Counting flag (Warehouse Bin) 
as these will be added manually. 

This Warehouse Bin Count Report allows you to physically print or preview the Count 
(or simply close the screen). 

Note: 	The Warehouse Bin Count Report can also be run from the menu at any time.

An example of the Report is shown below:
![stocktake_18.png](/simplestocktake/stocktake_18.png)
Note: 	The BAQ Report which is launched and whether On Hand quantity is shown or not is controlled by parameters (Count Parameters – Count Report section).
The report also shows the PCID if any.

### Full Stock Take

A Full Physical stock take is possible as long as there are no other stock takes taking part in the Warehouse you want to count. All Warehouses are selected by default, however, specific Warehouses can be selected on the Warehouse tab.
![stocktake_19.png](/simplestocktake/stocktake_19.png)
![stocktake_20.png](/simplestocktake/stocktake_20.png)

### Count Processing/History

The Count Processing screen is where a user will enter/review the results of a Count:
![stocktake_11.png](/simplestocktake/stocktake_11.png)
Search for and select a Count ID to see all the Warehouse(s) / Bin(s) which are either Open (Counting) or Closed (Processed or Cancelled) on the relevant tab.

If an Open Warehouse / Bin is selected:

1.	Any Transactions for the Part(s) affecting inventory in to or out of the Warehouse Bin since the Count was started can be optionally retrieved on the relevant tab.

Note: 	This is useful to review whether inventory levels might have changed following your physical count.
	This Transactions grid works on a BAQ which is configurable (Count Parameters – Count Activity BAQ).


2.	Part(s) in the Bin will be shown on the relevant Open Parts tab (Counting) or Closed Parts tab (Processed).

Note: 	On Hand and Variance quantity are optionally shown based on a parameter.
	Estimated Cost and Variance cost are optionally shown based on parameters.
(Count Parameters – Count Processing section)

### Entering A Count Quantity

Choose a Part in the Open parts tab and enter a Count Quantity. This marks the Part as being Entered. If you wish to count zero quantity, tick the Entered checkbox manually.

Reason code will optionally default based on a parameter (Count Parameters – Count Processing section), otherwise, you must select a valid Reason Code from the list.

Note: 	Valid Reason Codes are marked as “Count Discrepancy Reason” with a Reason Type of “Inv. Adjustment”.
	Serialised items do not get Quantity Adjusted, therefore a Reason Code does not default.

When a Part has been Entered:

1.	The On Hand value is captured and is not subsequently updated unless the Part is marked not Entered and then Entered again. 
a.	On Hand compared to Count Quantity determines the Adjustment Quantity which can be positive or negative.

2.	The End Date / Time of the Part is updated.

When a Part has been Entered, it will become Processed when you Submit Results. 

### Skipping Parts

Choose a Part in the Open parts tab and tick the Skip checkbox.

Note: 	No Quantity Adjustment will occur for Parts which are marked as Skip.

If the Part has not been Entered, the End Date / Time of the Part is updated.

When a Part is marked as Skip, it will become Processed when you Submit Results.

### Adding A Part

If a Part physically exists in a Warehouse Bin on your count but it does not exist in inventory within Epicor, you will need to add the Part to enter a Count Quantity. On the Count Processing screen select New Count Bin Part (<span style="color:blue">1</span>). This will open a line in the Open Parts section lower down In the Part box (<span style="color:blue">2</span>) type the part code or right click then Open With – Part Search and find the part you need to add. Select the part and add the quantity (<span style="color:blue">3</span>).
![stocktake_17.png](/simplestocktake/stocktake_17.png)
Note:	If the Part is Lot Tracked or Tracking multiple UOMs, you will need to specify any relevant Lot / UOM information. 
Parts which have been added can be deleted before they have been Processed which only occurs when you Submit Results.
The Count screen will honour the standard rules for PCID.

### Submitting Results

This Submit Results button acts on result(s) that have been entered i.e. Parts in the Open Warehouse / Bin that have been Entered or Skipped.

Note: 	Results that have been entered are always saved but are not actioned until 
Submit Results occurs.

1.	If the Part is marked as Skip:
a.	No Quantity Adjustment occurs.
b.	The Part is Closed and the Status changes to Processed.

2.	If the Part has been Entered:
a.	The Adjustment Quantity determines whether a Quantity Adjustment is necessary and if it is:
&nbsp;&nbsp;&nbsp;&nbsp;i.	The Reason Code that was specified is used for the adjustment.
&nbsp;&nbsp;&nbsp;&nbsp;ii.	The Part is marked with the Adjusted flag.
b.	The Part is Closed and the Status changes to Processed.

3.	If a Part has not been Entered or marked as Skip, it is considered incomplete and will not be processed:
a.	It will remain Open with a Status of Counting.

4.	Once all Parts are Closed (have been processed):
a.	The Warehouse / Bin is Closed and the Status changes to Processed.
b.	The Last Counted date/time of the Warehouse Bin is updated.

5.	Once all Warehouse(s) / Bin(s) are Closed (have been processed):
a.	The Count is Closed and the Status changes to Processed.

If required, you can enter results for all Warehouse(s) / Bin(s) and then submit them for the entire Count by selecting the Actions -> Count -> Submit Results.

Note: 	Once a Part, Warehouse / Bin or Count has been Closed, it is no longer amendable (with the exception of the Comment field).

### Cancelling

Sometimes it may be necessary to Cancel a Warehouse / Bin or the entire Count and options are available under the Actions menu:
![stocktake_12.png](/simplestocktake/stocktake_12.png)
Cancelling only affects Open records.

It is a way to Close a Warehouse / Bin and all Parts in the Warehouses / Bin without taking any further action.

Note: 	No Quantity Adjustment occurs.
The Last Counted date/time of the Warehouse Bin will not be updated.

When a Warehouse / Bin is cancelled:

1.	All Open Parts in the Warehouse / Bin are Closed and the Status becomes Cancelled:
a.	The End Date / Time of the Part is updated.

Note: 	If a Part was already Processed i.e. it was already Closed, it remains “as was” and the Status does not become Cancelled.

2.	The Warehouse / Bin is Closed:
a.	If all Parts in the Warehouse / Bin are Cancelled:
&nbsp;&nbsp;&nbsp;&nbsp;i.	The Status of the Warehouse / Bin is Cancelled.
b.	Otherwise, the Status of the Warehouse / Bin is Processed:
&nbsp;&nbsp;&nbsp;&nbsp;i.	This is to indicate that some actions may have occurred prior to cancellation.
 
3.	If there are no more Open Warehouse(s) / Bin(s):
a.	The Count is Closed.
b.	If all Warehouse(s) / Bin(s) are Cancelled:
&nbsp;&nbsp;&nbsp;&nbsp;i.	The Status of the Count is Cancelled.
c.	Otherwise, the Status of the Count is Processed.
&nbsp;&nbsp;&nbsp;&nbsp;i.	This is to indicate that some actions may have occurred prior to cancellation.

If a Count is cancelled, the actions are the same as above for each Open Warehouse / Bin in the Count.

### Comments

Comments can be added or updated against the Count, Warehouse / Bin or Part at any time, including when the record is Closed.

### Counting "on the fly"

You do not need to use 3.1 Count Selection to Start a Count:
![stocktake_13.png](/simplestocktake/stocktake_13.png)
You can choose any option from the New button within Count Processing to add a Count, Bin or Part “on the fly”.
 
If you select New Count - the Start Count screen will appear:
![stocktake_9.png](/simplestocktake/stocktake_9.png)
A unique Count ID is generated automatically based on the current date. It can be overridden if required but will be validated unique before a Count can be started.

Press OK to start the Count.

If you select New Count Bin, you will need to choose a Warehouse and Bin in the Open Warehouse / Bin grid.

Note: 	You will not be able to start a Count for any Warehouse Bin which exists in an Open Count.

Selecting New Count Bin Part is the same as the process described in 3.2.3 Adding a Part.

Once you have added all the Warehouse Bin(s) / Part(s) that you want to count, you can launch the Warehouse Bin Count Report via the Actions menu:
![stocktake_14.png](/simplestocktake/stocktake_14.png)
Note: 	This uses the same parameters as described in 3.1 Count Selection.

### Approval

If any of the counted parts fall outside of the approval limits, they will appear in the Count Approval screen.
![stocktake_21.png](/simplestocktake/stocktake_21.png)
From here the count can be accepted, rejected or sent for recount.
![stocktake_22.png](/simplestocktake/stocktake_22.png)
Approved – this will post the count as it was entered.
Recount – this will create a new count and make it as a recount
Rejected – this will reject the count and no adjustment will be made.

Note: 	This grid works on a BAQ which is configurable (Count Parameters – Count Approval BAQ).
Note: 	The approver will need to have Stock Take Approval and Sales Admin authorised in their User Account Security profile.

### Count Part Variance

![stocktake_15.png](/simplestocktake/stocktake_15.png)
Count Part Variance allows you to retrieve Open or Closed Count information for any combination of: Count ID, Part, Warehouse, Bin, Closed From / To.
Search and select the Count ID you want to review. Click the Refresh icon to show the details.

As a summary it provides full and detailed information of a Part across Count(s) including:

1.	Count / User / Warehouse / Bin / (Count) Start and End date
2.	Part / Lot / Serial / UOM / Completed (date) / Added / Entered / Skipped / Discrepancy / Adjusted / Reason
3.	Variance Quantity / Estimated Cost / Variance % (of On Hand)
4.	Adjusted Quantity / Actual Cost / Actual Variance Cost
5.	(Part) Comment / Status / Closed (date) / Class / Product Group

Combined with Epicor’s Group By and Summaries feature (on grids), this will allow you to determine cost and quantity information for any number of different combinations.

Note: 	This screen could be used to determine variance all the stock take parameters are entered into the set up page of the GHA Parameter screen. This grid works on a BAQ which is configurable (Count Parameters – Count Analysis section).

### Count Bin Summary/History

![stocktake_16.png](/simplestocktake/stocktake_16.png)
Count Bin Summary / History allows you to retrieve Closed Count information for any combination of: Count ID, Warehouse, Bin, Closed From / To.

The Count Bin Summary (top grid) provides summary information on Bin(s) across Count(s):

1.	How many times the Bin was Counted / Cancelled
2.	How many times a Count was Early / Late / On Time / Other (for example excluded Bins)
3.	How many items (Parts) were Counted / OK (no Discrepancy) / Discrepant / Skipped / Cancelled 
4.	The Average Variance %
5.	The Total Adjustment Actual Cost / Total Variance Cost

Based on information in the Count Bin Summary (top grid), a user may want to “drill down” into the detail of a Bin.

By selecting a row in the Count Bin Summary and then pressing the Retrieve button, Count Bin History information (bottom grid) is retrieved (specific to each Count shown):

1.	Count / User / Start / End / Comment / Early / Late / On Time / Other / Closed / Due / Overdue (dates) / Bin Status / Bin Comment
2.	How many items (Parts) were Counted / OK / Discrepant / Skipped / Cancelled
3.	The Average Variance %
4.	The Total Adjustment Actual Cost / Total Variance Cost

Based on information in the Count Bin History (bottom grid), a user may want to see details of a particular Count / Bin, in which case they should run 3.1 Count Part Variance

Note: 	The grids work on BAQs which are configurable (1.1 Count Parameters – Count Analysis section).

