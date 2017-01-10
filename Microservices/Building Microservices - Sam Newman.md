# Building Microservices: Designing Fine-Grained Systems - Sam Newman

---

# Preface
+ Microservices is an approach to distributed system
+ Promote the use of finely grained services
+ Avoid problems of traditional tiered architectures
+ Integrate new technologies and techniques
+ Full of concrete examples of microservices use around the world

# Why Should Read This Book

# Why I Wrote This Book?
Started thinking about the topic of application architectures, when working to help people deliver their software faster.
At the some time, many organization were experiencing with finer-grained architectures to accomplish similar goals, but also to achieve things like improved scaling, increasing autonomy of teams, or to more easily embrace new technologies.

# A Word on Microservices Today
Microservices is a fast moving topic, even the idea is not new.

I have tried to focus this book on ideas more than specific technologies, knowing that implementation details always change faster than the thought behind them.

Be prepared for many years of continuous learning to keep on top of the state of art!

# Navigating This Book
Organized in a topic-based format
+ Chapter 1: Microservices
+ Chapter 2: The Evolutionary Architect
+ Chapter 3: How to Model Services
+ Chapter 4: Integration
+ Chapter 5: Splitting the Monolith
+ Chapter 6: Deployment
+ Chapter 7: Testing
+ Chapter 8: Monitoring
+ Chapter 9: Security
+ Chapter 10: Conway's Law and System Design
+ Chapter 11: Microservices at Scale
+ Chapter 12: Bring It All Together

# Convention Used in This Book

# Acknowledgements

---

# Chapter 1: Microservices
We have been finding better ways to build systems.

Eric Evan's book Domain-Driven Design helped us understand the importance of representing the real world in our code, and show us better way to model our systems.

## What Are Microservices?
Microservices are small, autonomous services that work together.

### Small, and Focused on Doing One Thing Well
+ Difficult to change when codebase is so large.
+ Single Responsibility Principle
+ Independent services
+ Focus Service boundaries on business boundaries

How small is small?
+ It's not number of lines
+ Something that could be rewritten in two weeks
+ Small enough and no smaller
+ Once a piece of code no longer feels too big, it's probably small enough
+ How small is how well the services aligns to team structures.

### Autonomous
+ Microservice is a separate entity, it might be deployed as an isolated service on a platform as a service (PAAS) or it might be its own operating system process.
+ Avoid packing multiple services onto the same machine
+ All communication between services themselves are via network calls, to enforce separation between the services and avoid the perils of tight coupling
+ These services need to be able to change independently of each other
+ Picking technology-agnostic APIs to ensure that we don't constrain technology choices
+ Without coupling, everything breaks down for us

### Key Benefits
The benefits of microservicesare many and varied

#### Technology Heterogeneity
+ With a system composed of multiple, collaborating services, we can decide to use different technologies inside each one.
+ Adopt technology more quickly and understand how new advancements may help us
+ Embracing multiple technologies doesn't come without an overhead, of course
+ It's all about finding the right balance

#### Resilience
+ If one component of a system fails, but that failure doesn't cascade, you can isolate the problem and the rest of the system can carry on working
+ Service boundaries become your obvious bulkheads
+ We do need be careful however, we need to understand the new sources of failure that distributed systems have to deal with

#### Scaling
+ With a large, monolithic service, we have to scale everything together
+ With smaller services, we can just scale those services that need scaling
+ We can even apply scaling on demand for those pieces that need it

#### Ease of Deployment
+ A one-line change to a million-line-long monolithic application requires the whole application to be deployed in order to release the change
+ With microservices, we can make a change to a single service and deploy it independently of the rest of the system
+ Allow us to get our code deployed faster, if a problem does occur, it can be isolated quickly to an individual service, making fast rollback easy to achieve

#### Organizational Alignment
+ Many of us have experienced the problems associated with large teams and large codebase
+ We also know that smaller teams working on smaller codebase tend to be more productive
+ Microservices allow us to better align our architecture to our organization, helping us minimize the number of people working on any one codebase to hit the sweat spot of team size and productivity

#### Composability
+ One of the key promises of distributed systems and service-oriented architectures is that we open up opportunities for reuse of functionality
+ With microservices, we allow for our functionality to be consumed in different ways for different purposes

#### Optimizing for Replaceability
+ Teams using microservice approaches are comfortable with completely rewriting services when required, and just killing a service when it is no longer needed


### What is About Service-Oriented Architecture?
+ Service-oriented architecture (SOA) is a design approach where multiple services collaborate to provide some end set of capabilities, a service here typically means a completely separate operating process, communication between these services occurs via calls across a network rather than method calls within a process boundary
+ SOA at its heart is a very sensible idea, however, despite many efforts, there is a lack of good consensus on how to SOA well
+ Many of the problems laid at the door of SOA are actually problems with things like communication protocols, vendor middleware, a lack of guidance about service granularity, or the wrong guidance on picking places to split the system
+ Most of conventional wisdom around SOA doesn't help you understand how to split something big into something small
+ The microservice approach has emerged from real-world use, taking our better understanding of systems and architectures to do SOA well
+ Should think of microservices as a specific approach for SOA in the same way that XP or Scrum are specific approaches for Agile software development

### Other Decompositional Techniques

#### Shared Library
+ A very standard decompositional technique that is built into virtually any language is breaking down a codebase into multiple libraries, provided by third parties, or created in your own organization
+ Libraries give you a way to share functionality between teams and services
+ Drawbacks: lose true technology heterogeneity

#### Modules
+ Some languages provide their own modular decomposition techniques that go beyond simple libraries, they allow some lifecycle management of the modules, such that they can be deployed into a running process, allowing you to make changes without taking down the whole process
+ The Open Source Gateway Initiative (OSGI) is worth calling out as one technology specific approach to modular decomposition
+ The problems of OSGI is that it is trying to enforce things like module lifecyle management without enough support in the language itself

#### No Silver Bullet
+ Before we finish, I should call out that microservices are no free lunch or silver bullet, and make for a bad choice as a golden hammer
+ They have all the associated complexities of distributed systems, and while we have learned a lot about how to manage distributed systems well, it is still hard

### Summary
Hopefully by now you know what a microservice is, what make it different from other compositional techniques, and what some of the key advantages are

# Chapter 2: The Evolutionary Architect

## Inaccurate Comparisons

> You keep using that word. I do not think it means what you think it means - Inigo Montoya, from The Princess Bride

+ Architects have an important job
+ When we compare ourselves to engineers or architects, we are in danger of doing everyone a disservice. Unfortunately, we are stuck with the work architect for now. So the best we can do is to redefine what it means in our contexts

## An Evolutionary Vision for the Architect
+ Our requirements shift more rapidly then they do for people who design and build buildings
+ For most things we create, we have to accept that once the software gets into hands of our customers we will have to react and adapt, rather than it being a never-change artifact
+ Thus our architects need to shift their thinking away from creating the perfect end product, and instead focus on helping create a framework in which the right system can **emerge**, and **continue to grow** as we learn more
+ We should think of our role more as town planners than architects for the built environment
+ In SimCity, you might designate part of your city as an industrial zone, and another part as a residential zone. It's then up to other people to decide what exact building get created, but there are restrictions: if you want to build a factory, it will need to be in an industrial zone

## Zoning
+ What are our zones? These are our service boundaries, or perhaps coarse-grained groups of services
+ As architect we need to worry much less about what happens inside the zone than what happens between the zones
+ That means we need to spend time thinking about how our services talk to each other, or ensuring that we can properly monitor overall health of our system

## A Principle Approach
> Rules are for the obedience of fools and the guidance of wise man - Generally attributed to Douglas Bader

+ Making decisions in system design is all about trade-offs, and microservice architectures give us lots of trade-offs to make
+ Framing here can help, and a great way to frame our decision making is to define a set of principles and practices that guide it, based on goals that we are trying to achieve

### Strategic Goals
+ The role of the architect is already daunting enough, so luckily we usually don't have to also define strategic goals
+ If you're the person who defining the company's technical vision, this may mean you'll need to spend more time with the nontechnical parts of your organization

### Principles
+ Principles are rules you have made in order to align what you are doing to some larger goal, and will sometimes change
+ You probably don't want loads of these fewer than 10 is good number - small enough that people can remember, or to fit on small posters

### Practices
+ Our practices are how we ensure our principles are being carried out
+ They are set of detailed, practical guidance for performing tasks
+ Practices should underpin our principles

### Combining Principles and Practices
+ One person's principles are another's practices
+ For a small enough group, perhaps a single team, combining principles and practices might be OK

### A Real World Example

## The Required Standard
+ When you are working through your practices and thinking about the trade-offs you need to make, one of the core balances to find how much variability to allow in your system
+ One of the key ways to identify what should be constant from service to service is to define what a well-behaved, good service looks like

### Monitoring
+ It is essential that we are able to draw up coherent, cross-service views of our system health
+ This has to be a system-wide view, not a service specific view

### Interfaces
+ Picking a small number of defined interface technologies helps integrate new consumers
+ Having one standard is a good number, two isn't too bad, either

### Architectural Safety
+ We cannot afford for one badly behaved service to ruin our party for everyone
+ We have to ensure that our services shield themselves accordingly from unhealthy, downstream calls

## Governance Through Code
+ Getting together and agreeing on how things should be done is a good idea, but spending time making sure people are following these guidelines is less fun, as is placing a burden on developers to implement all these standard things you expect each service to do

### Exemplars
+ Written document is good, and useful
+ But developers also like code, and code they can run and explore
+ If you have a set of standards of best practices you want to encourage, then having exemplars that you can point people to is useful

### Tailed Service Template

## Technical Debt
+ We are often put in situations where we cannot follow through to the letter on our technical vision
+ Often we need to make a choice to cut a few corners to get some urgent features out
+ Our technical vision exits for a reason, if we deviate from this reason, it might have a short-term benefit but a long-term cost
+ The architect's job is to look at the bigger picture, and understand this balance

## Exception Handling
+ Sometime we make a decision that is just an exception to the rule, in these cases, it might be worth capturing such a decision in a log somewhere for future reference
+ If enough exceptions are found, it may eventually make sense to change the principle or practice to reflect a new understanding of the world

## Governance and Leading from the Center
+ Part of what architects need to handle is governance

## Building a Team
+ I am a strong believer that great software comes from great people. If you worry only about the technology side of the equation, you're missing way more than half of the picture

## Summary
Core responsibilities of the evolutionary architect
+ Vision
+ Empathy
+ Collaboration
+ Adaptability
+ Autonomy
+ Governance

---

# Chapter 3: How to Model Services
> My opponent's reasoning reminds me of the heathen, who, being asked on what the world stood, replied, "On a tortoise." But on what does the tortoise stand? "On another tortoise." - Joseph Barker (1854)

Where to start? We'll look at how to think about the boundaries of your microservices that will hopefully maximize the upsides and avoid some of the potential downsides

## Introducing MusicCorp

## What Makes a Good Service?

### Loose Coupling
+ When services are loosely coupled, a change to one service should not require a change to another
+ A loosely coupled service know as little as it needs to about the services with which it collaborates

### High Cohesion
+ We want related behavior to sit together, and unrelated behavior to sit elsewhere
+ If we want to change behavior, we want to change it in one place, and release that change as soon as possible
+ So we want to find boundaries within our problem domain that help ensure that related behavior is in one place, and that communicate with other boundaries as loosely as possible

## Bounded Context
+ Domain consists of multiple bounded contexts, and residing within each are things that do not need to be communicated outside as well as things that are shared externally with other bounded contexts. Each bounded context has an explicit interface, where it decides what models to share with other contexts
+ Another definition of bounded contexts is "A specific responsibilities enforced by explicit boundaries"

### Shared and Hidden Models

### Modules and Services

### Premature Decomposition
+ At ThoughtWorks, we ourselves experienced the challenges  of splitting microservices too quickly
+ In many ways, having an existing codebase you want to decompose into microservices is much easier than trying to go to microservices from the beginning

## Business Capabilities
+ When you start think about the bounded contexts that exist in your organization, you should be thinking not in terms of data that is shared, but about the capabilities those contexts provide the rest of the domain
+ Thinking about data leads to anemic, CRUD based services
+ So ask first "What does this context do?", and then "So what data does it need to do that?"

## Turtles All they Way Down
+ At the start, you will probably identify a number of bounded contexts, but these bounded contexts can in turn contain further bounded contexts
+ When considering the boundaries of your microservices, first think in terms of the larger, coarser-grained contexts, and then subdivide along these nested contexts when you're looking for the benefits of splitting out these seams

## Communication In Terms of Business Concepts
+ The changes that we implement to our system are often about changes the business wants to make to how the system behaves
+ If our systems are decomposed along the bounded contexts that represent our domain, the changes we want to make are more likely to be isolated to one, single microservice boundary, this reduces the number of places we need to make a change, and allows us to deploy that changes quickly
+ It's also important to think of the communication between these microservices in terms of the same business concepts

## The Technical Boundary
+ Making decisions to model service boundaries along technical seams isn't always wrong

## Summary
+ The ideas presented in Eric Evans's Domain-Driven Design are very useful to us in finding sensible boundaries for our services, and I've scratched the surface here
+ Although this chapter has been mostly high-level, we need to get much more technical in the next

# Chapter 4: Integration
+ Getting integration right is the single most important aspect of the technology associated with microservices in my opinion
+ Do it well, and your microservices retain their autonomy, allowing you to change and release independent of the whole

## Looking for the Ideal Integration Technology
+ SOA, XML-RPC, REST?
+ We'll dive into those in a moment, but before we do, let's think about what we want out whatever technology we pick

### Avoid Breaking Changes
+ We want to pick technology that ensures this happens as rarely as possible
+ Example: if a microservices add a new fields to data it sends out, existing customers shouldn't be impacted

### Keep Your APIs Technology-Agnostic
+ The one certainty is change
+ It's is very important that you keep your the APIs used for communication between microservices technology-agnostic

### Make Your Service Simple for Consumers
+ We want to make it easy for consumers to use our service
+ Having a beautiful factored microservice doesn't count for much if the cost of using it as a consumer is sky high
+ We'd like to allow our clients full freedom in their technology choice, but on the other hand, providing a client library can ease adoption

### Hide Internal Implementation Detail
+ We don't want our consumers to be bound to our internal implementation, this leads to increasing coupling
+ This means that when want to change something inside our service, we can break our consumers by requiring them to also change
+ So any technology that pushes us to expose internal representation should be avoided

## Interfacing with Customers
+ Let's look at some of the most common options out there and try to work out which one works best for us
+ Let's pick a real-world example from MusicCorp

## The Shared Database
+ By far the most common form of integration that I or any of my colleagues in the industry is database integration
+ In this world, if other services want information from a service, they reach in to the database, and if they want to change, they reach into the database

## Synchronous Versus Asynchronous
+ Before we start diving into the specifics of different technology choices, we should discuss on of the most important decisions we can make in terms of how services collaborate
+ Should communication synchronous or asynchronous
+ Request/Response or Event-based

## Orchestration Versus Choreography

## Remote Procedure Calls
+ Remote procedure call refers to the technique of making a local call and having it execute on a remote server somewhere
+ There are a number of different types of of RPC technology out there
  + SOAP
  + Thrift
  + Protocol Buffers
  + RMI
+ Many of these technologies are binary in nature , like Java RMI, while SOAP uses XML for its message formats

### Technology Coupling

### Local Calls Are Not Like Remote Calls
+ The core idea of RPC is to hide the complexity of a remote call
+ Many implementations of RPC, though , hide too much
+ With PRC, though, the cost of marshalling and unmarshalling payloads can be significant, not to mention the time taken to send things over the network
+ This means you need to think differently about API design for remote interfaces versus local interfaces
+ You need to think about the network itself, the first of the fallacies of distributed computing is "The network is reliable", but network aren't reliable, they can and will fail

### Brittleness

### Is RPC Terrible?

## REST

### REST And HTTP

### Hypermedia As The Engine of Application State

### Beware Too Much Convenience

### Downsides to REST Over HTTP

## Implementing Asynchronous Event-Based Collaboration
+ We've talked for a bit about some technologies that can help us implement request/response patterns. What about event-based, asynchronous communication?

### Technology Choices
+ Two main parts we need to consider here: a way for our microservices to emit events, and a way for our consumers to find out those events have happened
+ Traditionally, message brokers like RabbitMQ try to handle both problems
  + Producers use an API to publish an event to the broker
  + The broker handles subscriptions, allowing consumers to be informed when an event arrives
  + These brokers can even handle the state of consumers
+ These systems are normally designed to be scalable and resilient, but that doesn't come for free, it can add complexity to the development process
+ Another approach is to try to use HTTP as a way of propagating events, ATOM is a REST-compliant specification that defines semantics for publishing feeds or resources

### Complexities of Asynchronous Architectures

### Services as State Machines
