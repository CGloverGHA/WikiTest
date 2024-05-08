---
title: MFS Testing Technical Guide
description: 
published: true
date: 2024-01-19T15:01:40.931Z
tags: 
editor: markdown
dateCreated: 2023-08-25T13:27:26.428Z
---

# MFS Testing Technical Guide

## Loading Data API
Upon opening the MFS Testing Page you will be prompted with a spinning icon for the each of the tables that the API is loading. 

> If the API call is taking longer than a minute or the data returned seems to be incorrect eg. no profiles loaded. Then the page should be reloaded by pressing the "MFS Testing" button on the Navigation Bar.
{.is-info}


Upon loading into onto the page you will see an empty screen with an animated arrow on the bottom, simply scroll down to see the table with information. 

> This will only be shown when loading onto the page for the first time or if the cache is cleared.
{.is-info}




## Profile 

To create a new Profile click the "Add New" button on the profile table. This will create a new profile in the database with a unique Identifier.

To select a profile click on the radio button under the "Actions" tab on the table. 

To edit a profile click on the pen button under the "Actions" tab on the table and to delete click on the trash can icon.

Profiles are global to all users of the website however, one profile can own many different Environments. These environments are local to the profile selected. 

## Environments

To create a new Environment click the "Add New" button on the environment table. This will create a new environment in the database with a unique Identifier under the currently selected profile.

To select a environment click on the radio button under the "Actions" tab on the table. 

To edit a environment click on the pen button under the "Actions" tab on the table and to delete click on the trash can icon.

You can check if the Environment is correct by pressing the test connection icon. This will send an API call to Epicor using that environment and will return either a green checkmark to show success or ared cross to show failure.

Environments are local to the profile selected however, they can own many different jobs which are local the environment selected.

> When selecting a profile or environment the ID of the selected gets stored in local storage. This means that the selected profile or environment is computer dependent and will only be changed by the program or if local cache is cleared.
{.is-info}

## Jobs

### Running Jobs
Once there is a selected profile and environment and a job is set to run a "Send Jobs" button will appear on the bottom of the page. This will run all the jobs that have been set to run and will run the amount of time specified. 

Upon running all the jobs an information table will appear with all the completed job numbers and all the errors if any were present.

### Default Values

Upon clicking the "Set Default Values" button a modal will pop up which sets the default values on the machines local storage. These values automatically get inserted into the textboxes when adding new jobs.  

### Creating new / Editing existing

The modals for creating / editing jobs have a few different types of textboxes. These include: 

![image_2023-08-25_143806356.png](/image_2023-08-25_143806356.png)
A simple text box with accepts alphanumeric characters and shows a tooltip when hovered over.

![image_2023-08-25_143854412.png](/image_2023-08-25_143854412.png)
A checkbox which doesn't accept any sort of input apart from the checking the box

![image_2023-08-25_143955750.png](/image_2023-08-25_143955750.png)
A textbox with a search function. Upon clicking the search icon there are three possible results:
- Green Checkmark - which allows to open up the menu to see the API results
- Orange Sync Icon - which shows the API worked but didn't return any results
- Red Cross - which shows the search function failed

![image_2023-08-25_150141079.png](/image_2023-08-25_150141079.png)
A Combobox with fixed values

![image_2023-08-25_150217058.png](/image_2023-08-25_150217058.png)
A textbox which only accepts numberical values

![image_2023-08-25_150257005.png](/image_2023-08-25_150257005.png)
The search for part numbers is slightly different. Upon clicking the search button a modal will appear:

![image_2023-08-25_150342897.png](/image_2023-08-25_150342897.png)
Here usign the radio buttons allows for the searching of parts either using the part number or the serail number.

> Please note that the part search can take as long as 30 seconds when using the serial number search
{.is-info}

Upon a successful search a table will appear which will allow for selection of a part.

![image_2023-08-25_150722743.png](/image_2023-08-25_150722743.png)

To search for a Ship To a customer will first have to be selected. Before this is done a the search button for the Ship To will be greyed out and will not call the API for the Ship Toes.



