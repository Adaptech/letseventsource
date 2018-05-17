+++
title= "4. Convert EMD to EML"
date= 2018-05-02T10:29:57-07:00
description = "Event Markup Language (EML) is a YAML schema which describes the structure of a CQRS/ES system."
draft= false
+++

{{% alert theme="info" %}}**Event Markup Language describes the structure of a CQRS/ES system.**{{% /alert %}}

Run the following command:

```bash 

les convert

```

**Event Markup Language is a YAML schema for describing event sourced systems which make use of the CQRS ("Command Query Responsibility Segregation") pattern. EML makes such designs accessible to tools like ```les validate``` which act as a kind of "architect in a box".**

**This makes it possible to automatically validate whether implementing the design is likely to result in a good event sourced system:**

* Will it have transactional integrity?
* Does it have all the necessary events and event properties to make it possible to determine the current state of aggregates/streams/state machines by re-playing them from the event store?
* Do the events have all the necessary information for building the read models?
* Have certain business rules been considered when modeling the domain? For example, is it possible to send an invoice after it's been deleted? (It probably shouldn't be.)

EML is implementation language agnostic. It doesn't matter what stack the CQRS/ES system will be written in. At the moment there is a builder for EML -> NodeJS (```les-node```). There's also EML -> Swagger spec to give developers a nice UI to play with the system's API. A EML -> Golang implementation is in early alpha.

{{% notice tip %}}
Try  "```les --help```"
{{% /notice %}}