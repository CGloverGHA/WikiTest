---
title: Landmark Backup Process
description: 
published: true
date: 2024-03-12T15:14:50.747Z
tags: 
editor: markdown
dateCreated: 2024-03-12T15:12:36.924Z
---

# GHA Landmark Off-Site Backup Process

*Date of issue: 15/02/2024*
 
Prepared by: 
Charlie Glover

## Introduction
This document contains a quick run through of the process that takes place when swapping out the backup drives. As of today, we have 2 external 2TB drives that are swapped over on a Thursday and taken off-site. 


## Backup Infastructure
The SQL Databases are being backed up incrementally every 20 mins and are located on the GHAUKFS.  
Backups of GHAUKDEV-dev-01& GHAUKDEV-Dev-Core-01 are taken at 22:00pm. A copy of the backups is transferred to the external drives at 6:00am the following morning. A backup of the DC and virtual machines are included in this backup as seen in the image below. 

![lmbackup1.png](/technical-documentation/lmbackup1.png)

## Step-by-step Instructions
Follow these steps to ensure that the backup process is done correctly. As of today, the day in which these drives are swapped over is Thursday. It is important to ensure that the drives are not being swapped over on any other day. 

Step 1.) Connect to the host (Dev server) and open the Veeam console. Press “Connect” when the pop up appears.

![lmbackup2.png](/technical-documentation/lmbackup2.png)
  

Step 2.) Ensure that all the jobs have been successfully completed. 

![lmbackup3.png](/technical-documentation/lmbackup3.png)

Step 3.) Swap the external drives. Then check that the Drive has been assigned the letter D: and that the drive is unlocked.

*IF THE DRIVE LETTER IS NOT D: PLEASE SCROLL TO THE BOTTOM OF THIS PAGE TO FIND INSTRUCTIONS ON HOW TO CHANGE THE DRIVE LETTER BACK TO D:*

![lmbackup4.png](/technical-documentation/lmbackup4.png)

 Step 4.) Head back to the Veeam console and click “Backup Infrastructure.”
 
 ![lmbackup5.png](/technical-documentation/lmbackup5.png)

 
 Step 5.) Click the “Backup repository” on the left hand side of the screen. 
 
![lmbackup7.png](/technical-documentation/lmbackup7.png)

Step 6.) The USB Repository should be listed. 

![lmbackup8.png](/technical-documentation/lmbackup8.png)

 
 Step 7.) Open file explorer -> locate the D: drive -> Double click the drive -> Enter the backups folder -> Permanently delete anything inside. 
 
 ![lmbackup9.png](/technical-documentation/lmbackup9.png)

 
Step 8.) Head back into the Veeam Repositories screen that you was previously on. 

 ![lmbackup10.png](/technical-documentation/lmbackup10.png)

Step 9.) Right click the “GHAUKHVD01-BACK2USB” Repository and click “Properties” 

 ![lmbackup11.png](/technical-documentation/lmbackup11.png)
 
Step 10.) Once properties is open, click “Review” on the left hand side. 

![lmbackup12.png](/technical-documentation/lmbackup12.png)

Step 11.) Click the check box at the bottom of the screen and click “Apply.” Once applied click “Finish” 

![lmbackup13.png](/technical-documentation/lmbackup13.png)
 
This process is now complete, and these exact steps should be taken on the following Thursday. 	

Changing Drive Letter to D: 

Step 1.) Right click the windows icon and click “Disk Management” 

 ![lmbackup14.png](/technical-documentation/lmbackup14.png)

Step 2.) Locate the USB drive and right click, then click “ Change drive letters and paths. 
  
![lmbackup15.png](/technical-documentation/lmbackup15.png)

Step 3.) Click “Change”

 ![lmbackup16.png](/technical-documentation/lmbackup16.png)

Step 4.) On the drop-down list select “D:” and press “ok” 

![lmbackup17.png](/technical-documentation/lmbackup17.png)  

