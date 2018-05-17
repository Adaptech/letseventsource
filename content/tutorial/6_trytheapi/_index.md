+++
title= "6. Try the API"
date= 2018-05-02T10:29:57-07:00
description = "Explore the newly generated API using CURL and Swagger"
draft= false
+++

{{% alert theme="info" %}}**The NodeJS system built by ```les-node``` includes a Swagger API playground.**{{% /alert %}}

**The Swagger UI is at http://localhost:3001/api-docs.**

**Let's use the API:**

* Create a backlog of tasks:

```bash

curl -X POST "http://localhost:3001/api/v1/Todo/AddItem" -H "accept: */*" -H "Content-Type: application/json" -d "{\"description\":\"Change lightbulb\",\"dueDate\":\"2018-04-20\",\"todoId\":\"aa152e0c138942a599ba0f2f84541f4e\"}"
curl -X POST "http://localhost:3001/api/v1/Todo/AddItem" -H "accept: */*" -H "Content-Type: application/json" -d "{\"description\":\"Repair faucet\",\"dueDate\":\"2018-04-22\",\"todoId\":\"bb152e0c138942a599ba0f2f84541f4e\"}"
curl -X POST "http://localhost:3001/api/v1/Todo/AddItem" -H "accept: */*" -H "Content-Type: application/json" -d "{\"description\":\"Paint hallway\",\"dueDate\":\"2018-04-23\",\"todoId\":\"cc152e0c138942a599ba0f2f84541f4e\"}"

```

* Look at the backlog:

```bash

curl http://localhost:3001/api/v1/r/TODOList```

```

* Pull some items from the backlog into TODO:

```bash

curl -X POST "http://localhost:3001/api/v1/Todo/SetStatus" -H "accept: */*" -H "Content-Type: application/json" -d "{\"status\":\"todo\",\"todoId\":\"aa152e0c138942a599ba0f2f84541f4e\"}"
curl -X POST "http://localhost:3001/api/v1/Todo/SetStatus" -H "accept: */*" -H "Content-Type: application/json" -d "{\"status\":\"todo\",\"todoId\":\"bb152e0c138942a599ba0f2f84541f4e\"}"
curl -X POST "http://localhost:3001/api/v1/Todo/SetStatus" -H "accept: */*" -H "Content-Type: application/json" -d "{\"status\":\"todo\",\"todoId\":\"cc152e0c138942a599ba0f2f84541f4e\"}"

```

* Start some work and complete some work:

```bash

curl -X POST "http://localhost:3001/api/v1/Todo/SetStatus" -H "accept: */*" -H "Content-Type: application/json" -d "{\"status\":\"doing\",\"todoId\":\"aa152e0c138942a599ba0f2f84541f4e\"}"
curl -X POST "http://localhost:3001/api/v1/Todo/SetStatus" -H "accept: */*" -H "Content-Type: application/json" -d "{\"status\":\"done\",\"todoId\":\"bb152e0c138942a599ba0f2f84541f4e\"}"

```

Here's the result:

![get-todolist-result.png](/tutorial/get-todolist-result.png)


Try adding and completing some more items at http://localhost:3001/api-docs.

**To look some of the events which were stored to the event log and published when commands were POSTed, go to http://localhost:2113 (username 'admin', password 'changeit')**



