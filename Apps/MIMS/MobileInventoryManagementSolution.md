---
title: MIMS User Guide
description: MIMS user Guide
published: true
date: 2024-01-19T15:01:46.168Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:11:45.177Z
---

# Purpose
This is an informal document intended as an aide-memoire for the GHA Solutions and Site teams. The GHA Solutions team will record comments and recommendations when they occur during the project implementation. These may subsequently be revised, but it should not be assumed the details in the document are current. 
>NB *the screen shots in the following sections are displayed in an Outlook theme in Epicor. This is for display purposes and the functional screens with any Epicor theme work the same way, although the look will be different.*

# MIMS
The objective of these pages is to provide a user guide for the MIMS (Mobile Inventory Management System) application

**Contents**
---
&nbsp;&nbsp;&nbsp;&nbsp;[Configuration](#configuration)
&nbsp;&nbsp;&nbsp;&nbsp;[Warehouse](#h-31warehouse)
&nbsp;&nbsp;&nbsp;&nbsp;[Employee](#h-32employee)
[Main Application](#main-application)
&nbsp;&nbsp;&nbsp;&nbsp;[Screen Personalisation](#screen-personalisation)
&nbsp;&nbsp;&nbsp;&nbsp;[Main Menu](#main-menu)
&nbsp;&nbsp;&nbsp;&nbsp;[Stock Take](#h-52stock-take)
&nbsp;&nbsp;&nbsp;&nbsp;[Bin Enquiry](#h-53-bin-enquiry)
&nbsp;&nbsp;&nbsp;&nbsp;[Part Enquiry](#h-54-part-enquiry)
&nbsp;&nbsp;&nbsp;&nbsp;[Add & Issue part](#h-55-add-issue-parts)
&nbsp;&nbsp;&nbsp;&nbsp;[Move Stock](#h-56-move-stock)
&nbsp;&nbsp;&nbsp;&nbsp;[Job Picking](#h-57-job-picking)
&nbsp;&nbsp;&nbsp;&nbsp;[Job Returns](#h-58-job-returns)
&nbsp;&nbsp;&nbsp;&nbsp;[Job Receipts](#h-59-job-receipts)
&nbsp;&nbsp;&nbsp;&nbsp;[Order Picking](#h-510-order-picking)
&nbsp;&nbsp;&nbsp;&nbsp;[Tracking Number](#h-511-tracking-number)
&nbsp;&nbsp;&nbsp;&nbsp;[Reprint Labels](#h-512-reprint-labels)
&nbsp;&nbsp;&nbsp;&nbsp;[Goods In](#h-513-goods-in)
&nbsp;&nbsp;&nbsp;&nbsp;[NCR’s](#h-514-ncrs)
&nbsp;&nbsp;&nbsp;&nbsp;[Kanban Receipts](#h-515-bin-kanban-receipts)


# Configuration
 
MIMS configuration is done on the Parameters page, this can be found in the GHA Modifications part of the menu.
![param-1.png](/mimsassets/param-1.png)
* Picking Options (<span style="color:blue">1</span>) is reserved for future functionality, currently only sequence pick is installed.
* Picking Type (<span style="color:blue">2</span>), this allows the user to select how the orders for picking appear on the Picking Dashboard
* Dashboard Driven Picking (<span style="color:blue">3</span>), this is the default setting and picks will only appear if orders are sent to the employee, unticking this box will allow the user to select any order (this is reserved for future functionality)
* Display next Pick Only (<span style="color:blue">4</span>) this will only show the employee one line to pick.
* Default Report type (<span style="color:blue">5</span>) this will define the report style used for Order Picking
* Shipment Type (<span style="color:blue">6</span>), this will define how a customer shipment is created, Ship Complete, will mark the Pak as shipped, DO Not Ship Complete, will not mark the pack as shipped, Stage is reserved for future functionality.
* Material Queue (<span style="color:blue">7</span>) is reserved for future functionality
* Putaway (<span style="color:blue">8</span>) is reserved for future functionality
* Staging Options (<span style="color:blue">9</span>) is reserved for future functionality
* Force Scan of Receipt Location (<span style="color:blue">10</span>) will force the employee to scan the location of the Po Receipt
* Use Primary Bin as Default (<span style="color:blue">11</span>) will suggest the Primary Bin for receiving goods
* Default Report Style (<span style="color:blue">12</span>) this will define the report style used for the PO receipt
* Default Report Style (<span style="color:blue">13</span>) this will define the report style used for the RMA receipt 
* Force Scan of Receipt Location (<span style="color:blue">14</span>) will force the employee to scan the location of the Job receipts 
* Default Report Style (<span style="color:blue">15</span>) this will define the report style used for the Job receipt to stock
* Default Report Style (<span style="color:blue">16</span>) this will define the report style used for the Job-to-Job receipt
* Force Scan of Receipt Location (<span style="color:blue">17</span>) will force the employee to scan the location of the stock inventory transfer
* Default Report Style (<span style="color:blue">18</span>) this will define the report style used for the Inventory transfer movement
* Force Scan of Receipt Location (<span style="color:blue">19</span>) will force the employee to scan the location of the Kanban receipt
* Default Report Style (<span style="color:blue">20</span>) this will define the report style used for the Kanban receipt
* Force Scan of Receipt Location (<span style="color:blue">21</span>) will force the employee to scan the location of the Nonconformance
* Default Report Style (<span style="color:blue">22</span>) this will define the report style used for the Nonconformance
* Stored Image Settings (<span style="color:blue">23</span>) this is reserved for future functionality

## 3.1	Warehouse
 ![warehouse_picture1.png](/mimsassets/warehouse_picture1.png)
On the warehouse entry screen navigate to the GHA tab (<span style="color:blue">1</span>) and select the checkbox to indicate that the warehouse selected will be used as a picking location (<span style="color:blue">2</span>). Picking sequence (<span style="color:blue">3</span>) is reserved for future functionality.

## 3.2	Employee
 
On the employee record select the  Integration tab (<span style="color:blue">1</span>), then the GHA tab (<span style="color:blue">2</span>). Enter a Pin code(<span style="color:blue">3</span>) should you want the employee to utilize one. The sites field (<span style="color:blue">4</span>) is to restrict the sites the employee can work in. This is a tilde delimited list, if there is only one site, this can be left blank.
The buttons on the MIMS screen available to the employee are decided by the following matrix.
 ![employee_picture2.png](/mimsassets/employee_picture2.png)


# Screen Personalisation

Personalisation
The menu layout on the MIMS application can be personalised by the user.
 
•	By pressing and holding one of the buttons, the button can then be moved around.

<video width="240" height="480" controls>
  <source src="/mimsassets/customise_home_page.mp4" type="video/mp4">
  </video>

# Main Application

## Main Menu
When logging on via the application, the user will be presented with the Log in screen.
![main_menu_picture3.png](/mimsassets/main_menu_picture3.png)
•	From the employee ID¸ select the required employee, enter the PIN no and Log in
•	If the employee is only assigned to one site in Epicor, this will be the default.  If more than one site has been assigned, site can be selected
 
•	The main MIMS menu will appear
![main_menu_picture4.png](/mimsassets/main_menu_picture4.png)
## 5.2	Stock Take

 
•	To undertake a stock count for a part, select Stock Take - see no.1 below
![stock_take_picture5.png](/mimsassets/stock_take_picture5.png)
•	In the Count field (see no.1 below) enter or select the count number and the select Start - see no.2
![stock_take_picture6.png](/mimsassets/stock_take_picture6.png)
•	The warehouse(s) assigned to the count will be displayed – see no.1 below.   Select Scan – see no.2 or select the warehouse
![stock_take_picture7.png](/mimsassets/stock_take_picture7.png)
•	The bin locations assigned to the count will be displayed – see no.1 below
•	Select the required bin
![stock_take_picture8.png](/mimsassets/stock_take_picture8.png) 
•	The part(s) in the bin will be displayed – see no.1 below
•	Select the part to be counted
![stock_take_picture9.png](/mimsassets/stock_take_picture9.png) 
•	If the part is lot tracked, the lot(s) in the bin location for the part selected will be displayed – see no.1 below
•	If the lot being counted is found in the bin but not showing, then there is an option to Add Lot – see no.2 below
![stock_take_picture10.png](/mimsassets/stock_take_picture10.png)
•	Once the part has been selected, the screen appears to allow quantities to be added.
•	Enter the quantity that has been counted – see no.1 below
•	There is an option to use a calculator by selecting the Calc button – see no.2.  whatever value is entered into the calculator will then be added into the quantity field
•	If the part is not to be counted, select Skip - see no.3
•	Once either the quantity has been entered, select enter – see no.4
![stock_take_picture11.png](/mimsassets/stock_take_picture11.png)
•	The Count Completed screen will appear – see no.1 below
•	Select Update - see no.2 below
![stock_take_picture12.png](/mimsassets/stock_take_picture12.png) 
•	Once all the part(s) in the bin have been counted, the message below appears – see no.1 below
![stock_take_picture13.png](/mimsassets/stock_take_picture13.png)
 •	If Close is selected this will display the screen below highlighting that the count was successful.
![stock_take_picture14.png](/mimsassets/stock_take_picture14.png)
•	If no more parts are added the screen below will display
•	Select OK - see no.1
![stock_take_picture15.png](/mimsassets/stock_take_picture15.png) 
•	If More Parts is selected below, the Select Part screen will reappear
![stock_take_picture16.png](/mimsassets/stock_take_picture16.png)

 
•	Enter or scan the new Part to be added to the count/bin – see no.1 below
•	Select - see no.2
![stock_take_picture17.png](/mimsassets/stock_take_picture17.png) 
•	A warning message will be displayed – see no.1 below
•	Select Yes
![stock_take_picture18.png](/mimsassets/stock_take_picture18.png) 
•	A message will display saying the part has been added – see no.1 below
![stock_take_picture19.png](/mimsassets/stock_take_picture19.png) 
•	Enter the quantity - see no.1 and then select Enter - see no.2 below
![stock_take_picture20.png](/mimsassets/stock_take_picture20.png) 
•	Select OK - see no.1 below
![stock_take_picture21.png](/mimsassets/stock_take_picture21.png)

## 5.3	 Bin Enquiry
 
•	To review what inventory items are in a stock location, use the Bin Enquiry function – see no.1 below
![bin_picture22.png](/mimsassets/bin_picture22.png) 
•	If the? icon is selected at the top of the screen below, the Scanning options for the relevant screen will be shown, e.g. bin enquiry, move stock.  If scanning on any function, the system will automatically determine which bar code relates to each piece of required data based on the options available.
•	Scan or enter the warehouse and bin – see no.1
•	Select - see no.2
![bin_picture23.png](/mimsassets/bin_picture23.png) 
•	All the parts available in the warehouse and bin selected will be displayed showing the on-hand quantities and Units of measure - see below
![bin_picture24.png](/mimsassets/bin_picture24.png)
## 5.4	 Part Enquiry
 
•	To review current stock levels of a part, select Part Enquiry - see no.1 below
![part_picture25.png](/mimsassets/part_picture25.png) 
•	Scan or enter the Part Number- see no.1 below
![part_picture26.png](/mimsassets/part_picture26.png) 
•	The current on hand quantities and stock locations will be displayed for the part selected - see below
![part_picture27.png](/mimsassets/part_picture27.png)
## 5.5	 Add & Issue Parts
 
•	To add & issue materials to a job, select Add/Issue Parts - see no.1 below
![add_picture28.png](/mimsassets/add_picture28.png) 
•	The next step is to Scan or enter the Job Number – see no.1 below and then press Select – see no.2
![add_picture29.png](/mimsassets/add_picture29.png)  
•	Scan or enter the part to be issued into Material Part Number – see no.1 below and then Select – see no.2
![add_picture30.png](/mimsassets/add_picture30.png) 
•	The current on hand stock locations for the material part selected are displayed as below
•	Select the location to be issued from (see no.1) and then Select – see no.2
![add_picture31.png](/mimsassets/add_picture31.png) 
•	Enter the Quantity to be issued – see no.1 below and then select Done – see no.2
![add_picture32.png](/mimsassets/add_picture32.png) 
•	A confirmation message will appear – select Ok – see no.1 below
![add_picture33.png](/mimsassets/add_picture33.png) 
•	An information message will appear asking if more parts are required to be issued – see no.1 below.  If No is selected, this will return to the main screen.  If Yes is selected, the Add/Issue Parts screen will appear again
![add_picture34.png](/mimsassets/add_picture34.png)
## 5.6	 Move Stock
 
•	To move stock from one location to another, select Move Stock - see no.1 below
![move_picture35.png](/mimsassets/move_picture35.png) 
•	Scan or enter Part Number to be moved – see no.1 below.
•	Select the Warehouse/bin that the stock is to be moved from (see no.2) and then Select - see no.3
![move_picture36.png](/mimsassets/move_picture36.png) 
•	The on-hand quantity will be displayed – see no.1 below
![move_picture37.png](/mimsassets/move_picture37.png) 
•	Enter the Quantity to be moved – see no.1 below
•	Select done - see no.2
![move_picture38.png](/mimsassets/move_picture38.png) 
•	Scan or enter the warehouse/bin for the new stock location – see no.1 below and then Select – see no.2 
![move_picture39.png](/mimsassets/move_picture39.png) 
•	Select Confirm – see no.1 below
![move_picture40.png](/mimsassets/move_picture40.png)
## 5.7	 Job Picking
 
•	To pick materials for a job, select Job Picking – see no.1 below
![job_pick_picture41.png](/mimsassets/job_pick_picture41.png)
•	Scan or enter the Job Number - see no.1 below and then Select- see no.2
![job_pick_picture42.png](/mimsassets/job_pick_picture42.png) 
•	The number of materials to be issued for the job are shown – see no.1 below
•	There are 2 options – pick for the entire job or for a selection linked to the operation of a job – see no.2
![job_pick_picture43.png](/mimsassets/job_pick_picture43.png) 
•	If 'Selection' was selected, then the screen will display:  Select Operation - see no.1 below
![job_pick_picture44.png](/mimsassets/job_pick_picture44.png) 
•	The materials to issue linked to the operation will be displayed – see no.1 below
•	Select or scan the part to issue – see no.2
![job_pick_picture45.png](/mimsassets/job_pick_picture45.png) 
•	The next step will be to enter the quantity to be issued – see no.1 below and then select Issue – see no.2
![job_pick_picture46.png](/mimsassets/job_pick_picture46.png) 
•	A confirmation message will be displayed – see no.1 below
![job_pick_picture47.png](/mimsassets/job_pick_picture47.png)
•	Repeat the previous steps for each part to be issued to the job
## 5.8	 Job Returns
 
•	To return materials to stock already issued to a job, select Job Returns - see no.1 below
![job_ret_picture48.png](/mimsassets/job_ret_picture48.png) 
•	Scan or enter the job Number – see no.1 below and then Select – see no.2
![job_ret_picture49.png](/mimsassets/job_ret_picture49.png) 
•	Depending on the requirement, the entire job materials or a selection can be made – see no.1 below.  Once a selection has been made, the Material to Return screen will display
![job_ret_picture50.png](/mimsassets/job_ret_picture50.png) 
•	The materials issued to the job will be displayed– see no.1 below
•	Once the material has been scanned or selected (see no.2), the location screen will appear
![job_ret_picture51.png](/mimsassets/job_ret_picture51.png) 
•	The Warehouse/bin that the part is being returned to will be displayed and this can be changed if required – see no.1 below
•	Select – see no.2
![job_ret_picture52.png](/mimsassets/job_ret_picture52.png) 
•	Enter the Quantity to be returned – see no.1 below and then select Return - see no.2
![job_ret_picture53.png](/mimsassets/job_ret_picture53.png) 
•	A confirmation message will be displayed – see no.1 below.  Select OK
![job_ret_picture54.png](/mimsassets/job_ret_picture54.png)
## 5.9	 Job Receipts
•	To receive a stock quantity for a job, select Job Receipts - see no.1 below
![job_rec_picture55.png](/mimsassets/job_rec_picture55.png) 
•	Scan or select the Job Number – see no.1 below and then Select - see no.2
![job_rec_picture56.png](/mimsassets/job_rec_picture56.png) 
•	Enter the Quantity to be received – see no.1 below
•	Select the warehouse/bin for the job receipt – see no.2 and then Select – see no.3
![job_rec_picture57.png](/mimsassets/job_rec_picture57.png) 
•	Select Perform Receipt – see no.1 below
![job_rec_picture58.png](/mimsassets/job_rec_picture58.png) 
•	A confirmation message will appear – select OK – see no.1 below
![job_rec_picture59.png](/mimsassets/job_rec_picture59.png) 
•	An option to print labels will appear - see no.1 below
![job_rec_picture60.png](/mimsassets/job_rec_picture60.png)
## 5.10	 Order Picking
In order to send Orders to be picked to the employee, they need to be selected on the dashboard.
 
The picking Sequence (1) is reserved for future functionality, to assign a pick, select the employee in the combobox (2) and save the record. The filters (3) can be used to minimize the dashboard results.

 
•	To pick a sales order, select Order Picking - see no.1 below
![order_picture61.png](/mimsassets/order_picture61.png) 
•	The part and quantity will be displayed along with the customer to be shipped to and the delivery method.  Select the order
![order_picture63.png](/mimsassets/order_picture63.png) 
•	Scan or select the order 
![order_picture64.png](/mimsassets/order_picture64.png) 
•	The order quantity is displayed – see no.1 below
•	Enter the Qty to Pick – see no.2.
•	If the Qty to Pick is equal to or greater than the Qty Req¸the Shipped Complete will automatically be selected – see no.3
&nbsp;&nbsp;&nbsp;&nbsp;-	If the order quantity being shipped is less than the quantity required, the remaining quantity will be placed on back order. 
&nbsp;&nbsp;&nbsp;&nbsp;-	If the remaining quantity is not being shipped, manually select the Shipped Complete check box
•	Select Pack ¬– see no.4
![order_picture65.png](/mimsassets/order_picture65.png) 
•	A confirmation message will appear.  Select OK - see no.1 below
![order_picture66.png](/mimsassets/order_picture66.png) 
•	If the packing is complete, select Finish Pack – see no.1 below.  If not, select the back arrow
![order_picture67.png](/mimsassets/order_picture67.png) 
•	If Finish Pack was selected, the Add Dimensions screen appears
![order_picture68.png](/mimsassets/order_picture68.png) 
•	Scan or select the Package Type - see no.1 below.  This is an optional step and is not required
•	Enter the Weight – see no.2
•	Select confirm – see no.3
![order_picture69.png](/mimsassets/order_picture69.png)
## 5.11	 Tracking Number
 
•	To assign a tracking number to a shipment, select Tracking Number - see no.1 below
![track_picture70.png](/mimsassets/track_picture70.png) 
•	Scan or select the pack Number - see no.1 below and then Select – see no. 2
![track_picture71.png](/mimsassets/track_picture71.png) 
•	Scan or enter the tracking Number – see no.1 below and then select Update - see no.2
![track_picture72.png](/mimsassets/track_picture72.png) 
•	A confirmation message will appear – select OK – see no.1 below
![track_picture73.png](/mimsassets/track_picture73.png)
## 5.12	 Reprint Labels
 
•	The Reprint Labels function allows several label reprinting options – see no.1 below
![reprint_picture74.png](/mimsassets/reprint_picture74.png) 
•	To reprint select the appropriate option
![reprint_picture75.png](/mimsassets/reprint_picture75.png) 
•	To reprint Pack Slip, select the option. Enter the Package Number and then select Reprint
![reprint_picture76.png](/mimsassets/reprint_picture76.png) 
•	To reprint a Job Receipt, select the option. Scan or enter the job number and then Select
![reprint_picture77.png](/mimsassets/reprint_picture77.png) 
•	Depending on the job, select the appropriate option
![reprint_picture78.png](/mimsassets/reprint_picture78.png) 
•	Select the job
![reprint_picture79.png](/mimsassets/reprint_picture79.png) 
•	Select Print
 
•	To reprint a PO receipt, select the option. Enter the Packing slip Number, select and then Print
![order_picture80.png](/mimsassets/order_picture80.png) 
•	To reprint RMA receipts, select the option. Enter the RMA Number and then Print
![order_picture81.png](/mimsassets/order_picture81.png)
## 5.13	 Goods In
 
•	To enter a PO receipt or RMA receipt, select Goods In - see no.1 below
![goods_picture82.png](/mimsassets/goods_picture82.png)
•	Scan (see no.1 below) or enter the PO Number to be received (see no.2) and then select – see no.3.  If the PO number entered is the same as the RMA number, or vice versa, a message will appear asking for confirmation
![goods_picture83.png](/mimsassets/goods_picture83.png) 
•	The PO/lines to be received are shown.  Select the PO/line to be received
![goods_picture84.png](/mimsassets/goods_picture84.png)  
•	The Req Qty is shown – see no.1 below
•	Enter the Quantity being received – see no.2
•	If the quantity is equal to or greater than the Req Qty, the Release Complete check box is automatically selected – see no.3
o	If the quantity being received is less than the required quantity, the release complete check box is blank, and the remaining quantity will be left open pending another release.  If there are more receipts to be made (e.g., supplier has indicated that no more will be delivered) then the release complete check box can be manually selected.
•	Select receive - see no.4
![order_picture85.png](/mimsassets/order_picture85.png)
•	The next option is to print labels prior to the putaway.
•	Select the printer and the Quantity Per Container - see no.1 below.  The Quantity selected will dictate the number of labels printed e.g., if quantity of 50 is being received, and there are 10 per container, then 5 labels will be printed.
![goods_picture86.png](/mimsassets/goods_picture86.png)
•	Select the Warehouse/bin for the location the PO receipt is being received into (see no.1 below) and then select – see no.2 
![order_picture87.png](/mimsassets/order_picture87.png)
•	A confirmation message will appear and select OK - see no.1 below
![order_picture88.png](/mimsassets/order_picture88.png) 
•	If an RMA has been selected, this is shown on the screen.  Select the RMA
![goods_picture89.png](/mimsassets/goods_picture89.png) 
•	The RMA/line shows the part and return qty.  Select the line
![goods_picture90.png](/mimsassets/goods_picture90.png) 
•	Scan or select the Warehouse/bin that the returned material is being received into – see no.1 below and then Select – see no.2
![goods_picture91.png](/mimsassets/goods_picture91.png) 
•	The return Qty is shown – see no.1 below
•	Enter the quantity being returned – see no.2.
•	If the quantity being returned is the same as the return qty, the release Complete check box is automatically selected – see no.3
•	Select receive - see no.4
![goods_picture92.png](/mimsassets/goods_picture92.png) 
•	A confirmation message is displayed – select OK - see no.1 below
![goods_picture93.png](/mimsassets/goods_picture93.png)
## 5.14	 NCR's
 
•	To create a nonconformance for a stock item, select NCRs - see no.1 below
![ncr_picture94.png](/mimsassets/ncr_picture94.png) 
•	Scan or enter the Part number – see no.1 below and then Select – see no.2
![ncr_picture95.png](/mimsassets/ncr_picture95.png) 
•	Scan or enter the Warehouse/bin that the part is in – see no.1 below and then Select
![ncr_picture96.png](/mimsassets/ncr_picture96.png) 
•	Enter the reason for the NCR – see no.1 below
•	Enter the Quantity - see no.2
•	Select create - no. 3
![ncr_picture97.png](/mimsassets/ncr_picture97.png) 
•	A confirmation message will be displayed.  Select OK - see no.1 below
![ncr_picture98.png](/mimsassets/ncr_picture98.png)
## 5.15	 Kanban Receipts
 
•	To create a Kanban Receipt, select Kanban Receipts - see no.1 below
![kanban_picture99.png](/mimsassets/kanban_picture99.png) 
•	Scan or Enter the Part Number that the Kanban is for – see no.1 below and then Select – see no.2
![kanban_picture100.png](/mimsassets/kanban_picture100.png) 
•	Confirm the revision number (see no.1 below) and select – see no.2
![kanban_picture101.png](/mimsassets/kanban_picture101.png) 
•	Scan or enter the stock location in Warehouse/bin – see no.1 below and then Select - see no.2
![kanban_picture102.png](/mimsassets/kanban_picture102.png) 
•	Enter the production quantity in the Quantity field – see no.1 below and then select Create - see no.2
![kanban_picture103.png](/mimsassets/kanban_picture103.png) 
•	If the part being reported is serial tracked, the select Serials window will open.  Select Generate Serials - see no.1 below - and enter the number of serial numbers required.
![kanban_picture104.png](/mimsassets/kanban_picture104.png) 
•	If the part being produced is lot tracked, the Select Lot window will open.  Enter a lot number – see no.1 below or select Next Lot (see no.2) and then Select - see no.3
![kanban_picture105.png](/mimsassets/kanban_picture105.png) 
•	A confirmation message will appear.  Select  OK -  see no.1 below
![kanban_picture106.png](/mimsassets/kanban_picture106.png) 
•	An option to print a receipt tag/label is available
![kanban_picture107.png](/mimsassets/kanban_picture107.png)











