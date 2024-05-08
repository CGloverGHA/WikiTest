---
title: Deployment Procedures
description: 
published: true
date: 2024-01-19T15:00:38.601Z
tags: 
editor: markdown
dateCreated: 2023-11-27T08:32:18.536Z
---

# Deployment Procedures


## Process for Releasing new CABs

### Update the version number in the Version function
This should be done by the developer who created the CAB. In Epicor go to *"Epicor Functions Maintenance"*. Click on the *"Library"* and search for the CAB you wish to update. In the side bar right click on *"Version"* and edit the version in the *"Overview"* 
<br>
### Build the cab
This should be done by the developer who created the CAB. In Epicor go to *"Solution Workbench"*. Here use the *"Solution"* button and seach for the CAB you wish to build. Then on the top bar click on *"Actions"* and then *"Build Solution"* and before pressing *"Build"* click the checkbox that says *"Prompt For CAB File Name and Location"*
<br>
### Copy onto the wiki
This should be done by the developer who created the CAB. To Copy onto the Wiki find the area for the relevant CAB you want releasing and insert a new asset in place of the old version of the CAB.There should be two version of the CAB, an installation file and a patch file, make sure both of those are present. Then make sure to save the Wiki Page 
<br>
### Update change log on wiki 
This should be done by the developer who created the CAB. Find the area for the Change Logs for the relevant CAB which is being released. Typically this can be found on the same page as the CAB file itself. Then write down the version and the date that the CAB is released. Following that write down all of the changes that have been made inside of that CAB.
<br>
### Send the email 
The sending of an email should be done by administration. To send an email go to the License Portal and head over to the application section. Then press on the *"Send Emails"* button of the application which had the CAB change this then opens up a modal. Then press the first option *"Send CAB Email"* and press Send. An email should be sent to all relevant people.
<br>
### Copy CAB to hosted customers 
Contact support team if the CAB is effecting the backend, if not then the process is the same as adding a CAB to our own servers

## Process for releasing new API changes

### Commit the release version to bitbucket
This should be done by the developer of the API. Inside of a console cd into the folder you wish to commit. Then use the git commands: *"git status"* to see which files have been changed. Then use the git command *"git add -A"* to add all of the changed files. After that the command *"git commit -m "x" "* where x is a message about the changes that were made, this commits of all the changes locally so the command *"git push"* needs to be used to push the local changes to a remote branch. 

Please note:
If a repository is not created for the API then one must be created.
If a pipeline is not created for the API then one must be created.
If the branch you're commiting to does not already have a remote branch then one must be created.
The branch you push your commit to must the one that the pipeline is targeting. Typically this is the develop branch for Dev or the release branch for Live.
<br>

 
### Approve release to live server 
After pushing the API change to the pipelines, if the changes are for the Live server then a manager will have to approve the changes made. The manager should receive an email. They should then go to the relevant pipeline and click on the *"Approve button"*.
<br>

### Update change log on wiki 
This should be done by the developer who created the API changes. Find the area whic the API affects. Then write down the version and the date that the API is released. Following that write down all of the changes that have been made inside of that API.
<br>

### Send the email 
The sending of an email should be done by administration. To send an email go to the License Portal and head over to the application section. Then press on the *"Send Emails"* button of the application which had the CAB change this then opens up a modal. Then press the first option *"Send API Update Email"* and press Send. An email should be sent to all relevant people.
<br>

 
## Process for releasing new App changes


### Deploy change to Google Play store
Build an AAB file and sign it with the App signing key which can be grabbed from OnePassword. Go to Google Play Console navigate to the App that you are deploying then select production or internal testing track there's a button in top right called *"New Release"* click on that and then their is a section to upload the App bundle. Click on *"Upload"* and upload the AAB File. Further down there is a release note section click *"Add Release Notes"* and enter release note.
### Deploy change to Apple store
When deploying to the Apple Store the follwing tasks have to be done on the Mac Mini. 
For Xamarin App Release:
- Open app solution in Visual Studio 
- Clean the solution
- Make sure to select Project that is being built in top bar e.g *"mims.iOS"*
- Select release configuration
- Select generic build device (Make sure no IPhone is not plugged in)
- In solution Explorer right click on the selected project
- Click rebuild
- Once done right click project again
- Click *"archive for publishing"* 
- That will open new window with latest version on top. Select that version
- Click *"Sign and Distribute"*
- Select *"App Store"* 
- Select *"Next"*, *"Upload"*, *"Next"*, *"Provisioning Profile"*, *"Next"* 
- Enter app specific password (in OnePassword)
- Select *"Next"* 
- Go to *"App Store Connect"*
- Select the App you want to deploy
- Should be a table of releases
- Wait until the release you published is processed
- Click the link and enter required information 
	- Standard Apple Encryption 
	- No for France

For production: 
- Click on app store tab
- Left side bar - Click on the blue plus button
- Enter the version number
- Scroll down to release notes and enter the release notes
- Click *"Next"*, *"Next"*


Flutter

Inside of a console cd into the folder you wish to commit. Then use the git commands: *"git status"* to see which files have been changed. Then use the git command *"git add -A"* to add all of the changed files. After that the command *"git commit -m "x" "* where x is a message about the changes that were made, this commits of all the changes locally so the command *"git push"* needs to be used to push the local changes to a remote branch. 

Please note:
If a repository is not created for the App then one must be created.
If a pipeline is not created for the App then one must be created.
If the branch you're commiting to does not already have a remote branch then one must be created.
The branch you push your commit to must the one that the pipeline is targeting. Typically this is the develop branch for Dev or the master branch for Live.
<br>

 
### Approve release to live server
After pushing the App changes to the pipelines, if the changes are for the Live server then a manager will have to approve the changes made. The manager should receive an email. They should then go to the relevant pipeline and click on the *"Approve button"*.

### Send the email
The sending of an email should be done by administration. To send an email go to the License Portal and head over to the application section. Then press on the *"Send Emails"* button of the application which had the CAB change this then opens up a modal. Then press the first option *"Send App Update Email"* and press Send. An email should be sent to all relevant people.
<br>
 
## Process for Web

### Commit the release version to bitbucket
This should be done by the developer of the Web page. Inside of a console cd into the folder you wish to commit. Then use the git commands: *"git status"* to see which files have been changed. Then use the git command *"git add -A"* to add all of the changed files. After that the command *"git commit -m "x" "* where x is a message about the changes that were made, this commits of all the changes locally so the command *"git push"* needs to be used to push the local changes to a remote branch. 

If torchbearer has made the changes then if they push the work to the master branch it will automatically deploy to dev environment however, if those changes are to be made public then there is a pipeline in Azure DevOps that needs to be manually ran and approved.

Please note:
- If a repository is not created for the API then one must be created.
- If a pipeline is not created for the API then one must be created.
- If the branch you're commiting to does not already have a remote branch then one must be created.
- The branch you push your commit to must the one that the pipeline is targeting. Typically this is the develop branch for Dev or the release branch for Live.
<br>

 
### Approve release to live server
After pushing the API change to the pipelines, if the changes are for the Live server then a manager will have to approve the changes made. The manager should receive an email. They should then go to the relevant pipeline and click on the *"Approve button"*.
<br>

### Update change log on wiki
This should be done by the developer who created the API changes. Find the area whic the API affects. Then write down the version and the date that the API is released. Following that write down all of the changes that have been made inside of that API.
<br>

### Send the email
The sending of an email should be done by administration. To send an email go to the License Portal and head over to the application section. Then press on the *"Send Emails"* button of the application which had the CAB change this then opens up a modal. Then press the first option *"Send API Update Email"* and press Send. An email should be sent to all relevant people.
<br>


<br>

## Process for Field CAB
### Update the version number in the Version function
This should be done by the developer who created the CAB. In Epicor go to *"Epicor Functions Maintenance"*. Click on the *"Library"* and search for the CAB you wish to update. In the side bar right click on *"Version"* and edit the version in the *"Overview"* 
<br>
### Build the cab
This should be done by the developer who created the CAB. In Epicor go to *"Solution Workbench"*. Here use the *"Solution"* button and seach for the CAB you wish to build. Then on the top bar click on *"Actions"* and then *"Build Solution"* and before pressing *"Build"* click the checkbox that says *"Prompt For CAB File Name and Location"*
<br>
### Copy onto the wiki
This should be done by the developer who created the CAB. To Copy onto the Wiki find the area for the relevant CAB you want releasing and insert a new asset in place of the old version of the CAB.There should be two version of the CAB, an installation file and a patch file, make sure both of those are present. Then make sure to save the Wiki Page 
<br>
### Update change log on wiki
This should be done by the developer who created the CAB. Find the area for the Change Logs for the relevant CAB which is being released. Typically this can be found on the same page as the CAB file itself. Then write down the version and the date that the CAB is released. Following that write down all of the changes that have been made inside of that CAB.
<br>
### Send the email
The sending of an email should be done by administration. To send an email go to the License Portal and head over to the application section. Then press on the *"Send Emails"* button of the application which had the CAB change this then opens up a modal. Then press the first option *"Send CAB Email"* and press Send. An email should be sent to all relevant people.
<br>
### Copy CAB to hosted customers
Contact support team if the CAB is effecting the backend, if not then the process is the same as adding a CAB to our own servers
<br>

## Process for Parameter Screen
### Build the cab 
This should be done by the developer who created the CAB. In Epicor go to *"Solution Workbench"*. Here use the *"Solution"* button and seach for the CAB you wish to build. Then on the top bar click on *"Actions"* and then *"Build Solution"* and before pressing *"Build"* click the checkbox that says *"Prompt For CAB File Name and Location"*
<br>
### Copy onto the wiki
Copying to the Wiki should be done either by the Epicor developer or a normal developer. To Copy onto the Wiki find the area for the relevant CAB you want releasing and insert a new asset in place of the old version of the CAB. Then make sure to save the Wiki Page.
<br>
### Update change log on wiki
Updating the logs should be done either by the Epicor developer or a normal developer, preferably the person who developed the CAB. Find the area for the Change Logs for the relevant CAB which is being released. Typically this can be found on the same page as the CAB file itself. Then write down the version and the date that the CAB is released. Following that write down all of the changes that have been made inside of that CAB.
<br>
### Send the email
The sending of an email should be done by administration. To send an email go to the License Portal and head over to the application section. Then press on the *"Send Emails"* button of the application which had the CAB change this then opens up a modal. Then press the first option *"Send Param Screen Email"* and press Send. An email should be sent to all relevant people.
<br>
### Copy CAB to hosted customers
Contact support team if the CAB is effecting the backend, if not then the process is the same as adding a CAB to our own servers