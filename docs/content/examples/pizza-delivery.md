+++
title = "Pizza Delivery"
description = "In 30 Minutes Or It's Free"
weight = 1
+++

### A simple introductory example.

> **How we do it at "Yolanda's Always Hot & Fresh?** 

People pick their pizza from the online menu, special, custom, all-time favourites, drinks, etc. and phone us to order. We get their phone number and address. When a pizza is ready, it shows up on the "To Be Delivered" board. A driver makes the delivery and then marks the order as "Delivered". 

> **If more than 30 minutes have passed since the order was placed, the order is put on the "Refund"  screen.**

### Event Markdown 

```
Employee Created // employeeId, email, encryptedPassword
User Profile*
Employee List*
Company Created // employeeId, companyId, description
Company Profile*
Menu Item Added // companyId, menuItemId, description, price
Menu*
Order Created // orderId, employeeId
Order Item Added // orderId, menuItemId, quantity, price
Order Item Added // orderId, menuItemId, quantity, price
Order Item Added // orderId, menuItemId, quantity, price
Order Delivery Address Provided // orderId, address, phoneNo
Order Placed // orderId, dateTime
"To Be Delivered" Board*
Order Delivered // orderId, employeeId, dateTime
Refund Screen* // orderId, phoneNo, totalRefundAmount, dateTimePlaced, dateTimeDelivered
```