---
title: AuthenticationSvcAPI
description: 
published: true
date: 2024-01-19T14:58:46.541Z
tags: 
editor: markdown
dateCreated: 2023-10-03T13:19:33.651Z
---

# Web Application APIs

## Login 

1. Enter username and password

Once entered, the following will be verified:

If the user does not exist → ```ReturnError()```
If the user has been suspended → ```ReturnError()```

2. Select the customer ID

Once selected, the following will be verified:

If the customer ID is empty, then it will check how many customer ids are linked to the application id. 

If there are 0 → ```ReturnError()```
If there are 1 → It will set ```customerId``` to the first ( and only ) item in customer ids.

If there are more than 1:

Iterate through each customer record in the customer ids and return a model that will display the different ids to choose from.

It will check if the user is an Epicor user by comparing the details entered in the MFS app to the ones in Epicor. It will check if 2FA is enabled and generate a token for confirmation if it is. The application id will be verified to see if it is suspended or if it is correctly registered to the customer, or if a specific customer from that id has been suspended.

## Check Licenses 

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Gets and validates application against current session? Checks that there are enough sessions available.

3. Gets the amount of licenses available and how many are available. Outputs true if there are licenses available and false if there are none, along with an error message informing the user.


## Session Check 

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Gets and validates application against current session? 

3. Gets the amount of licenses registered and how many are available. If there are no licenses available it will inform the user with that message. If there are sessions available it will output ```true``` and how many sessions are available, including the number of licenses.

## Session List 

Checks if the ModelState is valid, if not output status code 401 and message is set to: "Invalid Token".

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

It will iterate through all of the sessions in session models and then output whether it was a success or not, a concurrent licence check and a message if needed. 

3. Maps and displays an output model, listing all the current sessions.

## Session Clear 

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Gets and validates application against current session? Checks the web token is valid and checks if the session exists.

4. Returns a success message.

Returns a success response, message and concurrent licence check, else it will return a 401 error with "Invalid Token" error.

## Credentials

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Reads the credentials of the token, validates customerId, if valid: gets the name of the customer. Checks if the user is an epicor user, outputs true if so and false if not.

3. Gets credentials from current device and outputs:

## Approve 

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Checks if user does not exist or is suspended, if so return error. Checks if user and customer guid is the same as existing credentials, if no match is found in either, output error.

3. Generates a login token with user details. checks if customer application is suspended or null. 

Generates a new refresh token, outputs login model.

## Regenerate Code

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Checks if the user is null or has been suspended. Checks if application and if customer is null, if so: ```_success``` is set to ```false```. 

3. Attempts to parse ```resultUser``` and ```resultCustomer``` into Guid objects.

4. Generates a 2FA code, ```response.Success``` is set to ```true``` and a code is emailed to the recipient.

## Refresh Token

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Validates the token as a json web token. Checks if the token exists, is expired, has been used, has been revoked, or does not match the saved token.

3. Generates a new refresh token with ```GenerateRefreshToken```, creates new refresh token object.

4. Outputs token and new refresh token.

## Logout 

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Calls ```Logout``` with ```email``` and ```token``` as parameters.

3. Gets and validates application against current session? Checks if json web token is valid and checks if session exists.

4. Returns either ```true``` or ```false``` with message as "invalid token"

## Password

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Reads the token, attempts to parse the user id as a Guid object.

3. It checks that the password is not the same as the old password, whether it is the current users password, and if the user is an epicor user it will ask them to change it in epicor.

## Password Reset

1. Validates the token through a method that returns true if the token is matched. Checks if the token is empty, if empty, return unathorised.

2. Reads and validates the token.

3. Checks if customer / user guid exists, customer exists, or if the user is an epicor user ( they will be asked to change password via epicor ).

4. Sets a new password, generates new password and emails to the recipient.
