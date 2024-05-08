---
title: System Set Up
description: System Set Up
published: true
date: 2024-01-19T15:07:45.949Z
tags: 
editor: markdown
dateCreated: 2023-12-07T10:10:18.351Z
---

[Simple Stock Take Menu](/Apps/simplestocktake)

# System Set Up

These steps need to be taken in the GHA Modifications section within the Epicor application.

### Count Parameters

To access the initial Parameters go to Menu – GHA Modifications – Parameters – Setup – Parameter Maintenance.
Then on the Stock Take tab please match all details as per below.
![stocktake_1.png](/simplestocktake/stocktake_1.png)

These parameters will be referred to within relevant sections of the guide.

Note: 	Where a parameter can be made not Active, this implies that any related function does not apply i.e. will not occur.

### Count Approval
Please navigate to Menu – GHA Modifications – Simple Stock Take – Setup – Approval Matrix Maintenance.
![stocktake_2.png](/simplestocktake/stocktake_2.png)
The count approval matrix allows you to set approval limits at a Part, Part Class, Product Group or Site level.  The amount that needs approving can be set at a percentage of the quantity, a monetary value, or the combination of both. Unless you need to specify something generally just use a matrix set on your main site.

For example, 5% of the quantity up to the value of £1000. This will allow you to adjust up to 5% of the quantity as long as the total adjustment is under £1000.

Should you require just a monetary value, the percentage can be set to 100%, if you require just a percentage value, the Variance Cost can be set to a number large enough to cover the stock value.

To create a new matrix, select New (<span style="color:blue">1</span>).
Enter an ID for the new matrix (<span style="color:blue">2</span>).
Enter the description of the new matrix (<span style="color:blue">3</span>).
Enter the percentage allowed for approval (<span style="color:blue">4</span>).
Enter the value allowed for the approval (<span style="color:blue">5</span>).
Select the relevant Approval group (<span style="color:blue">6</span>).
In the Approval Links (<span style="color:blue">7</span>) select the tab for the Site/Product Group/Part Class/Part you want this matrix to apply to. This will mainly be by Site.
Click save (<span style="color:blue">8</span>).

The Approval Group is the security group which allows approval or rejection of the count. These are created in Security Group Maintenance.

### Count Frequency
Navigate to Menu – GHA Modifications – Simple Stock Take – Setup – Count Frequency
![stocktake_3.png](/simplestocktake/stocktake_3.png)
Setup Count Frequency(s) to determine how often you will count. The Count Frequency can then be attached to a Warehouse Bin to denote how often you count a bin. 

To add a new frequency, select New (<span style="color:blue">1</span>).
Enter the new frequency ID (<span style="color:blue">2</span>).
Enter the description (<span style="color:blue">3</span>).
Enter the frequency value (<span style="color:blue">4</span>).
Enter the frequency multiplier (<span style="color:blue">5</span>).
Click save (<span style="color:blue">6</span>).

### Count Group
Navigate to Menu – GHS Modifications – Simple Stock Take – Setup – Count Group
![stocktake_4.png](/simplestocktake/stocktake_4.png)
Setup Count Group(s) which specify a Count Frequency. The Count Group determines the frequency for a specified location at your site.

To create a new Group select New (<span style="color:blue">1</span>).
Enter the Group ID (<span style="color:blue">2</span>).
Enter the description for the group (<span style="color:blue">3</span>).
Select the frequency you want (<span style="color:blue">4</span>). This is the frequency set up in Count Frequency.
Click Save (<span style="color:blue">5</span>).

A Count Group can be attached to a Warehouse Bin to denote how often you count a bin. 
Note: 	The benefit of attaching a Count Group to a Warehouse Bin is that you can change the Count Frequency of a Count Group without having to update Warehouse Bin(s) which are using it.

### Warehouse Bin
Navigate to Menu – GHA Modifications – Simple Stock take – Setup – Warehouse Bin
![stocktake_5.png](/simplestocktake/stocktake_5.png)
Use the warehouse drop down and Bin search to find the warehouse bin you want to review.

The Last Counted date and Time indicates when the bin was last counted and is not amendable.

Count Group and/or Count Frequency can be attached to a Warehouse Bin to denote how often you count a bin.

If both a Group and Frequency have been attached, the Frequency takes precedence.

Count Due Date can be amended to set a date for a previously uncounted Bin or to manually modify the next time the Bin requires counting.

Note:	You are still able to count a bin without either Group or Frequency attached. In such cases, the bin will never become due for counting automatically, it will have to be manually selected. 

If Manual Counting is specified, when a Count is Started for the Bin (3.1 Count Selection), the items (Parts) in the Bin are not added to the Count automatically – they need to be Added manually (3.2 Count Processing / History).

### Count Capacity
Navigate to Menu – GHA Modifications – Simple Stock Take – General Operations – Count Capacity
![stocktake_6.png](/simplestocktake/stocktake_6.png)
Once you have finished defining Count Frequency(s) and Group(s) and have attached these to Warehouse Bin(s), you are ready to review your configuration.

Count Capacity allows you to verify your configuration by calculating the count demand for all Warehouse(s) / Bin(s) which specify a Count Group or Frequency in the Site. Click Refresh (<span style="color:blue">1</span>) to update the Capacity details.

This allows you to determine if the count demand (based on your configuration) is too high or too low and therefore whether you may need to make changes to your configuration.
A Production Calendar must be chosen before the Count Capacity calculation can be run.

A Calendar can be marked as Default, meaning it will be remembered the next time you open the Count Capacity calculation (1.1 Count Parameters – Default Calendar).

If no Default Calendar has been defined, the Calendar will default from the Site and if not defined there then the Company, otherwise a Calendar must be chosen manually.

[Simple Stock Take Menu](/Apps/simplestocktake)


