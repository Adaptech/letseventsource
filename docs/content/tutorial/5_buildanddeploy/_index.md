+++
title= "5. Build and deploy the API"
date= 2018-05-02T10:29:57-07:00
description = "Build a CQRS/ES system in NodeJS and deploy it with docker-compose."
draft= false
+++

Run the following: 

```bash

les-node -b Eventsourcing.eml.yaml \
&& cd api \
&& npm install \
&& docker-compose up -d \
&& docker-compose restart api

```

**This implements the TODO list API in NodeJS, with in-memory read models and https://eventstore.org as event log.**

 It is possible to configure the system to use Postgres or LevelDB for read model storage, but the generated ```docker-compose.yml``` contains a dev enviroment setup where everything is in memory and all events get re-played every time the API docker container is re-started. The source code can be found in ```./api```.
