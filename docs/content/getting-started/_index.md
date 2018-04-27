+++
title= "Getting Started"
date= 2018-04-27T08:48:27-07:00
description = "Hello LES - Go directly from event storming to a functioning event sourced microservice."
draft= false
weight=100
+++

### Prerequisites

* [NodeJS 8.11.1 LTS](https://nodejs.org/en/) or better
* [docker-compose](https://docs.docker.com/compose/install/)

### Installation

**Latest version from source:**

```bash
git clone https://github.com/Adaptech/les.git
make install
```

... or ... 

[Instructions for Linux, Windows Mac & Docker](INSTALL.md)


### Hello World

**Step 1:**

Create an [Event Markdown](https://webeventstorming.com) file. Event Markdown (EMD) is a simple language used to describe an [event storming](https://ziobrando.blogspot.ca/2013/11/introducing-event-storming.html):

```bash
# TODO List
Add Item -> // description, dueDate
Todo Added // description, dueDate
TODO List* // todoId, description, dueDate
```
Save it to ```Eventstorming.emd```. 

**Step 2:**

```bash
les convert && les-node -b && cd api && npm install && docker-compose up -d --force-recreate
```

Or using Docker:
```bash
docker run -v $(pwd):/les les convert && docker run -v $(pwd):/les les-node -b && cd api && npm install && docker-compose up -d
```

(If you doing this in Linux and encounter "permission denied" errors, your USER or GROUP ID need to be specified.
 Say your USER ID is 1003, then add `--user 1003` after each `docker run` in the above command.)

**Step 3:**

There is no step 3.

* Add some items to the TODO list: http://localhost:3001/api-docs (Swagger/OpenAPI)
* View the items: http://localhost:3001/api/v1/r/TODOList
* Look at the "TodoAdded" events in the Eventstore DB: http://localhost:2113 (username 'admin', password 'changeit')
* Check out the source code for the "TODO List" system: ```./api```

### What next ...

* A collection of Event Markdown (EMD) examples: https://github.com/Adaptech/les/src/master/samples**

* Learn Event Storming: http://eventstorming.com

* Learn Event Markdown: https://webeventstorming.com

* EMD Cheat Sheet: https://github.com/Adaptech/letseventsource/raw/master/EMD-Cheatsheet-0.10.0-alpha-alpha.pdf

* https://gitter.im/Adaptech/les 

### IDE Integrations & Tools

* Event Markdown [vscode extension](https://github.com/markgukov/vscode-event-markdown)
