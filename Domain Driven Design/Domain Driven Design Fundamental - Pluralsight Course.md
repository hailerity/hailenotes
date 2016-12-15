# 1. Introducing DDD

## Why should you care about Domain Driven Design?

+ Principles & patterns to solve difficult problems
+ History of success with complex projects
+ Aligns with practices from our own experience
+ Clear, testable code that represents the domain


+ Solve Problems
+ ---> Understand Client Needs
+ --- ---> Build Software
+ --- --- ---> Write Code

```
DDD is complex

```
## High Level View of DDD

### Interaction with Domain Expert
Talk to domain experts

```
The important of Communication:
"Cultivate you ability to communicate with business people, to free up people's creativity for modeling, etc." - Eric Evans
```

### Focus on a SubDomain
+ Sales
+ Purchase Materials
+ Engineering
+ Marketing
+ Accounting
+ Manage Employees

Don't try to do everything at once, it would be very difficult & expensive

### Implementing the Subdomain
+ -> Interact with Domain Experts
+ -> Model a single Sub-Domain at a time
+ -> Implementation of Sub-Domains(Separation of Concerns)

## Benefits of DDD
+ Flexible
+ Customer's vision/perspective of the problem
+ Path through a very complex problem
+ Well-organized and easily tested code
+ Business logic lives in one place
+ Many great patterns to leverage

```
... it should be applied only to complex domains ...
```

## Drawbacks of DDD
+ Time and Effort
  + Discuss & model the problem with domain experts
  + Isolate domain logic from other parts of application
+ Learning curve (why you're watching this course)
  + New principles
  + New patterns
  + New processes
+ Only makes sense when there is complexity in the problem
  + Not just CRUD or data driven application
  + Not just technical complexity without business domain complexity
+ Team or Company Buy-in to DDD

## A Mind Map of DDD's Working Parts

---

# 2. DDD: Modeling Problems in Software

## Goals
+ Breaking up the Veterinary Office Domain
+ The Important of the Domain Expert
+ A Play!
+ Core elements of a Domain Model
+ Sub-Domains and Bounded Contexts
+ That Ubiquitous Term: Ubiquitous Language

## Learning About Our Domain by Talking With A Domain Expert
Role playing ... working with client to discover sub-domains

## Breaking the Domain into Sub-domains

## Focusing on One Sub-domain with the Domain Expert

## First High Level Model of the Sub-domain

## Creating a Bounded Context
Each model is only valid in a specific context, even if two models have the same name or refer to the same object, but they should be in their own bounded context.

So explicitly define the context within which a model applies... Keep the model strictly consistent within these bounds, but don't be distracted or confused by issues outside.

Ex:

Appointment Scheduling -> Client

vs

Billing -> Client

Remember though, if you have multiple contexts you'll want to keep them bounded. And one way to maintain this separation is to keep their data, code and team members distinct from one another.

You can introduce separation through: Namespaces, Folders, Projects. At least keep the concept in mind for guidance. Not hard rules, but guidance.

## Difference Between Sub-domain and Bounded Context
"Sub-domain is a problem space concept. Bounded context is a solution space concept".

Sub-domain is describing something about the way you've chosen to break down your business, or whatever the domain activity is, whereas the boundary context describe how the software and how the software development has been broken down.

## Understanding Context Map

## Eric Evans on Clearly Defining Context Boundaries

## Bounded Contexts in Our Application

## The Ubiquitous Language of a Bounded Context

## Working on a Ubiquitous Language With the Domain Expert
Working on a Common, "Ubiquitous" Language for the Appointment Scheduling Bounded Context

We need to make some terms clear between people
+ Clients: Person who: makes appointments, pays the bills, brings pets clinic
+ Patients: Animal for whom: Medical records are kept
+ Appointment: Scheduled time for: surgeries, any type of regular office visit

## Glossary of terms
+ Problem Domain: the specific problem the software you're working on is trying to solve.
+ Core Domain: the key differentiator for the customer's business - something they must do well and cannot outsource.
+ Sub-domain: separate applications or features your software must support or interact with
+ Bounded Context: A specific responsibility, with explicit boundaries that separate it if from other parts of the system.
+ Context Mapping: the process of identifying bounded contexts and their relationships to on another.
+ Shared Kernel: part of the model that is shared by two or more teams, who agree not to change it without collaboration.
+ Ubiquitous Language: a language using terms from the domain model that programmers and domain experts use to discuss the system.

# 3. Elements of a Domain Model

## Introduction

## Goals
+ Focus on Domain
+ Focus on Behaviors
+ Rich vs. Anemic Domain Models
+ Entities
+ Associations
+ Value Objects
+ Services

## The Important of Understanding DDD Terminology
Easy to talk about
Term overlap with technology
Entity is key element in DDD
Know enough to be dangerous

## Focus on the Domain
D is for Domain

[The Domain Layer is] responsible for representing **concepts of the business**, **information about the business situation**, and **business rules**. State that reflects the business situation is controlled and used here, even though the technical details of storing it are delegated to the infrastructure. This layer is the heart of business software.

Focus on the domain not the technical details

Focus on Behaviors
+ Schedule an appointment for a checkup
+ Note a pet's weight
+ Request lab work
+ Notify pet owner of vaccinations due
+ Accept a new patient
+ Book a room

Not Attributes
+ Appointment.Time
+ Pet.Name
+ Owner.Telephone
+ Room.Number

## Anemic and Rich Models
Anemic Domain Models vs Rich Domain Models

### Anemic Domain Models
Focus on state of objects

### Rich Domain Models

## Entities in DDD and in Our Bounded Context
Many objects are not fundamentally defined by their attributes, but rather by a **thread of continuity** and **identity**.

Entities are objects those are defined by identity

## Eric Evans on the Single Responsibility Entities
"I don't think an entity ought to have a lot of different business logic in it"
"...more and more conflict..."
"The responsibilities that I would focus the design of an entity on ... are the identity and the life cycle"
"The identity isn't [always] just an ID field"
"But sometime identity is so complex that I would have another object or set of functions be responsible for that."

UPS Package ID 98383849283
Received | Shipped | In Transit | Arrived Loc A | Arrived Loc B | Delivered

"The entity might delegate [logic] to value objects ... or invoke a service."

## Eric Evans on the Entity Equality Methods
Should Entities Have Equality Comparers?

"I've come to believe that an entity shouldn't even have an equality comparison."
"The question of whether an entity is the same as other entity is non-trivial question."


## How We've Implemented Entities in Our Code

## Associations (aka Relationships)

## Value Objects

## Eric Evans on the Methods in Value Objects
Should value objects have methods and logics?
"Value objects are very good place to put methods and logics ... a better place than entities."
"An example: Dates are a classic value object"
But logic with no side effect

## Value Objects in Our Code
Value Objects are immutable (never be changed)

## Eric Evans on the Entity Logic in Value Objects
Should value objects own the logic of entities?
"If there is logic that is classic software logic, I like to have that in value objects."
"You can really test value objects tremendously easier than entities."
"The entity becomes a critical place of glue... an orchestrator."
"Methods of the entity [have] high level things that read like a use case level of communication, rather than the nitty gritty details."

## Domain Services
When an operation is important to the model, but doesn't necessarily belong on any one entity or value object, a service is often appropriate.
But don't be too quick to give up on finding a natural home for the operation on an existing entity or value object.

Good domain services
+ Not a natural part of an Entity or Value Object
+ Have an interface defined in terms of other domain model elements
+ Are stateless (but may have side effects)

Examples of Services in Different Layers
+ UI Layer (& Application Layer)
+ Domain (Application Code)
+ Infrastructure

## Glossary of Terms
+ Anemic Domain Model: Model with classes focused on state management. Good for CRUD.
+ Rich Domain Model: Model with logic focused on behavior, not just state. Preferred for DDD.
+ Entity: A mutable class with an identity (not tied to it's property values) used for tracking and persistence.
+ Immutable: Refers to a type whose state cannot be changed once the object has been instantiated.
+ Value Object: An immutable class whose identity is dependent on the combination of its values.
+ Services: Provide a place in the model to hold behavior that doesn't belong elsewhere in the domain.
+ Side Effects: Changes in the state of the application or interaction with the outside world (e.g. infrastructure)

## Key Takeaways

## Resources

---

# 3. Aggregates in DDD
A Critical Pattern for Managing Complexity in the Domain

# Introduction

# Goals
DDD helps with complex domains
How do we manage this complexity?

+ Aggregates
+ Aggregate Roots
+ Invariants
+ Shifting our Design to Smarter Aggregate
+ Implementing Aggregates in Code

# Tackling Data Complexity

# Introducing Aggregates and Aggregate Roots
+ Customer Aggregate: (Aggregate Root) Customer <1>----<N> Address
+ Product Aggregate: (Aggregate Root) Product <1>---<N> Component

Data changes to the Aggregate should follow ACID

An **aggregate** is a cluster of associated objects that we treat as a unit for the purpose of data changes.

# Interacting with Aggregates
Relationships between Aggregates
+ Non-Root Aggregate can only be referenced by the Root Aggregate in the same Aggregate
+ Root Aggregate can reference to and be referenced by other Root Aggregate

# Evolving the Appointments Aggregate


# Using Invariants to Better Understand Our Aggregate
Invariants
Examples of Aggregate Invariants
+ Total items on purchase order do not exceed limit
+ Two appointments do not overlap on another
+ End date follow begin date

# Modeling Breakthroughs and Refactoring

# Considering Schedule as Our New Aggregate

# The Schedule Aggregate in Our Application

# Review Aggregate Tips
+ Aggregates are not always the answer!
+ Aggregates can connect only by the root
+ Don't overlook using FKs for non-root entities
+ "Aggregates of one" are acceptable (An aggregate that has only one object in it)
+ "Rule of Cascading Deletes"

# Glossary of Terms
+ Aggregate: is a group of related objects that work together in a transaction (a transaction graph of objects)
+ Aggregate Root: the entry point of an aggregate which ensures the integrity of the entire graph
+ Invariant: a condition that should always be true for the system to be in a consistent state
+ Persistence Ignorant Classes: Classes that have no knowledge about how they are persisted

# Resources

---

# 4. Repositories

# Introduction
An other important pattern for managing domain complexity

# Goals
+ Define Repositories
+ Tips & Benefits
+ Common Repository Conundrums
+ Repository Implementations in Our App

# Introducing Repositories
Repository Design Pattern
(Design Pattern Library Course on PluralSight)

Object Life Cycle
+ No persistence:
Create -> Do Stuff -> Destroy
+ With persistence:
Create -> Reconstitute from Persistence -> Do stuff -> Save Changes to Persistence -> Destroy

--> Use Repositories to manage the Life Cycle of persistent objects without the objects having to know anything about their persistence.
We call those objects persistence ignorant

A repository represents all objects of a certain type as a conceptual set ... like a collection with more elaborate querying capability

# Repository Tips, Benefits, and Guidance
### Tips
+ Think of it as an in-memory collection (actions with repositories: add, remove, retrieve)
+ Implement a known, common access Interface
+ Methods for add & remove
+ Methods that predefine criteria for object selection
+ Repos for aggregate roots
+ Client focuses on the model, repo focuses on persistence

### Benefits
+ Provides common abstraction for persistence
+ Promotes Separation of Concerns
+ Communicate Design Decisions
+ Enables Testability
+ Improved Maintainability

Client code can be ignorant of repository implementation... but developers cannot

Common Repository Blunders
+ N+1 Query Errors
+ Inappropriate use of eager or lazy loading
+ Fetching more data than require

# Comparing Repositories and Factories
Factories are only involved in creating new objects
Repositories are used to find and update existing objects
Repositories can use a Factory to create its objects
Factories should not be involved in persistence

# To IRepository T or Not to IRepository T

# Generic Repositories in DDD

# Repositories in Our Application

# Refactoring for better Separation

# Glossary
+ Repository: A class that encapsulates the data persistence for an aggregate root
+ ACID: Atomic, Consistent, Isolated, and Durable

# References
