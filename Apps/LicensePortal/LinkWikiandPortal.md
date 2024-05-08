---
title: WikiOutgoingService
description: 
published: true
date: 2024-01-19T15:01:16.049Z
tags: 
editor: markdown
dateCreated: 2023-03-01T15:22:51.007Z
---

# Wiki Outgoing Service


## Triggers
### **SendSuspendedUserfFromLicPortaltToWiki** 
This trigger is located on **GHALicensePortal.dbo.AspNetUsers**.

It runs when the suspended column in AspNetUsers is either added or updated.

It selects the values from the email and suspended column of the edited row and send a message of this format to the queue: 
`{"Suspend": Email,"Suspended":success} `

where Suspend is a string and Suspended is a boolean value.

### **SendNewRoleFromLicPortalToWiki**
This trigger is located on **GHALicensePortal.dbo.AspNetUserRoles**

This trigger runs whenever a customer receives a new role or an existing role is updated

Initially it gets the values from: UserId and RoleId from the edited row.

The RoleId is used to get all of the roles that the user has from AspNetRoles table. All of these roles are then put into a string value. 

The UserId is used to get the user's email's from the AspNetUsers table. 

Both of these are then used to send a message to the queue in this format:
`{"UpdateEmail": UserEmil,"Roles": AllRoles}`

where UserEmail is a string and AllRoles is a string

### **SendUserFromLicPortalToWiki**
This trigger is located on **GHALicensePortal.dbo.AspNetUsers**

This trigger runs whenever a new user is added or an existing one is edited.

Initially it gets the values from: Id, CustomerId, KnownAs and email from the inserted row.

The Id is used to find all of the roles that the user has. This returns a list which is looped through to get all of the roles into a string. Each item is separated by a "," and at the end of the list a ":" is placed.

The CustomerId is used to get all of the applications that the customer has access to. This is again looped through and added to the same string as above. Again each item is separated by a ",". However this also checks if the application is suspended. If it is then the group is not added to the list of available apps for the user.

Knownas is used set a username to the user.

Finally the email is used to later add the user to the wiki and send a welcome email.

All of these are placed into this query:
`		'{`
          `"Email": Email, `
          `"Name":username,`
          `"Password":"\u0022Password1\u0022",`
          `"ProviderKey":"\u0022local\u0022",`
          `"Group": group,`
          `"MustChangePassword":"true",`
          `"SendWelcomeEmail":"false"`
		`}'`
         
Where Email is a string
Username is a string
Group is a string 
          
### **UpdateCustomerApplicationsFromLicPortalToWiki**
This trigger is located on **GHALicensePortal.dbo.CustomerApps**  

This trigger is ran whenever a customer receives a new application or an existing one gets edited. 

Initially it just gets the value from the CustomerId from the inserted row.

This is just used to create a list of Id, Email, Knownas from AspNetUsers which is used to loop through all of the customers that would be affected by the change. 

After this list is created then the same process and message as SendUserFromLicPortalToWiki. A message to add a new user to sent. This is then checked in code and if a customer already exists then it just updates the groups.



### **SuspendApplicationFromLicPortalToWiki**
This trigger is located on **GHALicensePortal.dbo.Applications**

This trigger is ran whenever a new application is added or an existing one is edited. 

Initially this just gets the ApplicationId from the inserted row. 

This is used to create a list of all of the customers that have that applications and then the trigger follows the same process as the UpdateCustomerApplicationsFromLicPortalToWiki trigger. This ensures all users how should have access to that application do indeed have access to the website and the correct group.	


## Service how it works

The service connects to the GHALicenseMQ database which allows for the service to use the ` [dbo].[Recieve_Message]` stored procedure which takes the first message in the queue. This is then checked for a null value and then deserialised based on what the message starts with. 

This service loops every 60000 milliseconds (1 minute) this is hardcoded in. To change this, a connection will need to be made to the GHA license portal database and the data should be kept in the AppSettings table.

The service then, depending on the type of message that is being sent through, will send the message to one of the following functions:

1. SendApiToWiki 
	- This sends a GraphQL request using RestSharp 106.15.0. The response from this is then checked. If the user has been successfully added then two emails are sent to the user. The first email is a welcome email where the user is told about the wiki, the second email contains a password for the user to log in. 
	- The password is randomly generated in the program and the user has to create a new password upon first login. 
	- If the user is already in the wiki then the groups of the user are reset. This just means that the users groups are checked and updated with new correct information
  
2. UpdateUserFromMessage
	- This first checks the email provided and gets the ID of the user through a GraphQL request to the wiki. This response is then use to get all of the groups the user is currently in.
	- The message recieved by this function should contain a list of all the roles the user possesses. When the users role is changed then the service gets all of the users current groups and amends them accordingly. For example if previously the user wasn't a super user and they had access to the License Portal documentation they would have access to the "License Portal : User" group on the wiki however, after the update if the super role is added then the user will be given access to the "License Portal : SuperUser" group in the Wiki. 

3. SetUserAsSuspended
	- This first checks the email provided and gets the ID of the user through a GraphQL request to the wiki.
	- This id is then used to suspend the user using a GraphQL request. 
