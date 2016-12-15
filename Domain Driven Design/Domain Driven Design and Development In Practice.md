# Domain Driven Design and Development In Practice
> From InfoQ [Article](https://www.infoq.com/articles/ddd-in-practice), Posted by Srini Penchikala on Jun 12, 2008

## Background
+ Based on Eric Evans' book "Domain Driven Design"
+ Covering the domain modeling and design aspects mainly from a conceptual and design stand-point
+ To cover the domain modeling and design from a practical stand-point

## Introduction
Terms
+ Fat Service Layer
+ Anemic Domain Model
+ Return On Investment (ROI)
+ Enterprise Architecture (EA)
+ Service Oriented Architecture (SOA)

Content
+ Anemic domain models vs Rich domain models

### Role of Domain Driven Design in Enterprise Architecture
### Domain Driven Design and SOA

## Project Management
Terms
+ Design by Contract (DbC)
+ Automated Tests
+ CI
+ Refactoring
+ POJO (POCO in .NET)
+ Dependency Injection (DI)
+ Aspect Oriented Programming (AOP)

![DDD Implementation Cycle](https://cdn.infoq.com/statics_s1_20161208-0302u1/resource/articles/ddd-in-practice/en/resources/DDDImplementationCycleDiagram.gif "DDD Implementation Cycle")


## Sample Application

Home Loan Processing System
+ Underwriting
+ Closing
+ Funding

## Architecture
A typical enterprise application architecture consists of the following four conceptual layers:

+ **User Interface (Presentation Layer)**: Responsible for presenting information to the user and interpreting user commands.
+ **Application Layer**: This layer coordinates the application activity. It doesn't contain any business logic. It does not hold the state of business objects, but it can hold the state of an application task's progress.
+ **Domain Layer**: This layer contains information about the business domain. The state of business objects is held here. Persistence of the business objects and possibly their state is delegated to the infrastructure layer.
+ **Infrastructure Layer**: This layer acts as a supporting library for all the other layers. It provides communication between layers, implements persistence for business objects, contains supporting libraries for the user interface layer, etc.

Layered Application Architecture Diagram
![Layered Application Architecture diagram](https://cdn.infoq.com/statics_s1_20161208-0302u1/resource/articles/ddd-in-practice/en/resources/ArchitectureDiagram_lg.gif "Layered Application Architecture diagram")


Design Aspects
* Object Oriented Programming (OOP)
* Dependency Injection (DI)
* Aspect Oriented Programming (AOP)

### Dependency Injection
### Aspect Oriented Programming
### Annotations
### Domain model and Security
### Business Rules
+ Data validation
+ Data transformation
+ Business decision-making
+ Process routing (work-flow logic)

Terms
+ Groovy (scripting language)
+ Domain Specific Languages (DSL)


## Design

### Design Patterns that Support DDD
+ Domain Object (DO)
+ Data Transfer Object (DTO)
+ DTO Assembler
+ Repository: The Repository contains domain-centric methods and uses the DAO to interact with the database.
+ Generic DAO's
+ Temporal Patterns: These patterns add time dimension to rich domain models. Bitemporal framework, which is based on Martin Fowler's Temporal Patterns, provides a design approach to dealing with bitemporal issues in the domain models. The core domain objects and their bitemporal properties can be persisted using an ORM product such as Hibernate.

### DDD Anti-Patterns
+ Anemic domain objects
+ Repetitive DAO's
+ Fat Service Layer: This is where service classes will end up having all the business logic.
+ Feature Envy: This is one of the classic smells mentioned in Martin Fowler's book on Refactoring where the methods in a class are far too interested in data belonging to other classes.

### Data Access Objects

### Persistence

### Caching

### Transaction Management

### Data Transfer Objects


## Development

### Code Generation

### Refactoring

## Unit Testing/Continuous Integration

## Deployment

## Conclusion
"It's important not to blur the lines between the philosophy of design (DDD) and the technical tool box that helps us fulfill it (OOP, DI, and AOP)" - Eric Evans

## Advancing Frontiers
