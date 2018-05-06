+++
title= "8. Working directly with Event Markup"
date= 2018-05-02T10:29:57-07:00
description = "Edit Event Markup to customize the system and use functionality not available from EMD."
draft= false
+++

### Deleting the previous iteration, including data

Delete the entire system with ...

```bash

cd api
docker-compose down

```

### Retaining data from the previous iteration

To retain the event store data, delete just the API docker container but leave the eventstore running:

```bash

cd api
docker-compose stop api && docker-compose rm -f

```

### Edit the EMD (or EML)

```les validate -f``` runs continuously, re-validating the EMD/EML each time ```Eventstorming.emd``` is saved:

![les-validate-example.png](/tutorial/les-validate-example.png)

This version makes sure that the "Add Item" userId parameter actually belongs to a registered user. But there is a validation error - for that to be possible, a read model must exist where users can be looked up by userId when somebody POSTs to ```/api/v1/Todo/AddItem```. Let's add one:

```bash

# TODO List
Register User -> // userId, email
User Registered // userId, email
User Lookup* // userId, email

Add Item -> // description, dueDate, userId
Todo Added // description, dueDate, userId
Set Status -> // status
Todo Status Changed // status
TODO List* // todoId, description, dueDate, status

```

Validation now passes:

![les-validate-example-ok.png](/tutorial/les-validate-example-ok.png)

### Rebuild and deploy

```bash

les convert todolist.emd && \
les-node -b Eventsourcing.eml.yaml && \
cd api && \
npm install && \
docker-compose up -d && \
docker-compose restart api # The restart is a workaround for a race condition when starting containers. :-(

```

Try it:

```bash

curl -X POST "http://localhost:3001/api/v1/Todo/AddItem" -H "accept: */*" -H "Content-Type: application/json" -d "{\"description\":\"Serpentlake\",\"dueDate\":\"Tuesday 3 May 2018\",\"todoId\":\"241dfb5c5e3243ea802e62a4ef000a5a\",\"userId\":\"48b0ef227d204fdc971def3deeb9ef4e\"}"

```

... results in:

```{"message":[{"field":"userId","msg":"userId does not exist."}]}```

Therefore, register the user:

```bash 

curl -X POST "http://localhost:3001/api/v1/User/RegisterUser" -H "accept: */*" -H "Content-Type: application/json" -d "{\"email\":\"natalieharris066@test.com\",\"userId\":\"48b0ef227d204fdc971def3deeb9ef4e\"}"

```

... and try adding a TODO item for that userId again:

```bash
curl -X POST "http://localhost:3001/api/v1/Todo/AddItem" -H "accept: */*" -H "Content-Type: application/json" -d "{\"description\":\"Serpentlake\",\"dueDate\":\"Tuesday 3 May 2018\",\"todoId\":\"241dfb5c5e3243ea802e62a4ef000a5a\",\"userId\":\"48b0ef227d204fdc971def3deeb9ef4e\"}"

```


The item can now be found in the TODO list read model:

```bash

curl -X GET "http://localhost:3001/api/v1/r/TODOList" -H "accept: */*"

```

returns ...

```json

[{"todoId":"241dfb5c5e3243ea802e62a4ef000a5a","description":"Serpentlake","dueDate":"Tuesday 3 May 2018","status":"","userId":"48b0ef227d204fdc971def3deeb9ef4e"}]

```

... because now a user with userId 48b0ef227d204fdc971def3deeb9ef4e exists:

```bash

curl -X GET "http://localhost:3001/api/v1/r/UserLookup" -H "accept: */*"

```

returns ...

```json

[{"userId":"48b0ef227d204fdc971def3deeb9ef4e","email":"natalieharris066@test.com"}]

```
