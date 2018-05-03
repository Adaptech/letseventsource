+++
title= "3. Turn the Event Markdown \"Green\""
date= 2018-05-02T10:29:57-07:00
description = "\"Green\" EMD is event markdown which follows some simple conventions and has enough information to use it to generate a working event sourced CQRS API from it."
draft= false
+++

{{% alert theme="info" %}}**"Green" EMD is event markdown which follows some simple conventions and has enough information to use it to generate an event sourced microservice API from it.**{{% /alert %}}

To validate an EMD file for greenness, see ```les validate --help```.

Save this to a file called ```Eventstorming.emd```:

```bash

# TODO List
Add Item -> // description, dueDate
Todo Added // description, dueDate
Set Status -> // status
Todo Status Changed // status
TODO List* // todoId, description, dueDate, status

```

Compared to the previous EMD for the TODO List event storming, the new version has additional properties and other information needed to create a CQRS/ES system.

**["Green" EMD Cheat Sheet .pdf](https://github.com/Adaptech/letseventsource/blob/master/EMD-Cheatsheet-0.10.0-alpha.pdf)**

![eventstorming](/tutorial/EMD-Cheatsheet-0.10.0-alpha.png)