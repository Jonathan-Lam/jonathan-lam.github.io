---
title: SPOT Backend
layout: post
date: 2023-09-15 12:00 -800
categories: [software, backend]
tags: [SPOT]
image:
  path: /assets/SPOT_Backend/gateway_states.png
---
### State Diagram Overview
Below is a flowchart of the SPOT flow state. In summary, we check the parking spot's occupancy until we determine a vehicle has arrived. The tower sensor unit waits and senses for the SPOT mobile app on the user's smartphone through Bluetooth and pushes the user and spot ID to the Gateway unit. The Gateway then creates an API call to the Google Cloud Platform's App Engine to note the change of state and checks the databases to see if the user had a parking pass. If not, a payment option is provided on the mobile app; otherwise the parking spot is validated and the user has parked successfully.

![Flowchart](/assets/SPOT_Backend/Flowchart.png)
_State Flowchart_

We use the App Engine for handling web API calls and hosting the website. We use Cloud SQL for storing user info and parking spot states.

![Diagram sketch](/assets/SPOT_Backend/rough_diagram.jpg)
_Diagram sketch_

###  MySQL
We have 4 tables for our MySQL schema:

1. spot_table
![Spot Table](/assets/SPOT_Backend/spot_table.png)
_Spot Table_
We record spot information such as its ID, status, user ID its currently linked to, hourly rate, and parking lot it belongs to.

2. user_table
![User Table](/assets/SPOT_Backend/user_table.png)
_User Table_
We keep track of user info here, such as their name, ID assigned to them, permit type, email, and current account balance.

3. transaction_table
![Transaction Table](/assets/SPOT_Backend/transaction_table.png)
_Transaction Table_
We track the payment transactions of users with the given timestamp, user ID, payment amount, and parking spot/parking lot they occupied.

4. spot_status_table
![Spot Status Table](/assets/SPOT_Backend/spot_status_table.png)
_Spot Status Table_
We track the status change of each spot by recording the spot ID, timestamp, status, and parking lot the spot belongs to.

### App Engine and APIs
We use REST APIs to manage records in MySQL tables and allow access to data for the mobile app, gateway, and website. Below is a summary of the web APIs:

#### Gateway Handlers:
- GET - Returns verified parking spots for the specific gateway
- POST - Updates sensor status in the database

#### Mobile App Handlers:
- POST - Verifies the given spot with the user ID

Payment:
- POST - Handles deduction of funds from user account

Spots:
- GET - Returns number of open spots in a parking lot

Login:
- POST - Verifies the user login information

Mobileinfo:
- POST - Returns the account information to the user

Bluetooth:
- POST - Returns parking lots and spots of bluetooth strings for bluetooth differentiation

#### Website Handlers:
MainPage:
- GET - Returns website home page index.html

Users:
- GET - Returns Users.html page
- POST - Lists user accounts from search

Edit:
- GET - Returns form for editing accounts
- POST - Updates account information

Delete:
- POST - Deletes user account from database

Add:
- POST - Creates user entry in user database

Logs:
- GET - Return Logs.html page
- POST - Lists transaction history entries from search

Occupation:
- POST - Lists occupation history entries from search

NorthRemote:
- GET - Returns NorthRemote.html

EastRemote:
- GET - Returns EastRemote.html

Baskin:
- GET - Returns Baskin.html

get_spotinfo:
- GET - Returns spot information for the parking map

get_parkinglot:
- GET - Returns list of spots and their statuses for a parking lot
