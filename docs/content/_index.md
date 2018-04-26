+++
title= "Let's Event Source - Documentation"
date= 2018-04-26T06:35:30-07:00
description = ""
draft= false
+++

# Event Sourced Systems Made Simple

**The LESTER Stack - “Let’s Event Source Together”**

![Lester Pipline](LESTER-stack-diagram.png)

**LESTER takes an event storming and turns it directly into deployment-ready commands, events, documentation and infrastructure. It makes prototyping and implementation of an event based system simple and keeps it closely aligned with business objectives and requirements. Its goal is to remove many of the hurdles associated with adopting CQRS/ES.**

The LESTER tooling is currently in alpha, but has been used for Real Life projects.

### In:

* Event Markdown (EMD) is a machine- and remote collaboration friendly way of capturing the results of an [event storming](http://ziobrando.blogspot.ca/2013/11/introducing-event-storming.html). It attempts to distract as little as possible from what makes the stickies & paper-on-the-wall version so successful and to augment it: Easy to do. Brings business and technical people together. Fun. Deliberately fuzzy to discourage getting lost in detail not (yet) needed. 

* Event Markup Language (EML) is a simple implementation-agnostic YAML DSL for describing event sourced systems, custom business rules and read models.

### Out:

* Fully functional, scalable and maintainable CQRS/ES system.
* API, with Swagger API playground.
* Language-agnostic. The reference implementation builds systems in NodeJS. An experimental Golang version exists. There is a prototype for turning an event markup language spec into a serverless implementation on Azure.
* Currently supported event store: https://eventstore.org.
* Read model storage in Postgres, LevelDB, Cassandra or in memory.
