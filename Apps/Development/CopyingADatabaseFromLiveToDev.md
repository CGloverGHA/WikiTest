---
title: Copying a database from Live to Dev
description: 
published: true
date: 2024-01-19T15:00:35.804Z
tags: 
editor: markdown
dateCreated: 2023-06-21T07:04:21.499Z
---

# How to

- On Dev01 server
	- Copy \\GHAUKFS01\SQLBackup\GHAUKSQL01\Apps\DB\f359ec87-e245-4765-a3da-bc22d8603d47 to \\ghaukdvsql01\d$\SQL Backup\Manual
  - Grant permissions (full control?) to copied file
  - 
```  
use master

RESTORE DATABASE [f359ec87-e245-4765-a3da-bc22d8603d47]  
FROM DISK='D:\SQL Backup\Manual\f359ec87-e245-4765-a3da-bc22d8603d47_backup_2023_06_20_220001.bak' 
WITH REPLACE
```



First time

```
CREATE DATABASE [e6aa6926-173e-4708-a7f7-ae1ff877b4a0] 

RESTORE DATABASE [e6aa6926-173e-4708-a7f7-ae1ff877b4a0] 
FROM  DISK = N'D:\SQL Backup\Manual\e6aa6926-173e-4708-a7f7-ae1ff877b4a0_backup_2023_06_21_220001.bak' 
WITH  FILE = 1,  
MOVE N'e6aa6926-173e-4708-a7f7-ae1ff877b4a0' 
  TO N'D:\SQL DB\e6aa6926-173e-4708-a7f7-ae1ff877b4a0.mdf',  
MOVE N'e6aa6926-173e-4708-a7f7-ae1ff877b4a0_log' 
  TO N'D:\SQL Logs\e6aa6926-173e-4708-a7f7-ae1ff877b4a0_log.ldf',  
NOUNLOAD,  
REPLACE,  
STATS = 5

update ghalicenseportal.dbo.customers 
set customerid = 'e6aa6926-173e-4708-a7f7-ae1ff877b4a0',
ConnectionString = '...',
environment = 'develop'
where name = 'zWhales'

CREATE LOGIN [e6aa6926-173e-4708-a7f7-ae1ff877b4a0] with password = '...'


use [e6aa6926-173e-4708-a7f7-ae1ff877b4a0]
alter authorization 
on database::[e6aa6926-173e-4708-a7f7-ae1ff877b4a0] 
to [e6aa6926-173e-4708-a7f7-ae1ff877b4a0]

```