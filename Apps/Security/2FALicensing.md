---
title: Licensing and 2FA
description: 
published: true
date: 2024-01-19T15:02:44.352Z
tags: 
editor: markdown
dateCreated: 2023-06-22T06:18:26.591Z
---

# Technical Reference for Licensing and 2FA
<br/>

## Licensing
<br/>

### Mobile Application Licensing
<br/>

#### Named Licensing vs Concurrent Licensing

**What is named licensing on devices?**

A customer will buy a set number of licenses and only that many devices can be registered at any one time.

**What is concurrent licensing on devices?**

A customer will buy a set number of licenses. An unlimited number of devices can be registered but only the set number can be used (logged in) at any one time.

#### Business process - named licensing

Named licensing is enabled by turning concurrent licensing off in the license portal on the Customer Applications page

- An application is dowloaded from the relevant app store
- The device is registered by scanning the QR code provided by the license portal
- If there are spare licenses available the device is registered
- If there are no licenses available the device goes into approval mode where it may be turned into an Admin device
- Any registered device should have the ability to be put into Admin mode

Admin devices are used by GHA in order to test a customers set up. They do not consume a license, do not appear on a customers license portal and do not count as a login when preventing multiple logging of a technician/employee/user

Any named device should be able to be logged in and logged out without affecting the licenses.



#### Business process - concurrent licensing

Concurrent licensing is enabled by turning concurrent licensing on in the license portal on the Customer Applications page

- An application is dowloaded from the relevant app store
- The device is registered by scanning the QR code provided by the license portal
- There is no limit to the number of devices that can be registered
- Any registered device should have the ability to be put into Admin mode

Admin devices are used by GHA in order to test a customers set up. They do not consume a license, do not appear on a customers license portal and do not count as a login when preventing multiple logging of a technician/employee/user

When logging in on concurrent licenses a license is consumed. Once there are no more licenses available no devices will be allowed to log in again until a license is released.

A license can be released in one of two ways:
- a user/technician/employee logs out
- a license is released via the license portal

> If a license is released using the license portal, how does the device know not to let the user continue?
> - In the case of Mobile Field Service they will not be allowed to travel, arrive or start a new job
> - In the case of MIMS they will not be allowed to start a new mini-app.
>
> This necessitates an internet connection when using the apps and performing these functions

An admin device allows a user to login without affecting the number of concurrent licenses consumed

<br/>

#### Technical process

**Device Registration**

Named licensing is enabled by setting the `CustomerApps.ConcurrentLicensing` flag to false. This can be done using the License Portal.

The number of named licenses is set in the `CustomerApps.MaxDevices` field

The QR code for registration generated on the License Portal contains the license key for the customer application (`customerapp` table) and the customer. This is used by the app to generate a device token containg the following:
- Application license key (hard coded in the app)
- Customer license key (from registration barcode)
- Customer/Application license key (from registration barcode)
- Device identity (GUID unique to the device and app combination)

When the QR code is scanned the the `LicenseSvc/Register` endpoint is called with the device token and the name of the device. On the API: 
1. The token is decoded to give the customer/application license keys and the device identity.
2. The licenses keys are checked for validity
3. The customer and application are checked to make sure they have not been suspended
4. The Devices table is checked to see whether the device exists
 - if the device exists then there is nothing to do and  a "Device Already Registered" message is returned.
 - if the device does not exist and concurrent licensing is enabled then the device is added to the Devices table 
 - if the device does not exist and named licensing is enabled then the number of devices already registered is checked against the named licenses in the `CustomerApps.MaxDevices` field. If there are licenses free then the device is added to the Devices table
 
If for any reason the device cannot be added then an appropriate message is returned to the device.
 
The /Register endppoint returns the customer name (to be displayed on the app as confirmation registration was successful) and the named/concurrent licensing flag, which may be used when logging in/out.

**Logging in**

When a technician/employee/user is logged in the id and password is passed to the API
- FieldServiceSvc/Login
- MIMSSvc/Login (to be written)

Device token checks are made as above to make sure the customer and application are valid as well as checking for suspensions

The password is compared to the that in the database, as well as other checks (eg valid vahicle, app versions)

If Concurrent Licensing is enabled then the number of devices logged in is checked against the `CustomerApps.MaxDevices` field, if no licenses are available then logging in fails.

For Mobile Field Service,  
- the technician is checked against the Technician table 
- if the device is not an admin device a check is made whether the technician is logged in on another device (`mfs.technicians.DeviceId`), if they are logging in is prevented

The following fields on the database are updated:

`Technicians.LoggedIn = true`
`Technicians.LastLoggedIn = DateTime.UtcNow`
`Technicians.DeviceId = DeviceIdentity of the device`
`Devices.HardLogin = true`
`Devices.UserId = TechnicianId of the technician`
`Devices.LastLogin = DateTime.UtcNow`

**Logging out**

The same checks are made as in logging in, apart from the fields being updated as follows:

`Technicians.LoggedIn = false`
`Technicians.LastLoggedIn = null`
`Technicians.DeviceId = null`
`Devices.HardLogin = false`
`Devices.UserId = null`
`Devices.LastLogin = null`

**Releasing Licenses**

This occurs via the license portal but has the same effects on the database as logging out

<br/>

### Web Application Licensing

**Features** 

- Only uses concurrent licensing
- Support multple customers
- Multiple applications *are* supported by using a unique url for each application
- Optional ERP link
  - ERP link turned off it uses standard Microsoft security
  - ERP link turned on checks which ERP and then uses ERP authentication via REST
- Optional 2FA using email and internally generated tokens
<br/>
- On succesful login 
  - issues an authentication token and a refresh token. When the authentication token expires a new one is generated from the refresh token
  - Creates a session, the number of which cannot exceed the number of licenses purchased
<br/>
- All subsequent calls to the API require
  - A valid authentication token
  - A valid session (if the user has no session then one is created provided there are enough available licenses)

**Registration**

At the moment users can be added in one of two ways:

1. Using the API call LicenceSvc/AuthenticationManagement/UserAdd
2. Syncing from Epicor using a data import or amending a user (then via data directives)

Users are stored in the following tables:

`GHALicensePortal.dbo.Users`
`GHALicensePortal.dbo.UserCustomers`
`GHALicensePortal.dbo.UserApplications`

The following table will be used 

`GHALicensePortal.dbo.UserRoles`

>Only the Users table is populated currently - future state is to populate UserCustomers from Epicor using the token sent to the API, and UserApplications from the license portal settings.
>
>The new License Portal should include a page to add users and assign to customers and applications as necessary
{.is-warning}

**Logging in**

***Preamble***

There are two scenarios when logging in, the user is registered with a single customer or with multiple customers.

If the user is registered with multiple customers they are presented with a list of customers after entering their username and password. After selecting a customer they are authenticated.

If the user is registered with only one customer they are authenticated directly against that one.

After a user has successfully logged in a session is created for them. Once all the sessions have been used no more users will be allowed to log in. After an amount of time, currently fixed at 10 minutes of inactivity, a session will be released.

>Sessions cannot be released at the moment except through the time out feature. Future work will add a screen to either the License Portal (temporary fix) or the Back Office
{.is-warning}

Optionally, every 14 days a user will have to use two factor authentication to validate their login. Currently only authentication via a code sent by email is supported.

***Mechanism***

When a user is logged in the username, password, application id and whether the test database is used is passed through to the `LicenceSvc/AuthenticationManagement/Login` endpoint.

The endpoint returns either a success, or a fail with a error message of "Invalid Username or Password". Any more information is not disclosed for security reasons.

---

- Check whether there is a record for that email address in the User table
- Check whether the user is suspended
- Check the user is registered against the application
- Get the list of customers the user is registered against
  - if no customer are registered return an error
  - if exactly one customer is registered against the user then proceed
  - if more than one customer is registered against the user then return the list customers. This list is presented on the login page for the user to choose one. When resubmitted this customer is used and the list of customers check is bypassed
- if the user (in the UserCustomers table) is marked as an Epicor user
  - get the Epicor connection string from the customer database
  - get the username from Epicor for the logged in email address
  - attempt to log in to Epicor using the Epicor credentials
- if the user is not marked as an Epicor user, it is designed to be standalone and the user is authenticated using Microsoft authentification

- Check whether the user (in the UserCustomer table) is marked for two factor authentication
  - if they are and the last 2FA authenticated date is more than 14 days ago (hard coded in) then
    - generate a 2FA token
    - email it to the user
    - return an Authentication token as normal
    - display a screen to enter the 2FA token
    
- Create a new session in the customer `Sessions` table. If there are no sessions available (comparing the number of valid (user has not logged out and the session is less than `CustomerApps.InactiveTime` minutes old) sessions in the `Sessions` table to the `CustomerApps.MaxLicenses` field) then do not allow the user to log in and return a "There are not enough sessions available - please see your administrator or try logging in later" error.

---

***Validating 2FA***

The customer will receive an email with the 2FA token. This is entered on the screen and submitted along with the Authentication token generated by logging in using the `LicenceSvc/AuthenticationManagement/Approve` endpoint. The token entered is compared to the last generated token against the user, then the user is logged in normally as above.

The 2FA token lasts for 10 minutes, after which it is invalid and a new token will need to be produced by logging in again.

[Testing](/Apps/Security/2FALicensingTesting)
