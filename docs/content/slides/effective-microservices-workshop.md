+++

title = "Event Sourced Microservices with LESTER"
date = "2017-04-24T18:36:24+02:00"
type="slide"

theme = "solarized"
[revealOptions]
transition= 'concave'
controls= true
progress= true
history= true
center= true
+++

# Event Sourced Microservices with LESTER

![Adaptech Logo](/images/adaptech-logo-big-1.png)
---

## Introduction To Event Sourcing & CQRS

- Manage microservice coupling & cohesion
- Integrate legacy with events
- Simplify code
- Less meetings, less planning, better results.

---


## Event Storming

![Webventstorming Example](/images/webeventstorming-example.png)

___

# The Human Eventstorming
___

## Why?

- Great for exploring large complex systems.
- Takes only a couple of hours.
- Less crossed wires.
- Less meetings, less "documentation".
- Shared understanding, understood by all.
- Fun!
___

## How to Event Storm

![Adaptech Logo](/images/eventstorming-eventstormed.png)

___

#### https://webeventstorming.com

<iframe width="1120" height="720" src="https://www.youtube.com/embed/1Pb4a8lr74E" frameborder="0" allowfullscreen></iframe>

Note: "EMD (Event Markup Language) is a simple text notation for event storming online. We also use it to generate APIs for the Adaptech Platform. Basically, any line with a -> is a command. Anything with a * is a document. Everything else is an event."
___

# Bike From Mike
**Envelope 1**
![bike](/images/bike.png)

Note: 
1. "Take a look at these requirements and do an event storming."

2. "That's the 'happy path'. Now ... spend two minutes on a second event stream which shows what happens when (deletion, etc.)"

___
## Bike From Mike

![BikeFromMike](/images/bikefrommike-eventstorming.png)

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

___
## Recipe Reviews

What’s tasty? This site is about ranking recipes - enter yours and watch the number of stars go up. Should your creation be “Culinary Star Of The Month” by gaining the most 5 star ratings you get a $500 gift certificate.

Let’s make a site where aspiring and seasoned chefs can enter their recipies. We do need their email address to tell them if they won and they want to be able to edit and delete their creations. Site visitors are able to assign 1 to 5 stars and add comments.

___
# No Tech Jargon

* Ubiquitous Domain Language - practice it!
* Events are "timeless", surviving technology fads & obsolescence.

> If we re-built it on a different stack - would this spec still apply?"


---
# Bounded Contexts: Finding Service Boundaries

___

## Strategic Domain Driven Design

> "A bounded context is the context within which a ubiquitous language applies."


# Restaurant Workflow

- Server
- Kitchen
- Expediter

![Restaurant](/images/restaurant-example.png)

___

|               | Restaurant Kitchen Workflow                                                                                    |
|----------------------------|----------------------------------------------------------------------------------------------|
| Order Taken                |                                                                                              |
| Order Placed               | (**Kitchen**: "Order placed means that I have received an order which needs to be plated.") |
| Order Started              |                                                                                              |
| Order Plated               | (**Expediter**: "Order plated means that I have received an order for allocation to tables.")    |
| Plates Allocated To Tables | (**Server**: "Plates allocated to tables means there is an order for delivery.")                 |
| Order Delivered            |                                                                                              |
| Order Paid                 |                                                                                              |


___

Continued... 

|               | Restaurant Kitchen Workflow                                                                                    |
|----------------------------|----------------------------------------------------------------------------------------------|
| Plates Allocated To Tables | (**Server**: "Plates allocated to tables means there is an order for delivery.")                 |
| Order Delivered            |                                                                                              |
| Order Paid                 |                                                                                              |

___
## Three (Ubiquitous) "Languages"

#### Server

![server](/images/restaurant-server-example.png)

#### Kitchen

![kitchen](/images/restaurant-kitchen-example.png)

#### Expediter

![server](/images/restaurant-expediter-example.png)

___ 

# Kanban Board

- TODO
- Doing
- Done

Note: 
"Using the Post-Its on the tables, event storm a simple Kanban board."
After 5 minutes, show the [Kanban board example](https://sites.google.com/adaptechsolutions.ca/workshop/kanban-board)

___

# Context Mapping Restaurant Kanban

How do these  map to the Kanban board TODO/Doing/Done?

```
# Kitchen
Order Received
Order Started
Order Plated
```

Note:
1. Discuss for 1 minute: How would the events for the kitchen be mapped to the events on the Kanban board? 
1. Ask a table group to present what they found.
1. Show other examples which could be mapped to a TODO list in this way, then give table groups two minutes to come up with their own examples.

```
Bug Found
Bug Assigned
Bug Fixed
```

```
Cab Ride Requested
Cab Ride Started
Cab Ride Paid
```

___

# Context: Expediting

```
Order Received
Plates Allocated To Tables
Order Delivered
```
___

# Context: Server

```
# Server
Order Taken
Order Placed
Order Received For Delivery
Order Delivered
Order Paid
```

___


# Find The Bounded Contexts

[sites.google.com/adaptechsolutions.ca/workshop/shopping-cart](https://sites.google.com/adaptechsolutions.ca/workshop/shopping-cart)

![shopping-cart](/images/shopping-cart-example.png)

Note:
"Copy the EMD into webeventstorming.com. Then group commands and events which belong together. Put a comment for the name of the bounded context. WRITE DOWN THE EVENTS FOR LATER. Note: Documents can belong to more than one context!" (5 minutes)

---

# Hackathon

![manwithhammer](/images/man-with-hammer-300px.png)

