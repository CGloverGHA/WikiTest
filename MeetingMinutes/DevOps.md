---
title: Dev Ops Meeting
description: 
published: true
date: 2024-02-20T08:28:33.239Z
tags: 
editor: markdown
dateCreated: 2023-01-23T09:01:28.335Z
---

**24th February 2024**

# Attendees

* Phil Manning
* Peter Roden
* Josh Sweeney
* Bart Wojda

# Agenda

### Azure Running out of storage

Currently our storage for Azure Dev Ops can hold up to 2GBs of packages. This was recently exceeded.

Three options are as follows: 
1. Pay for more storage
	- $2 for every 2 GBs
2. Delete old packages that are no longer in use.
3. Removing nuget.org from upstream source

### Dev SQL Server Certificate

SQL Server certificates are now being used on GHAUKDEVSQL01

<br/>

### Live load balancer

Implemented and tested 20/1

### Disaster Recovery

#### Dev Server

Discussed - all back ups are being done on the same box. No disaster recovery should the box be stolen or damaged.

Main risk is the SQL server - all Epicor data is stored here and may be being worked on. Two possibilities discussed:

- Daily off site back ups (logistically difficult but not insurmountable)
- Saving the epicor CABs on one drive or the wiki

PM to change SQL transaction log backups to database incremental backups

### Wiki

Development department thinking about changing the wiki

CG to implement new wiki if and when decided

### SQL Server connection issues

When a connection is lost to the SQL server the field service sync services do not reconnect. To resolve these service need to be stopped and restarted.

Other services may be affected but they only run periodically. Restart all services anyway.

<span style="color:red">PR to document</span>

Is it possible for the service itself to check if the SQL connection is still there and reconnect if neccessary?

<span style="color:red">Dev team to investigate</span>

***Check again on
Thursday, 29 February 2024
Saturday, 30 March 2024
Monday, 29 April 2024
Wednesday, 29 May 2024***

#### Headings
- Infrastructure
	- Container Environment
  - Container Monitoring
  - Container Management
	- Server management
  - SQL Server
- Security
	- Application Security
  - API Security
  - Deployment Pipeline Security
  - Penetration Testing
  - Epicor Security
- Epicor
	- Environments
  - Parameter screen
  - Epicor client CABs
  - Licensing
- Documentation
	- Wiki
  - Technical Reference Guides
- Development Roadmap
