---
title: Client Installer Guide
description: 
published: true
date: 2024-03-13T12:22:02.479Z
tags: 
editor: markdown
dateCreated: 2024-03-13T11:34:56.705Z
---

# Client Installer Guide
 
*Prepared by: 
Charlie Glover*

## Introduction
This document will explain the client installer program that has been created to help install multiple environments in one instance. The environment version and name are to be stated within the config, for the correct ones to be downloaded. The location of the download can also be specified within the code. 

## Stages of the Installer Application

1st) The installer creates the client install folder and creates a subfolder under the install folder i.e C:\Epicor with the name of the environment.

2nd It then sets the permissions on the folder to allow authenticated users to modify the client install folder and subfolders and files to allow updates. 
3rd Next, downloads the release client, updates and mods zips to a temporary folder and extracts them to the client folder.
4th Creates an Epicor folder on the desktop and creates the relevant shortcuts. 

## Configuration
There are 3 sections that can be changed within the config in order to manipulate the location of the install, the version and the environment name. 

Step 1.) The “value=”C:\Epicor” is where you can change the location. “C:\Epicor”  can be modified to your own liking, the environments will be installed there. 

![installer1.png](/technical-documentation/installer1.png)
 

Step 2.) The root for where the deployment folders are held should be entered here. This varies from On-premise customers and hosted customers. As seen below, on-prem customers will use the naming conventions for the server running the Epicor App servers.  

 ![installer2.png](/technical-documentation/installer2.png)

Step 3.) This section will clean up temporary files. If you want to remove temporary files after install, keep the value “True” if you want to keep the temporary files set the value to “False”
  
![installer3.png](/technical-documentation/installer3.png)

Step 4.) This is where you can set the environments you would like to install. 
“erpVersion” is where you specify the version that the environments are running. (For on-prem, use the UNC. E.g ERP11.2.300.0Deployment.) If you want to install multiple environments that are running different versions, use a different line for each version as seen in the image below. 
“erpEnvironments” Is the name of the environment itself. For multiple environments, separate the names with “,” as seen in the image below. 

“addSkipToShortcut”  - If you would like to skip updated on launch, this will add the function to the shortcut. Simple enter =”True” 
“addShortcutPrefix” – You can add a prefix to the shortcut. Simply enter the desired prefix within the “”. If you do not require a prefix, then leave it blank

Enter your required environment information into the gaps following the breakdowns above. 

![installer4.png](/technical-documentation/installer4.png)
.  
NOTE: Ensure you save the config after you have entered your desired configuration.
“File -> Save”

## Installer
The installer is a separate exe that will run and install your environments. This will run directly from the configuration you have entered into the config file. 

Step 1.) Double click the application file. A pop up will appear, click “Yes” 

![installer5.png](/technical-documentation/installer5.png)
 
Step 2.) A Microsoft defender pop-up will appear. Click “More Info” 
 
![installer6.png](/technical-documentation/installer6.png)

Step 3.) Click “Run anyway” 
 
 ![installer7.png](/technical-documentation/installer7.png)

Step 4.) When the installer appears, click “Install.” 

![installer8.png](/technical-documentation/installer8.png)
 
Step 5.) The installer will run, showing the logs for the download.

Step 6.) The environments will be in the location you have set in the config. As you can see in the image below, the environments that I stated within the config have each been installed. The shortcuts that are created will look something like this. The “_____” will be filled with your customer number. 

![installer9.png](/technical-documentation/installer9.png)
 

NOTE: Epicor 10 –Data Collection Non classic will not work. This is due to it not existing in Epicor 10 and only being available in Kinetic. 

