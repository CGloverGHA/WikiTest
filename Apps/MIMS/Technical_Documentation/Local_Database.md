---
title: Local_Database
description: 
published: true
date: 2024-01-17T13:26:49.215Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:14:00.577Z
---

The local database is a SQLite database stored on the User's device that is primarily used to locally save user data between sessions

Most of the data stored in this database is **not backed up to Epicor**. This means that if the app is re-installed, the data will be lost


# Fields
## Last Employee
This stores the `EmpID` of the last logged in user

## Plant
Stores the last selected plant from the [Login Screen](./Applets/Login_Screen.md)

# MIMS Layout
Stores a local copy of the layout of the Applets on the [Home Page](./Applets/Home_Page.md)

# Databases
## Employees
A local list of Employees stored in a separate database