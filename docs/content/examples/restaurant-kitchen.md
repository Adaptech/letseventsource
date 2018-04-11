+++
title = "Restaurant"
description = "Feeding The Masses"
weight = 1
+++

This can be used to practice with bounded contexts and context maps. The Kitchen example can be context mapped to the columns of a [Kanban board](/examples/kanban-board/)

> The kitchen point job is the toughest. You have to coordinate everybody, keep an eye on food quality, do the plating and ensure the dish completion times are the same within a table.

```
# Kitchen
Order Received
Order Started
Order Plated

# Expediter 
Order Received
Plates Allocated To Tables
Order Delivered

# Server
Order Taken
Order Placed
Order Received For Delivery
Order Delivered
Order Paid
```

This is an example with three contexts and context maps:

- "Order Placed" for a server means "Order Received" for the Kitchen.
- "Order Plated" for the kitchen indicates "Order Received For Delivery" for the Server.

Without bounded contexts the language wouldn't be quite right:

| Kitchen Workflow                |                                                                                              |
|----------------------------|----------------------------------------------------------------------------------------------|
| Order Taken                |                                                                                              |
| Order Placed               | (Kitchen: "Order placed means that I have received an order which needs to be plated.") |
| Order Started              |                                                                                              |
| Order Plated               | (Expediter: "Order plated means that I have received an order for allocation to tables.")    |
| Plates Allocated To Tables | (Server: "Plates allocated to tables means there is an order for delivery.")                 |
| Order Delivered            |                                                                                              |
| Order Paid                 |                                                                                              |