---
title: MQChecker
description: Documentation for the MQChecker internal program
published: true
date: 2024-01-19T15:01:53.131Z
tags: 
editor: markdown
dateCreated: 2023-02-01T13:11:48.989Z
---

# MQChecker
**Introduction**
Message Queue is a service which allows for jobs to be sent to epicor one at a time. It runs on the server. However sometimes the MQ can go down, there is no way of knowing it is down apart from checking if the messages are moving. This can be bad as if the MQ goes down during the night, there will be no notification or issue pop up anywhere. 

**How It Works**
The checker runs once an hour (by default, can be changed in settings) and sends an email if there are enough items on the MQ. Then it checks again in some time to see if it has changed. If it has changed then it sends an email saying that it's moving without issue however, if it doesn't change (time of first message or the size of the queue hasn't gone down) then an email is sent saying that is it most likely down and needs checking out by someone.

The people which recieve the email are listed in GHA.LicensePortal.dbo.Admins under HealthChecker.

Also the email which is recieved formats the email using html to be able to easily view what is wrong with the MQ. Both the first and second email are formatted like this.

### MQ table variables (AppSetting Table)

- MQChecker - HoursToRun
	-  Decimal
	- Used to see how often the program should run. Calculated, rounded and then changed to a integer. This allows for someone to be able to say 0.5 of an hour.
- MQChecker - MinutesToGoBack
	 - Integer 
	 - Used to only send email if the messages on the queue have been on the queue for a specified amount of minutes.
- MQChecker - MinutesToWait
	 - Integer 
	 - Used to see how long the program should wait before checking if the queue has changed.
- MQChecker - Schedule
	- Takes a Boolean which determines if it is scheduled. 1 - true  0 false
	- Takes a Integer which determines how often the worker should check if the time has been reached
	- Takes a String value which states at which time the worker should run if scheduled
- MQChecker - SendFirstEmail
- MQChecker - SendMovedEmail
- MQChecker - SendRunningEmail
- MQChecker - SendSecondEmail
	- Boolean / list
	- Used to see if an hourly email should be sent regardless of the result of the queue size 
	- 0 - don't send 1- send
	- Also stores the email which the email will be sent to. The emails are split using ';'. 
- MQChecker - SizeToCheckAbove
	 - Integer 
	 - Used to only send the email out if there is one or more tables on the MQ which have more messages than the stated amount.
- MQChecker - TableType
	- Integer
	- Used to see which table should be sent.
	- 0 is more simplistic 1 is more detailed