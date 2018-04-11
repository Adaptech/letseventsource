+++
title = "Shopping Cart"
description = "Online purchasing - what are the bounded contexts?"
weight = 1
+++

#### The Shopping Cart example shows a full "real life" event storming from end to end, with multiple bounded contexts. It's good enough to generate an API using the Adaptech platform.

Shopping carts are boring, but everybody is enough of a "domain expert" to make it a suitable example for a workshop.

> "We purchase inventory. When it's there we put it into the product catalog where people can see it. They can add products to a shopping cart at any time. We only ask them to register on the site when they want to check out the cart. After that they can place an order and give us payment information so we can process the payment. They we get what they ordered from the inventory and ship it."

## Bounded Contexts

- Inventory management
- Product catalog 
- Shopping cart / ordering
- Order fulfillment
- User registration / authentication

## Event Storming

For https://webeventstorming.com:

```
# Online Ordering

Create Inventory Item-> // sku, description
Inventory*
Inventory Item Created // sku, description
Record New Inventory-> // sku, quantity
Inventory Item Stocked // sku, quantity

Create Product-> // productId, sku, hasInventory, description, retailPrice 
Product Added To Catalog // productId
Product Catalog*

Add Item To Cart-> // cartId, productId, quantity
Shopping Cart Created // cartId
Shopping Cart*
Shopping Cart Item Added // cartId, productId, quantity

Register -> // userId, email, password
User Registered // userId, email, encryptedPassword
User Profile*
User Authenticated // userId
Shopping Cart Associated With User // userId, cartId

Check Out -> // cartId
Shopping Cart Checked Out // cartId
Order Created // orderId
Order*
Order Item Added // orderId, sku, productId, quanity, retailPrice
My Orders*

Provide Payment Info-> // userId, creditCardNo, nameOnCard, expiryDate
Payment Info Provided // userId, linkToEncryptedCreditCardVault
Payment Info*
Pay-> // paymentId, creditCardNo, orderId
Payment Processed // paymentId 
My Payments*

Place Order-> // userId, orderId
Order Placed // orderId

# Fulfill the order by adding items from inventory to the package to be shipped:
Add Item From Inventory-> // orderId, sku, quantity
Inventory Item Added To Order // orderId, sku, quantity

# When all the ordered items have been added to the package, the order is ready for shipment:
Order Ready // orderId

Mark Order As Shipped-> // orderId, dateShipped
Order Shipped // orderId, dateShipped

Mark Order As Delivered-> // orderId, deliveryDate
Order Delivered // orderId, deliveryDate

```