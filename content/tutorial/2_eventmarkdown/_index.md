+++
title= "2. Turn it into Event Markdown (EMD)"
date= 2018-05-02T10:29:57-07:00
description = "Event Markdown (EMD) is a simple language used to capture the results of an event storming."
draft= false
+++

{{% alert theme="info" %}}**Event Markdown (EMD) is a simple language used to capture the results of an event storming.**{{% /alert %}}


![Eventstorming-graph.1.png](/tutorial/Eventstorming-graph.1.png)

**Event Markdown (EMD):**

```bash

Add Item -> 
Todo Added // description, dueDate
Set Status -> 
Todo Status Changed 
TODO List* // description, dueDate

```

{{% panel theme="success" header="**Comments**" %}}
```# This is a comment.```
{{% /panel %}}

{{% panel theme="success" header="**Commands**" %}}
* This is a command:

**Do Something ->**

* Commands can have parameters:

**Add Item -> // description, dueDate**
{{% /panel %}}

{{% panel theme="success" header="**Events**" %}}

* And this is what events look like:

**Something Happened**

* With properties: 

**Todo Added // description, dueDate**
{{% /panel %}}

{{% panel theme="success" header="**Documents**" %}}

* Documents (also known as a read models):

**TODO List***

* Or, with properties:

**TODO List* // todoId, description, dueDate, status**
{{% /panel %}}

**Enter EMD at https://webeventstorming.com to see it as a graph:**

![Eventstorming.1.png](/tutorial/Eventstorming.1.png)

