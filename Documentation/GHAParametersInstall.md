---
title: GHA Parameters Install
description: 
published: true
date: 2024-03-13T13:12:34.960Z
tags: 
editor: markdown
dateCreated: 2024-03-13T12:27:59.444Z
---

# GHA Parameters Install

## Installation of the GHA Params CAB

Step 1.) In Epicor open the ‘Solutions Workbench’ program

---
Step 2.) Under the ‘Actions’ menu click ’Install Solution’.

---
Step 3.) Click the ‘Solution File’ button and browse to the location of the CAB file
         o	GHA Params.cab
 
---

Step 4.) In the Deployment Folder, select your Application Server virtual directory, usually

![paraminstall1.png](/technical-documentation/paraminstall1.png)
 
---

Step 5.) Check ‘Remove Directives with Matching Name’
  
---

Step 6.) Select ‘Automatically overwrite duplicate files’ and ‘Automatically overwrite duplicate data’
  
---

Step 7.) Click Install
NOTE: Sometimes there will be an error with regards to an outdated directive. To rectify this:

---

Step 8.) Restart the app server / application pool of the Epicor environment
  
---

Step 9.) In Epicor open the ‘Directive Update’ program

---

Step 10.) Click on the ‘Directive Recompile Setup
  
---

Step 11.) Check ‘Refresh Signatures’

---

Step 12.) Select ‘All’ under the ‘Owned By’ dropdown

---

Step 13.)Leave the rest unchanged
  
---

Step 14.) Click ‘Start Recompile’

---

Step 15.)Check that all directives have been recompiled successfully

---

## Client Deployment Files

Step 1 .)With the Application Server virtual directory, usually

![paraminstall1.png](/technical-documentation/paraminstall1.png)
  
Step 2.) In the Client folder should be a GHA Params folder containing the client files zip
  
Step 3.) Copy the GHA Params folder and contents to

![paraminstall2.png](/technical-documentation/paraminstall2.png)
  
Step 4.) Use these steps to update the Deployment Client Config file for automatic update of Epicor clients with the client sides files for the new dashboard:
  
o	Navigate to the client\config folder in the deployment share location of your Epicor application installation
  
![paraminstall3.png](/technical-documentation/paraminstall3.png)
  
o	Open the *.sysconfig file that is used for the Epicor Client installations where the dashboard is to be deployed and add the following node at the end of the configuration file before!

![paraminstall4.png](/technical-documentation/paraminstall4.png)
  
![paraminstall5.png](/technical-documentation/paraminstall5.png)
  
o	When you run the clients using this sysconfig, the system copies the Dashboard client files onto them.
  
o	Save and  exit the sysconfig file.
  
NOTE: Also do the same in the respective auto*.sysconfig file in the same folder
The “X” referenced above for GHA Params refers to the zip, e.g GHA Params.1.zip
