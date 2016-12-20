# Contact Repository using Domain Driven Design

## 1. Talk to Domain Expert
Our domain is Contact Repository

- **Domain Expert**: I want to see the number of contacts in Repository, specify by status _imported_, *exported*
- **Domain Expert**: I want to add new contact when I have new one
- **Domain Expert**: I want to export a list of contacts to call them
- **Analyst**: Should I delete it after it is exported
- **Domain Expert**: No, no, no. I still want to see it after it's exported, just mark it as *exported*
- **Analyst**: What do you want to see from a contact?
- **Domain Expert**: Customer information: name, email, mobile, address; where is it from: landingpage, lead, edumall ...; the type of the contact: c3_cod or c3
- **Analyst**: Ok

Business aspects:
+ Import contact
+ Export contact

### Import contact
Add contact repository

Each contact has:
+ Customer information
+ Type of contact
+ Status of contact: each contact should have to be imported or exported
+ Source of contact: each contact can come from different source: edumall, landingpage, lead ...
+ Order: order of the contact

### Export contact
Change contact status to exported, and never export it again

So contact can:
+ **export**


### Ubiquitous Language
+ **Contact**: an order of customer
+ **Customer**: who orders
+ **Status**:
+ **Source**: where contact come from


## 2. Create models

**Contact** (Entity)  
        ---> **Customer** (Entity)  
        ---> **ContactType** (Value Object)  
        ---> **ContactStatus** (Value Object)  
        ---> **ContactSource** (Value Object)  
        ---> **Order** (Entity or Value Object ?)

### Aggregate
We have **Contact Aggregate** with Contact is **Aggregate Root**, and that's the only Aggregate we have so far.

Why not Customer is the Aggregate Root?

Let's say, it a contact is destroyed, should customer information be destroyed too?. Hold on, we have some buzzwords here:
+ **Customer**
+ **Contact**
+ **Order**

What is a contact exactly?

Should we call it order instead of contact?
+ An order has *customer information*, *order detail*
+ A contact has *customer information*, *order* -> this is the way domain expert says

And now, back to above question, should customer has it own aggregate?

How to answer this question? Developer saying or domain expert saying?

I have no idea, but let customer has it own aggregate.

### ERD
[ERD](./assets/dmarol-erb.md)

### Service
We can have a ContactService serving import contact and export contact. But we can put action import and export to Contact, so?

Let's talk more about import and export

#### Import contact


#### Export contact
