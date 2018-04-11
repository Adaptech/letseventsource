+++
title = "Bike From Mike"
description = "Distributed bike rentals"
weight = 1
+++
### "BikeFromMike" is Mike's bike rental company. 

**He offers retailers, restaurants and other businesses a side line in bike rentals because that makes for more potential customers visiting the premises and additional revenue.**

Mike provides each business with some rental bikes. Renters can see where they can pick up a bike on a nice map which shows locations and availability (while prominently featuring the products and services of participating businesses). Renters pay using the app, pick up their steed and drop it off at any other participating location. As an encouragement to visit other BikeFromMike locations and mayBike From Mikebe have a nice meal or do some shopping the "clock stops" while they are on the premises, adding the time spent there to the rental time free of charge. Mike can see when locations are about to run out of rental stock and spends much of his time ferrying bikes from surplus locations to places in need.

![bike](/images/bike.png)

```
Business Signed Up // businessId, locationId, description
Bike Added To Inventory // bikeId, description
Bike Delivered // bikeId, businessId, locationId
Bike Location & Inventory Report*
Bike Availability Map By Location*
Renter Registered // renterId
Payment Received
Bike Rented // rentalId, renterId, locationId, bikeId
Bike Rental Returned // rentalId
```