# DDD Quickly

## 1. What is Domain Driven Design?

### Building Domain Knowledge

Where do we start from a software development perspective?
-> Start by understanding the domain

Air traffic controllers are the specialists of this domain.
But, the controllers are not system designers or software specialists.
You need to extract essential information generalize it.
When you start talking to them, you will hear a lot about aircrafts taking off, and landing, aircrafts in midair...
-> You need to start somewhere

Departure <- Aircraft --- Destination

You will hear flight, path, route...

Aircraft ---> Route ---> Departure
                    ---> Destination

## 2. The Ubiquitous Language

### The Need for a Common Language

### Create the Ubiquitous Language


## 3. Model Driven Design

### The Building Blocks Of A Model Driven Design

### Layered Architecture

### Entities

### Value Objects

### Services

### Modules

Modules are used as a method of organizing related concepts and tasks in order to reduce complexity

Software code should have high level of cohesive and low level of coupling.
+ Communicational cohesive: operate on the same data
+ Functional cohesive: work together to perform a well-defined task

Modules should have well-defined interfaces which are accessed by other modules.

Choose modules that tell the story of the system and contain a cohesive set of concepts.

Give the modules names that become part of the Ubiquitous Language. Modules and their names should reflect insight into domain.

After the role of the module is decided, it usually stays unchanged, while the internals of the module may change a lot.

### Aggregates
Managing the life cycle of a domain object constitutes a challenge in itself, and if it is not done properly, i may have a negative impact on the domain model. Three patterns which help us to deal with it:

+ Aggregate is a domain pattern used to define object ownership and boundaries.
+ Factories and Repositories are two design patterns which help us deal with object creation and storage.

Aggregates
+ The root is an Entity, and it is the only object accessible from outside
+ The root can hold references to any of other aggregate objects
+ An outside object can hold references only to the root object
+ It's possible for the root to pass transient references of internal objects to external ones with the condition that the external objects do not hold the reference after the operation is finished. One simple way to do that is to pass copies of the Value Objects to external objects.

### Factories

Factories are used to encapsulate the knowledge necessary for object creation, and they are especially useful to create Aggregates. When the root of the Aggregate created, it is necessary that all objects subject to invariants are created too.

Factory Pattern
+ Factory Method: to add a method to Aggregate Root, which takes care of the object creation
+ Abstract Factory: create a separate Factory object

Factories are not needed when:
+ The construction is not complicated
+ The creation of an object does not involve the creation of other objects, and all the attributes needed are passes via the constructor
+ The client is interested in implementation, perhaps wants to choose Strategy used.
+ The class is the type. There is no hierarchy involved, so no need to choose between a list of concrete implementations.

### Repositories

The purpose of Repositories are to encapsulate all the logic needed to obtain object references.

A Repository may contain detailed information used to access the infrastructure, but its interface should be simple.
A Repository should have a set of methods used to retrieve objects.
The implementation of a repository can be closely liked to the infrastructure, but that the repository interface will be pure domain model.


## 4. Refactoring Toward Deeper Insight

### Continuous Refactoring

There are many ways to do code refactoring. There are even refactoring patterns.

The design has to be flexible.A stiff design resists refactoring. Code that was not built with flexibility in mind is code hard to work with.

### Bring Key Concepts Into Light

Refactoring is done in small steps. The result is also a series of small improvements.

Breakthrough

How to recognize implicit concepts?
+ Listen to the language

Some sections of the design may not be so clear

Another obvious way of digging out model concepts is to use domain literature: books.

There are other concepts which are very useful when made explicit: Constraint, Process and Specification.
+ Place the Constraint into a separate method has the advantage of making it explicit.
+ The best way to implement processes is to use a Service. If there are different ways to carry out the process, then we can encapsulate the algorithm in an object and use a Strategy.
+ A Specification is used to test an object to see if it satisfies a certain criteria.

## 5. Preserving Model Integrity

This chapter is about large projects which require the combined efforts of multiple teams.

It is so easy to start from a good model and progress toward an inconsistent one.

The first requirement of a model is to be consistent, with invariable terms and no contradictions. The internal consistency of a model is called *unification*.

### Bounded Context

The main idea to define the scope of a model, to draw up the boundaries of its context, then do the most possible to keep the model unified.

A Bounded Context is not a Module. A Bounded Context provides the logical frame inside of which the model evolves.

Modules are used to organize the elements of a model, so Bounded Context encompasses the Module.

When different teams have to work on the same model, we must be very careful not to step on each others toes.

There is a price to pay for having multiple models. We need to define the borders and the relationships between different models.

### Continuous Integration

### Context Map

### Shared Kernel

### Customer Supplier

### Conformist

### Anti-corruption Layer

### Separate Ways

### Open Host Service

### Distillation


## 6. DDD Matters Today: An Interview with Eric Evans
