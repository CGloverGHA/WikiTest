---
title: Mod Install Guide
description: 
published: true
date: 2024-03-13T13:28:57.390Z
tags: 
editor: markdown
dateCreated: 2024-03-13T13:28:55.237Z
---

# GHA Mod Install Guide


## Introduction

This document demonstrates how to install new GHA mods and CAB files. It also includes a step-by-step tutorial on how to install client side mods (configuring automatic updates and running MetaUI migration). 

## Installing New GHA Mods
This is a step-by-step tutorial for dummies on how to install cabs with screenshots. This run through demonstrates how to install MIMS. However they are very similat steps on how to install other mods such as MFS and Parameters
 
Step 1.) For best practices, download the new cabs to the correct environments "MODS" folder located on GHAUKFS01.
You can do this by installing the files on the actual server from the wiki and copying them over to the GHAUKFS01 share.
  
Step 2.) Enter the correct environment that the CAB files need to be installed on. Do GHUKAPP03 First.
  
Step 3.) Open the Solution workbench when in the correct environment. 
  
Step 4.) First, we need to install the mobile fields.  Click "Actions" then click "Install solution”. 
  
Step 5.) Click " Solution File" then browse to the Mobile Fields CAB file first. 
 
Step 6.) Check the following boxes then install. 
 
•	"Delete previous install”.
•	"Automatically override duplicate data" 
  
Step 7.) We need to regen the DB. On the server which houses the Epicor you're working on, open the Epicor administration console. 
  
Step 8.) Browse to the DB for the environment under the "Database server manager”. 
  
Step 9.) Right click on the Database and click "Regenerate data model" and press "Generate”. 
  

Step 10.) Browse to the environment under "Server Management”. 
 
Step 11.) Right click the environment and press "Recycle Application Pool”. 
  
Step 12.) We now need to install the parameters. Download the Parameters CAB file. 
 
Step 13.) Open the Solution workbench when in the correct environment.  
 
Step 14.) Click "Actions" then click "Install solution”. 
  
Step 15.) Click " Solution File" then browse to the Parameters CAB file. 
 
Step 16.) Check the following boxes then install. 
 
•	"Delete previous install”.
•	"Remove Directives with matching name”.
•	"Automatically override duplicate data" 
•	"Automatically override duplicate files"
  
Step 17.) Click "Actions" then click "Install solution”. 
  
Step 18.) Click " Solution File" then browse to the MIMS CAB file.
  
Step 19.) Check the following boxes for MIMS. 
 
•	"Only Target Current Company"
•	" Remove Directives with matching name”.
•	"Delete Previous Installs" 
•	"Automatically overwrite duplicate files"
•	"Automatically overwrite duplicate data"
 
 Step 20.) Click Install 
 

## Client-Side Mods
For the client-side mods (E.g. Procurement Dashboards) – For example this one is being installed on K20222SIPilot, where this environment is mentioned, replace this with the required location. 
 
Step 1.) Install the new CAB file in the solution workbench. 
-Automatically overwrite, remove matching names. Change the directory for the install to the      ERP.

Step 2.) Copy the new mod to the desktop of the server or any local space. The new mod should be located in the “GHAModsGeneral” shared storage.
 
Step 3.) Head to web server directory -> inetpub -> wwwroot -> K20222SIPilot -> Client (This environment is on DV01) 
 
 ![modinstall1.png](/technical-documentation/modinstall1.png)
 
Step 4.) Copy this to the Epicor client deployment folder and paste the file into this location. Data(D:) -> Epicor -> ERP11 -> ERP11.2.200.2 -> ClientDeployment -> Custom -> Client  

![modinstall2.png](/technical-documentation/modinstall2.png)
  
Step 5.) Head to this location Data(D:) -> Epicor -> ERP11 -> ERP11.2.2.200.0 -> ClientDeployment -> Client -> Config
 
 ![modinstall3.png](/technical-documentation/modinstall3.png)
 
Step 6.) Copy the automatic updates tag into both the configs shown above. (AutoK20222SIPilot & K20222SIPilot) The tag is found within the install guide given with the CAB file. Just copy and paste this line under the other customisation lines. 
 
 ![modinstall4.png](/technical-documentation/modinstall4.png)

Step 7.) Recycle the app pool within the Epicor administration console. 

![modinstall5.png](/technical-documentation/modinstall5.png)

Step 8.) Open the Epicor session and head to conversion workbench. 

![modinstall6.png](/technical-documentation/modinstall6.png)

Step 9.) Tick the 191 Meta UI conversion and then click actions and run pending 

![modinstall7.png](/technical-documentation/modinstall7.png)

Step 10.) Test that the new mods work. Both Dashboards should open

![modinstall8.png](/technical-documentation/modinstall8.png) 


