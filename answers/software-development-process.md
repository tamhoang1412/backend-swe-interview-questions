# Topic: SOFTWARE DEVELOPMENT PROCESS

## DDD. What is DDD?

DDD stands for Domain-Driven Design. It is a design approach that models software as close as possible with the domain knowledge provided by domain experts.

## 2 base foundations of DDD

2 base foundations of DDD are ubiquitous languages and model-driven design.

- Ubiquitous language is a dictionary that describes things to create a common understanding between team and domain expert. That includes names of all classes, names of all services, rules that software needs to follow...

- Model-driven design is a design approach that focuses on data models. Model-driven design contains a few key components like:

  - Entity: is the thing that is identical and its identity is immutable.
  - Value object: is the thing that we care only about its value and don't care about its identity.
  - Service: is the thing that its behavior does not belong to any entity.
  - Module: domain model is divided into smaller modules to be easier to develop and maintain.
  - Aggregate: is the thing that groups several things into a united block, and this block communicates with the outside world through the aggregate root.
  - Factory: is the thing that creates complicated things.
  - Repository: is the thing that refers to entities and has methods to create, update, delete, read... entities.

## TDD. What is TDD?

To be defined.
