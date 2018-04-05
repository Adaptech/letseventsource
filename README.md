# LetsEventStore
Lester takes a specification for an event sourced system and produces deployment-ready commands, events, documentation and infrastructure.

## Event Sourced Systems, Made Simple
“Lester” = “Let’s Event Source Together”

Lester takes a specification for an event sourced system and produces deployment-ready commands, events, documentation and infrastructure. It is designed to make prototyping and starting implementation of an event based system very simple and very closely aligned with business objectives and requirements.

### In:
Event Markdown (EMD) is a machine- and remote collaboration friendly way of doing event storming. It retains what makes the Post-It & paper-on-the-wall version successful: Easy to do. Brings business and technical people together. Fun. Deliberately fuzzy to discourage getting lost in detail not (yet) needed. Event Markup Language (EML) is a simple implementation agnostic YAML based declarative language for describing event sourced systems. Custom business rules and read models in NodeJS or Golang.

### Out:
Fully customizable, non-befuddling, no lock-in developer-friendly NodeJS or Golang. Infrastructure: Event Store and read model databases. Currently supports Eventstore, Postgres, LevelDB, Cassandra. Devops: Docker containers on Kubernetes.

![Lester Pipline](https://github.com/adaptech/letseventsource/blob/master/images/lester-pipeline.png)
