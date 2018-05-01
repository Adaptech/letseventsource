+++
title= "What use is this? I'm stuck in legacy code."
date= 2018-04-26T06:43:00-07:00
description = "How to benefit from CQRS and event sourcing when surrounded by legacy code."
draft = false
alwaysopen = true
weight=800
+++
 
[There's a white paper for that.](https://insights.adaptechsolutions.net/legacy-evolution-whitepaper/#adaptech-github-letseventsource)

The LESTER stack has been used to prototype legacy integrations which make the old system "talk" about itself. It does that by publishing business events which new "microservices" can subscribe to. If a two-way integration is needed the legacy can subscribe to business events from the new systems. This can lead to establishing the legacy as its own bounded context which integrates with other systems via pub-sub and domain events and establishes options for it's eventual replacement.

Such replacement, complete or partial, is invariably messy, with a lot of trade-offs to be made. Most of them are business decisions rather than technical considerations. Domain Driven Design helps a lot with establishing criteria for making these because it helps with understanding where one spaghetti ends and the next one begins.

Eric Evans's [four strategies for dealing with legacy systems](http://dddcommunity.org/library/evans_2011_2/) are a great inspiration for how to write good code in that kind of environment.

[This talk](https://www.infoq.com/presentations/Legacy-Code-DDD) shows examples on how they might be applied.



