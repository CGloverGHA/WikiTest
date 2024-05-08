---
title: Licensing2FATesting
description: 
published: true
date: 2024-01-19T15:02:46.913Z
tags: 
editor: markdown
dateCreated: 2023-06-26T11:27:22.899Z
---

# Testing for Licencing and 2FA
<br/>


## Mobile Apps
<br/>

<pre><span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Feature</strong></span></span>: Named Licenses
  As a GHA mobile application customer I want to buy named licenses so each individual has their own registered device

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Background</strong></span></span>: In the License Portal:
    <span style="color:#0000ff;"><strong>Given</strong></span> Mobile Field Service has concurrent licensing disabled
     <span style="color:#0000ff;"><strong>And</strong></span> Device Licenses is set to 2
     <span style="color:#0000ff;"><strong>And</strong></span> all devices have been removed 
  
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 1</strong></span></span>: Register a device successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a device is registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the device
     <span style="color:#0000ff;"><strong>And</strong></span> the device appears on the License Portal in the device list
    
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 2</strong></span></span>: Register a second device successfully
    <span style="color:#0000ff;"><strong>Given</strong></span> a device is registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a second device is registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the device
     <span style="color:#0000ff;"><strong>And</strong></span> the device appears on the License Portal in the device list

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 3</strong></span></span>: Fail to register a third device
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a third device is registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application does not register the device with a <span style="color:#ff6600;">"All device licenses have been used"</span> error
     <span style="color:#0000ff;"><strong>And</strong></span> the device appears on the License Portal in the device approval list

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 4</strong></span></span>: Relinquish a device to register a third device
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
      <span style="color:#0000ff;"><strong>And</strong></span> a third device has failed to register
    <span style="color:#0000ff;"><strong>When</strong></span> the first device is removed from the list on the License Portal
     <span style="color:#0000ff;"><strong>And</strong></span> the third device is again registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the device
     <span style="color:#0000ff;"><strong>And</strong></span> the first device no longer appears on the License Portal in the device list
     <span style="color:#0000ff;"><strong>And</strong></span> the third device appears on the License Portal in the device list

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 5</strong></span></span>: Create an Admin device and register a further device
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> the second device is made an Admin device on the License Portal
     <span style="color:#0000ff;"><strong>And</strong></span> a third device is  registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the third device
     <span style="color:#0000ff;"><strong>And</strong></span> the first device appears on the License Portal in the device list
     <span style="color:#0000ff;"><strong>And</strong></span> the second device appears on the License Portal in the device list as an Admin device
     <span style="color:#0000ff;"><strong>And</strong></span> the third device appears on the License Portal in the device list

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 6</strong></span></span>: Create an Admin device from an unregistered device
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
      <span style="color:#0000ff;"><strong>And</strong></span> a third device is registered using the QR code provided on the License Portal
      <span style="color:#0000ff;"><strong>And</strong></span> the third device appears on the License Portal in the device approval list
    <span style="color:#0000ff;"><strong>When</strong></span> the third device is made into an Admin device
    <span style="color:#0000ff;"><strong>Then</strong></span> the device appears on the License Portal in the device approval list as an Admin device
    
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 7</strong></span></span>: All devices can be used by different technicians
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a technician is logged in on one device
    <span style="color:#0000ff;"><strong>Then</strong></span> a second technician can log in on the second device   
    
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 8</strong></span></span>: Prevent log on by a user on two devices
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a technician is logged in on one device
     <span style="color:#0000ff;"><strong>And</strong></span> the same technician is logged in on the second device    
    <span style="color:#0000ff;"><strong>Then</strong></span> login should be prevented with a <span style="color:#ff6600;">"Cannot log in on more than one device"</span> error

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 9</strong></span></span>:Log a user off a device and log onto another
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
     <span style="color:#0000ff;"><strong>And</strong></span> a technician is logged in on one device
     <span style="color:#0000ff;"><strong>And</strong></span> the same technician prevented from being logged in on the second device
    <span style="color:#0000ff;"><strong>When</strong></span> the technician is logged off the first device
     <span style="color:#0000ff;"><strong>And</strong></span> the technician is logged in on the second device    
    <span style="color:#0000ff;"><strong>Then</strong></span> the login should be successful

</pre>

<br/>

<pre><span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Feature</strong></span></span>: Concurrent Licenses
  As a GHA mobile application customer I want to buy concurrent licenses so multiple devices can be registered but only a certain (licensed) amount used at one time

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Background</strong></span></span>: In the License Portal:
    <span style="color:#0000ff;"><strong>Given</strong></span> Mobile Field Service has concurrent licensing enabled
     <span style="color:#0000ff;"><strong>And</strong></span> Device Licenses is set to 2
     <span style="color:#0000ff;"><strong>And</strong></span> all devices have been removed 

  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 1</strong></span></span>: Register a device successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a device is registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the device
     <span style="color:#0000ff;"><strong>And</strong></span> the device appears on the License Portal in the device list
    
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 2</strong></span></span>: Register a second device successfully
    <span style="color:#0000ff;"><strong>Given</strong></span> a device is registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a second device is registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the device
     <span style="color:#0000ff;"><strong>And</strong></span> both devices appear on the License Portal in the device list
    
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 3</strong></span></span>: Register a third device successfully
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a third device is registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the device
     <span style="color:#0000ff;"><strong>And</strong></span> all three devices appear on the License Portal in the device list
         
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 4</strong></span></span>: Register a fourth device successfully
    <span style="color:#0000ff;"><strong>Given</strong></span> three devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a fourth device is registered using the QR code provided on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> the application successfully registers the device
     <span style="color:#0000ff;"><strong>And</strong></span> all four devices appear on the License Portal in the device list
     
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 5</strong></span></span>: Create an Admin device
    <span style="color:#0000ff;"><strong>Given</strong></span> three devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> one of the devices is made an Admin device on the License Portal
    <span style="color:#0000ff;"><strong>Then</strong></span> two of devices appear on the License Portal in the device list
     <span style="color:#0000ff;"><strong>And</strong></span> the third device appears on the License Portal in the device list as an Admin device
    
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 6</strong></span></span>: Login on a single device
    <span style="color:#0000ff;"><strong>Given</strong></span> three devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a technician logs in on one of the devices
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
     <span style="color:#0000ff;"><strong>And</strong></span> the login is seen on the login list on the License Portal
    
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 7</strong></span></span>: Login on two devices
    <span style="color:#0000ff;"><strong>Given</strong></span> three devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> two technicians log in on two of the devices
    <span style="color:#0000ff;"><strong>Then</strong></span> both logins are successful
     <span style="color:#0000ff;"><strong>And</strong></span> the logins are seen on the login list on the License Portal
     
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 8</strong></span></span>: Login on three devices
    <span style="color:#0000ff;"><strong>Given</strong></span> three devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> two technicians log in successfully on two devices
     <span style="color:#0000ff;"><strong>And</strong></span> both technicians can be seen on the login page of the license portal
     <span style="color:#0000ff;"><strong>And</strong></span> a third technician attempts to log in on the third device
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is unsuccessful
     <span style="color:#0000ff;"><strong>And</strong></span> the third login is not seen on the login list on the License Portal
     
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 9</strong></span></span>: Log a user out to log in another
    <span style="color:#0000ff;"><strong>Given</strong></span> three devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> two technicians log in successfully on two devices
     <span style="color:#0000ff;"><strong>And</strong></span> both technicians can be seen on the login page of the license portal
     <span style="color:#0000ff;"><strong>And</strong></span> a third technician fails to log in on the third device
     <span style="color:#0000ff;"><strong>And</strong></span> one of the logged in techncicians is logged out
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
     <span style="color:#0000ff;"><strong>And</strong></span> the first login is not seen on the login list on the License Portal
     <span style="color:#0000ff;"><strong>And</strong></span> the third login is  seen on the login list on the License Portal
     
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario 10</strong></span></span>: Prevent log on by a user on two devices
    <span style="color:#0000ff;"><strong>Given</strong></span> two devices are registered successfully
    <span style="color:#0000ff;"><strong>When</strong></span> a technician is logged in on one device
     <span style="color:#0000ff;"><strong>And</strong></span> the same technician is logged in on the second device    
    <span style="color:#0000ff;"><strong>Then</strong></span> login should be prevented with a <span style="color:#ff6600;">"Cannot log in on more than one device"</span> error
</pre>

<br/>

## Web Applications
<br/>
<pre>
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Background</strong></span></span>: 
    <span style="color:#0000ff;"><strong>Given</strong></span> the user is set up against a single customer
</pre>
<br/>
<pre>
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Single login without 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using the application password
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
</pre>

<pre>  
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Single login with 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using the application password
    <span style="color:#0000ff;"><strong>Then</strong></span> an email is sent to the user with an authorisation code
     <span style="color:#0000ff;"><strong>And</strong></span> a screen is presented with the authorisation code
    <span style="color:#0000ff;"><strong>When</strong></span> the user enters the authorisation code from the email
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
    
</pre>

<pre>
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Single login linked to Epicor without 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using their Epicor password
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
</pre>

<pre>  
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Single login linked to Epicor with 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using their Epicor password
    <span style="color:#0000ff;"><strong>Then</strong></span> an email is sent to the user with an authorisation code
     <span style="color:#0000ff;"><strong>And</strong></span> a screen is presented with the authorisation code
    <span style="color:#0000ff;"><strong>When</strong></span> the user enters the authorisation code from the email
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
    
</pre>
<pre>
  <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Background</strong></span></span>: 
    <span style="color:#0000ff;"><strong>Given</strong></span> the user is set up against multiple customers
</pre>
<br/>
<pre>
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Multiple logins without 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using the application password
    <span style="color:#0000ff;"><strong>Then</strong></span> the user is presented with a choice of customer logins
    <span style="color:#0000ff;"><strong>When</strong></span> the user chooses a customer
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful    
    
</pre>
<pre>  
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Single login with 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using the application password
    <span style="color:#0000ff;"><strong>Then</strong></span> an email is sent to the user with an authorisation code
     <span style="color:#0000ff;"><strong>And</strong></span> a screen is presented with the authorisation code
    <span style="color:#0000ff;"><strong>When</strong></span> the user enters the authorisation code from the email
    <span style="color:#0000ff;"><strong>Then</strong></span> the user is presented with a choice of customer logins
    <span style="color:#0000ff;"><strong>When</strong></span> the user chooses a customer
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
    
</pre>
<br/>
<pre>
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Single login linked to Epicor without 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using their Epicor password
    <span style="color:#0000ff;"><strong>Then</strong></span> the user is presented with a choice of customer logins
    <span style="color:#0000ff;"><strong>When</strong></span> the user chooses a customer
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
</pre>

<pre>  
   <span style="text-decoration:underline;"><span style="color:#0000ff;"><strong>Scenario</strong></span></span>: Single login linked to Epicor with 2FA
    <span style="color:#0000ff;"><strong>Given</strong></span> a user has Epicor Connection disabled
      <span style="color:#0000ff;"><strong>And</strong></span> the user has two factor authentication disabled
    <span style="color:#0000ff;"><strong>When</strong></span> the user logs into the web application using their Epicor password
    <span style="color:#0000ff;"><strong>Then</strong></span> an email is sent to the user with an authorisation code
     <span style="color:#0000ff;"><strong>And</strong></span> a screen is presented with the authorisation code
    <span style="color:#0000ff;"><strong>When</strong></span> the user enters the authorisation code from the email
    <span style="color:#0000ff;"><strong>Then</strong></span> the user is presented with a choice of customer logins
    <span style="color:#0000ff;"><strong>When</strong></span> the user chooses a customer
    <span style="color:#0000ff;"><strong>Then</strong></span> the login is successful
</pre>

Concurrent Liensing