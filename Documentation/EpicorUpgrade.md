---
title: Epicor Upgrade
description: 
published: true
date: 2024-03-18T15:25:46.849Z
tags: 
editor: markdown
dateCreated: 2024-03-13T15:44:21.717Z
---

# Epicor Upgrade Process

## Introduction
Here is a step by step process on how to upgrade Epcicor to a newer release.

---

Step1.) First thing we need to do is to run through backups as a failsafe for if something goes wrong. Taking a backup of the virtual machines and databases.

---

Step 2.)Install the media (RL and UD) that you would like to upgrade to. Do this by heading to the ebicweb webiste and installing the realease version and the patch version you would like. Run these exe once installed. After the installation is complete, untick the "open administration console box" 

---

Step 3.) Open the epicor administration console, remove the database for the app server youre upgrading and then re register it. This will force an update to the DB.  

---

Step 4.) A pop up will appear, choose the correct version you are updating to. 

---

Step 5.) Next, right click the data base and click "Upgrade Database"

---

Step 6.) Then click "Show more " and then click the configuration cog at the top of the pop up. Change the BAQ to dd/mm/yyyy
 
---

Step 7.) Click "Start" 

---

Step 8.) Once finished click "Show log" and copy all of the log into a text file and save to desktop 

---

Step 9.)Click "Close" 

---

Step 10.) Remove and re-register the app server.

---
 
Step 11.) Open the admin console 

---

Step 12.)Right click the app server and open the server configuration.

---

Step 13.)Change the deployment directory to the new version of epicor you are upgrading to.

---

Step 14.) On the drop down click the new UD

---

Step 15.)Ensure everything is correct make sure password is set etc 

---

Step 16.) Head to the Reporting services tab -> click the "import report" tick box (do not deploy yet, follow the next steps) 
	
---

Step 17.)Stop the task agent -> start menu -> epiucor software -> open task agent -> righ click the server -> stop agent -> yes 

---

Step 18.) Head to IIS and stop the server app pool -> app pools -> server -> right click and stop. 

![epicorupgrade1.png](/technical-documentation/epicorupgrade1.png)
---

Step 19.) Head to this file location and enter the server you are upgrading. Delete these three things 

![epicorupgrade2.png](/technical-documentation/epicorupgrade2.png)
---

Step 20.) Go to the server file from this and then delete everything other than custom 

![epicorupgrade3.png](/technical-documentation/epicorupgrade3.png)
---

Step 21.)Head into the custom folder 

---

Step 22.)Sort by date modified 

---

Step 23.) Delete everything but these 2 

![epicorupgrade4.png](/technical-documentation/epicorupgrade4.png)
---

Step 24.) Head to this file location, and delete the app server folder 

![epicorupgrade5.png](/technical-documentation/epicorupgrade5.png)
---

Step 25.) Make a backup of the DB again

---

Step 26.) Click deploy on the app server config 

---

Step 27.) Click okay once done 

---

Step 28.) Open the epicor shortcut on the desktop and log in  

---

Step 29.) Click Okay on the upgrade pop up 

---

Step 30.) Click "Yes" on pending conversions 

---

Step 31.) Then click "Actions" 

---

Step 32.) "Run pending conversions "

---

Step 33.) Click on the admin console 

---

Step 34.)Click on the app server 

---

Step 35.) Click task agent config 

---

Step 36.) Install task agent (next, next, next, next) 

---

Step 37.) Launch task agent 

---

Step 38.) Click "File "

---

Step 39.) Click "New agent "

---

Step 40.) Should populate it with the appropriate stuff

---

Step 41.) Add in username and password. 

---

Step 42.) Log into Epicor 

---

Step 43.) Test print 
○ User group report 
○ Print preview 

---

Step 44.) Next we need to install CSF 

---

Step 45.)Check how many companies the environment has  

---

Step 46.) In Epicor press the help button and search country specific functionality install and follow the guide step by step 

https://erphelp112400.zendesk.com/hc/en-us/articles/24843968848141-Getting-Started-with-United-Kingdom-CSF

---



---

Step 47.) When onto the configs. Ensure that you do it for the normal config and the auto. 

---

Step 48.) Copy and paste the line of code in and adapt the numbers for the version 

![epicorupgrade6.png](/technical-documentation/epicorupgrade6.png)
---
Step 49.) Head to D:\Epicor\ERP11\ERP11.2.400.0\ClientDeployment\Custom\Client\CSFUK and rename the csf to the version (remove last 0 and add the number of the version you require) 
 
---

Step 50.) Get rid of the skip in the shortcut (Right click shortcut, click properties an delete "Skip"

---

Step 51.) Install mods
(There are instructions on how to install the mods within the cab folders)

---
## The next steps may vary depending on wether extensions are set up: 

Step 1.) Open Epicor admin console

---

Step 2.) Open app server config 

---

Step 3.) Click "extensions" at the top 

---

Step 4.) Click "Data discovery"

---

Step 5.) Scroll down 

---

Step 6.) Click "Deploy"

---

Step 7.) Click "Ok" 

---

Step 8.) Test all new menu items work (Open them all and ensure that they all populate with either

---

Step 60.) Copy all the configs over? 

---

**Key terms**

Upgrade DB (Regenerate data model) 

Script Runner ( right click the database and press run scripts, look for the purple un run scripts)

Meta ui migration (open conversion workbench in Epicor and run 191) 

Directive update ( Open directive update on Epicor and click the second tab at the top, then click the check box and run the update)

Don’t forget that is epicor isnt opening, copy the inetroot, wwwepicor, mod folder into the deployment folder (D: Epicor, 11.2.400, custom, paste) 

If there are errors on the logs save them to a text file and keep it on the desktop. 
