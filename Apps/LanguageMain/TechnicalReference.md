---
title: Language Maintenance Technical Reference
description: 
published: true
date: 2024-01-19T15:01:01.265Z
tags: 
editor: markdown
dateCreated: 2023-11-06T12:55:01.396Z
---

# Language Maintenance Technical Reference

## General Information
The link for the dev version of this web application is: **[https://langdev.ghahosted.com](https://langdev.ghahosted.com)**.
Currently there is no link for the live version.
<br>

## Login Page
Below is the login page for the Language Maintenance Program
![loginpage.png](/languagemaintenance/loginpage.png)
To log in a username and password must be provided.

There are currently two different error messages that can appear below the log in button
1.
![erroroccurend.png](/languagemaintenance/erroroccurend.png) 
If either the username or password text box is empty then this error appears. However, this error can also appear when something went wrong with the API itself, the password and username may be correct but the program would not be available at this time.
2.
![invalid.png](/languagemaintenance/invalid.png)
This error means that the API works fine but the provided details were not correct.

When entering the password the text is naturally hidden, this can be changed to be able to view the password by pressing the button next to the textbox with the eye icon - upon pressing this button the icon will change and the password will be revealed - pressing the button again will hide the password again.

If a valid username and password is entered and the log in button is pressed then the user will be taken to the landing page which is the Language Page.

To Login this web application uses `https://dev02api.ghahosted.com/mobileportal/api/v1/LicenceSvc/AuthenticationManagement/Login`

## Language Page

![langpage.png](/languagemaintenance/langpage.png)

### Top Bar
Currently the top bar contains only two sections: 
1. The title which when pressed brings the user back to the landing page of the application
2. The profile icon which when pressed brings the user to the profile page
### Selection Section
This section allows the user to select what information they wish to view - changing any of the details calls the API again. However the API call should take less than a second to run so the loading should not be noticable unless internet speeds are slow.

To get the language files selected the web app uses: `https://dev02api.ghahosted.com/mobileportal/api/v1/LicenceSvc/LanguageFile`

#### Applications DropDown
This drop down contains all of the application which contain a language file - Currently this is just Mobile Field Service. 
This information is taken from the  ` GHALicensePortal.dbo.LanguageFiles ` database through the License API

#### Languages DropDown
This drop down contains all of the languages currently available to edit. There are two files which cannot be opened and editting this way, the English file and the Notes file.

To get the languages the web app uses: `https://dev02api.ghahosted.com/mobileportal/api/v1/LicenceSvc/Languages`

#### Web API Switch
This switch allows to switch between the Web and API version of the language files.

#### Show All Missing Switch
This switch allows to switch between all of the information from the language files and just the missing information.

#### New Language Button
This button opens up the new language modal
![newlangmodal.png](/languagemaintenance/newlangmodal.png)
This modal allows to create a new language.

To create a new language the web app uses : `https://dev02api.ghahosted.com/mobileportal/api/v1/LicenceSvc/LanguageFileCopy`

The Applcations drop down works the same as the other application drop down - New application languages cannot be created here, they must firstly have a valid English File in the ` GHALicensePortal.dbo.LanguageFiles `. 

The language name accepts text and then checks if the provided text against a list of valid languages and the appropriate ISO Code. If an ISO Code cannot be found for the language provided then an error is displayed and the modal stays open. 

An error is also displayed if a user inputs a language that already exists. If this occurs the modal will close and show the user two errors underneath the New Language button on the main page.
![errors.png](/languagemaintenance/errors.png)

After a successful request has been inputted then both the Web and the API version for the language provided is created. When creating the language the API copies the english file, clears it and saves it in ` GHALicensePortal.dbo.LanguageFiles ` under the new language name.


## Profile Page

After pressing the profile button in the right corner of the top bar the user will be taken to the profile page where they are able to see their basic details and they are able to change their own password.
![profilepage.png](/languagemaintenance/profilepage.png)

### Changing Password
For a user to change their password they need to first insert their current password and then their new password twice. To then confirm the changes the user needs to press the Change Password Button which will either return an error which looks similar to this: 
![errorprofilepage.png](/languagemaintenance/errorprofilepage.png)
or a success which looks like this:
![successprofilepage.png](/languagemaintenance/successprofilepage.png)

Please note: A password needs to be at least 8 digits long, needs to contain a number, capital letter and a symbol to be valid.

### Other
In this page the user can also log out from their account and they can also go back to the previous page.


## Editing a Language
### Selecting section to Edit
To select a section the user needs to press on which header they wish to view. Upon press the section will open up and allow the user to make changes.
The below is the "Text Field Labels" section expanded
![expanded.png](/languagemaintenance/expanded.png)

### Saving
After making changes to one or more of the text boxes in the selection a "Save" button will appear on the bottom of the page.
![savebutton.png](/languagemaintenance/savebutton.png)
Upon pressing this button the all of the text boxes (including the notes) will be saved and sent over to the database.

To save the file the web app uses: `https://dev02api.ghahosted.com/mobileportal/api/v1/LicenceSvc/LanguageFileAddFromString`





