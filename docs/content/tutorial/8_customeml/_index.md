+++
title= "8. Customize Event Markup"
date= 2018-05-02T10:29:57-07:00
description = "Edit Event Markup to customize the system and use functionality not available from EMD."
draft= false
+++

{{% alert theme="info" %}}**Edit Event Markup to customize the system and use functionality not available from EMD.**{{% /alert %}}

When deriving a CQRS/ES systems from Event Markdown, ```les convert``` makes a number of default assumptions about what the resulting system specified in the Event Markup YAML file should look like and what functionality it should have. In cases where there are additional requirements EML can be augmented and customized.

Event Markdown language is intentionally simple enough so it takes no more than 10 minutes to learn. In addition, it tries to mirror a very important event storming concept which Alberto describes as "deliberate fuzziness" - avoid getting side tracked into too much detail. Instead, focus on the big picture and on getting a shared understanding of the problem space.  

alone is no. That information can be augmented or edited in Event Markdown Language (EML).

In an empty directory create an ```Evenstorming.eml.yaml``` file:

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

**This EML file contains some additional functionality:**

![command-preconditions-example.png](/tutorial/command-preconditions-example.png)

This is an example of preconditions which must be met for a command being able to execute: In order to be able to mark a user as authenticated (e.g.) after the user has been logged in by a system external authentication mechanism, the user cannot have been deleted and the user must have registered.



