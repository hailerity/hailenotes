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

[The Domain Layer is] responsible for representing concepts of the business, information about the business situation, and business rules. State that reflects the business situation is controlled and used here, even though the technical details of storing it are delegated to the infrastructure. This layer is the heart of business software.

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

### Anemic Domain Models
Focus on state of objects

### Rich Domain Models

## Entities in DDD and in Our Bounded Context

## Eric Evans on the Single Responsibility Entities

## Eric Evans on the Entity Equality Methods

## How We've Implemented Entities in Our Code

## Associations (aka Relationships)

## Value Objects

## Eric Evans on the Methods in Value Objects

## Value Objects in Our Code

## Eric Evans on the Entity Logic in Value Objects

## Domain Services

## Glossary

## Key Takeaways

## Resources
