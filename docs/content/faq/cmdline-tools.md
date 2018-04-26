+++
title= "What are \"les\", \"les-node\" and \"compliance-test\"?"
date= 2018-04-26T06:43:00-07:00
description = "The LESTER stack command line tools."
draft = false
alwaysopen = true
weight=700
+++

# LESTER Command Line Tools

## les

 - [les](https://github.com/Adaptech/les/tree/master/cmd/les) validates EMD/EML for completeness and converts event stormings (described in Event Markdown) to Event Markup (EML) suitable for generating CQRS/ES systems.

Think of ```les``` as an architect-in-a-box.

## les-node

[les-node](https://github.com/Adaptech/les/tree/master/cmd/les-node) builds an event sourced NodeJS API from EML.

## What is the "compliance-test" utility?

[compliance-test](https://github.com/Adaptech/les/tree/master/cmd/compliance-test) tests whether an HTTP API built from a reference EML specification is a complete error-free event sourced system. (a.k.a. “les compliant”). It assumes that certain conventions were followed for routes and API endpoint names. It is implementation language agnostic.

## What do les-redux, les-csharp, les-shellscript, les-haskell, les-whitespace and les-akka have in common?

They are not in existence. The only languages for which EML->API builders have been created at this point are EML->NodeJS, EML->Swagger/OpenAPI (as a [Golang package for use by other tools](https://github.com/Adaptech/les/tree/master/pkg/eml/generate/openapi)) and a EML->Golang pre-alpha version.

## What is les-I-can’t-stand-code-other-than-my-own?

Event Markup Language is your hedge against the framework trap (a.k.a. “straight jacket, implemented as mystery code”). It is deliberately implementation- and language-agnostic. ```eml-node``` demonstrates how to turn EML into a working CQRS/ES system with an API and a Swagger API playground. If you prefer (or need) to implement your own version, go ahead.
