---
title: TrimLogger
description: Documentation for Trim Logger internal program
published: true
date: 2024-01-19T15:01:32.773Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:11:39.416Z
---

# TrimLogger

### **Introduction**

The Trim log Service Worker has been created to delete logs from all customer databases which have are older than 60 days old. This has been done to be able to speed up the day-to-day use of the log databases. This service runs once every day and deletes all logs from each customer which meet the criteria of the date range.

### **How it Works**

Inside the AppSetting.json there is information stored such as: the environment on which the worker will operate; the amount of time that it will wait before running again, this is measured in milliseconds; the amount of time that will be used to create a date in the past, logs will be deleted if they are older than this date.

The first thing the worker does it access the AppSettings file and get the environment on which it is working on. Once it knows the environment it gets all of the customers from that environment and puts them into a list. It then reads each customer from the list and selects the customer Id and their licence key from the database, this information is then used to access their database. Once in their database the worker checks for: MFS.MessageLogs, MFS.ErrorLogs, MFS.KeyLogs, MFS.ChangeLogs, AQS.MessageLogs, AQS.ErrorLogs. If any of the tables don't exist, then that log is simply skipped. If the log is present, then the worker checks how many items in that log are older than the date specified earlier by the use of the AppSettings file. If there is more than one item older than the date, then the worker deletes those items from the log. If the worker has deleted some items, it logs the amount deleted and from were. The worker then moves on to the next customer. Once all the customers are checked, the worker stops and starts again in 24 hours.

### **Trim Log Setting Table** ( AppSettings Table)


- TrimLogger - ChangeLogs
- TrimLogger - ErrorLogs
- TrimLogger - KeyLogs
- TrimLogger - MessageLogs
	- All of the both take an integer value . This value determines how many days should the worker go back to delete them.

- TrimLogger - LoopPeriod(ms)
	- Take a Integer value . This determines how often the Trim Logger should run if not scheduled

- TrimLogger - MaxLogsDeleted
	- Takes a Integer value. Determines how many logs should be deleted at once. 

- TrimLogger - Schedule
	- Takes a Boolean which determines if it is scheduled. 1 - true  0 false
	- Takes a Integer which determines how often the worker should check if the time has been reached
	- Takes a String value which states at which time the worker should run if scheduled

