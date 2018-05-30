+++
title= "8. Customize Event Markup"
date= 2018-05-02T10:29:57-07:00
description = "Edit Event Markup to customize the system and use functionality not available from EMD."
draft= false
+++

{{% alert theme="info" %}}**Edit Event Markup to customize the system and use functionality not available from EMD.**{{% /alert %}}

When deriving a CQRS/ES systems from Event Markdown, ```les convert``` makes a number of default assumptions about what the resulting system specified in the Event Markup YAML file should look like and what functionality it should have. In cases where there are additional requirements EML can be augmented and customized.

Event Markdown language is intentionally simple enough so it takes no more than 10 minutes to learn. In addition, it tries to mirror a very important event storming concept known as "deliberate fuzziness" - avoid getting side tracked into too much detail. Instead, focus on the big picture and on getting a shared understanding of the problem space.

That information can be augmented or edited in Event Markdown Language (EML).

**Save an ```Eventstorming.eml.yaml``` file to an empty directory:**

```bash

Solution: User Registration
Contexts:
- Name: User Registration
  Streams:
  - Stream: User
    Commands:
    - Command:
        Name: RegisterUser
        Parameters:
        - Name: userId
          Type: string
          Rules:
          - IsRequired
        - Name: email
          Type: string
          Rules:
          - IsRequired
        Postconditions:
        - UserRegistered
    - Command:
        Name: MarkAsAuthenticated
        Parameters:
        - Name: userId
          Type: string
          Rules:
          - IsRequired
        Preconditions:
        - UserRegistered MustHaveHappened
        - UserDeleted MustNotHaveHappened
        Postconditions:
        - UserAuthenticated
    - Command:
        Name: DeleteUser
        Parameters:
        - Name: userId
          Type: string
          Rules:
          - IsRequired
        Preconditions:
        - UserRegistered MustHaveHappened
        Postconditions:
        - UserDeleted
    Events:
    - Event:
        Name: UserRegistered
        Properties:
        - Name: "email"
          Type: string
          IsHashed: false
        - Name: "userId"
          Type: string
          IsHashed: false
    - Event:
        Name: UserAuthenticated
        Properties:
        - Name: "userId"
          Type: string
          IsHashed: false
    - Event:
        Name: UserDeleted
        Properties:
        - Name: "userId"
          Type: string
          IsHashed: false
  Readmodels: []

```

The EML file contains some additional functionality:

![command-preconditions-example.png](/tutorial/command-preconditions-example.png)

This is an example of preconditions which must be met for a command being able to execute: In order to be able to mark a user as authenticated (e.g.) after the user has been logged in by a system external authentication mechanism, the user cannot have been deleted and the user must have registered.

**Build the API...**

```bash

les-node -b

```

**Start it...**

```bash

cd api && npm install && docker-compose up -d

```

**... and try it out at http://localhost:3001/api-docs.**

{{% panel theme="success" header="**So that's it for the tutorial.**" %}}
LESTER is currently quite alpha, with many missing features. The design goal for EMD/EML is to eventually be full featured enough to enable users to build a simple CRUD systems with validation rules, etc. end-to-end without needing going into the generated code itself. In Real World scenarios, LESTER is currently mostly used as a one-way street - iterate in EMD and EML until there is need to customize the NodeJS code itself, then proceed in Node only. This has turned out to be very useful for getting started with projects. Where we tried it it has saved considerable development time. In addition, the process of event storming and iterating has helped a lot with understanding requirements.
{{% /panel %}}