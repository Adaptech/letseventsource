+++
title= "What do you mean by \"complete\" event sourced system?"
date= 2018-04-26T06:43:00-07:00
description = "A \"complete\" CQRS/ES system is transactionally consistent, cohesive and loosely coupled."
draft = false
alwaysopen = true
weight=600
+++

A “complete” event sourced system ...

* Records changes to the state of a state machine as a stream of events over time.
* Can re-build the current state of a state machine from recorded events.
* Is transactionally consistent:  The current state of a state machine (a.k.a. transaction, event stream, or if DDD is your thing, aggregate) contains all the data needed to make decisions on what the next state should be when commands are processed. Commands succeed or fail atomically.
* Commands result in state changes.
* Commands must contain a reference to the state machine whose state they change.
* State changes are recorded as time stamped events stated in past tense.
* Events must contain a reference to the state machine whose state changes they record.
* Read models must not contain any data which they cannot get from subscribing to events.
* Commands cannot act on state machines which do not exist. Unless executing the command results in creation of a new state machine.
* Command parameters cannot reference ids of state machine instances which do not exist.
