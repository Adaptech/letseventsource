+++
title= "2. Turn it into Event Markdown (EMD)"
date= 2018-05-02T10:29:57-07:00
description = "Event Markdown (EMD) is a simple language used to capture the results of an event storming."
draft= false
+++

**Event Markdown (EMD) is a simple language used to capture the results of an event storming.**


![Eventstorming-graph.1.png](/tutorial/Eventstorming-graph.1.png)

**Event Markdown (EMD):**

```bash

Add Item -> 
Todo Added // description, dueDate
Set Status -> 
Todo Status Changed 
TODO List* // description, dueDate

```

* ```# This is a commment.```.

* This is a command: ```Command ->```. Commands can have parameters: ```Add Item -> // description, dueDate```

* And this is what events look like: ```Something Happened```. Or, with properties: ```Todo Added // description, dueDate```

* Finally, a document (also known as a read model): ```TODO List*``` or ```TODO List* // todoId, description, dueDate, status```

**Enter EMD at https://webeventstorming.com to see it as a graph:**

![Eventstorming.1.png](/tutorial/Eventstorming.1.png)

