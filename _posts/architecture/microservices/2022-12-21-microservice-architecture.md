---
layout: "post"  
title: "Microservice Architecture"  
date: 2022-12-21  
permalink: "/architecture/miroservice/basics.htm"
---

####  Hx/Motivations of Microservices  
- Earlier we had Monolith and SOA  

#####  Monoliths  
- Single point of failure  
- Single process  
- Strong Coupling  
- Increased Complexity  
- Since everything lived inside a single system, overhead of network calls, de/serialization etc were not applicable  
- Sharing capabilities were not built  
- All components must be developed within same tech platform  
- Upgrade needed to be done for whole application at once  
- Inflexible and time consuming Deployment : All app should be deployed, increased scope of testing  
- Single pool of resources were shared across all the components, no way to allocate resources as per the requirement of the components  

##### SOA  
- Apps are exposing functionalities to outside world  
- Services were defined using SOAP & WSDL  
- ESB (Enterprise Service Bus) was responsible for all cross cutting concerns of application  
  - It lived between client & service and service & sevice  
  - Expensive and complex in long run  
  - Authentication, routing, validation everything was done in it  
- Sharing of data and functionality became easier compared to monoliths  
- Polyglot: services developed in various tech stack were able to communicate  

#### Characteristics of Microservice Architechture  
- As per Martin Fowler's first article on Microservice Architecture, see the link in additional resources  

##### Componentization via Services  
- Independent deployment  
- Well defined interfaces  
- Independent scaling of services  

##### Organised Around Business Capabilities  
- A single team owns a particular capability end-to-end  
- All the layers in service can evolve rapidly  
- Have well defined boundries  

##### Products not Projects  
- Team works closely with customers  
- Deliver and run the service  
- Better Customer Satifaction  

##### Smart Endpoints, Dumb Pipes  
- Dumb Pipes: Simple protocols  
- Smart Endpoint: Endpoint service the functionality knows everything  

##### Decentralized Governance  
- Each services can their own tailored standards as per their need  
- Independent to choose technology to solve a particular problem  

##### Decentralized Data Management  
- Each services using their own db  
- Right tool can be used for right task  
- Introduces the challenge of distributed transactions  
  - Mechanism to achive distributed transaction is complicated and fragile  
- Problem of Data Duplication, leading to inconsistency  
- Eventual consistency  
  - Due to complexity of distributed transaction this architecture emphesise on transactionless coordination between services or eventual consistency  
  - Have some kind of separate process to deal with mistakes  
  - Tradeoff is cost of fixing mistakes is less than the cost of lost business  

##### Infrastructure Automation  
- Short deployment cycles  

##### Design for Failure  
- Extensive logging and monitoring  
- During development, keep in mind that will can go wrong at sometime  
- Dont leave unhandled exceptions  
- Retry mechanism  
- Automatically restore the service in case of failure if possible  
- It helps in increase reliability of system  
- Better user exeperience  

##### Evolutionary Design  
- Start small, and upgrade each path gradually  
- Easy to identify the problems  
- 
#### Problems solved by this architecture  
1. Single Technology Platform Restrictions  
2. Inflexible Deployments  
3. Inefficient use of Compute Resources  
4. Large and Complex  
5. Complicated and expensive ESB  
6. Lack of toolings  


#### Distributed Transaction  
- **Saga Pattern**  
  - Divide single transaction into small transactions at microservice level  
  - Sub Transaction on success trigger next sub transaction using message  
  - Sub Transaction on failure trigger previous sub transaction using rollback message  
  - **Orchastration Saga Pattern** Another option is to introduce orchestration service, which takes the responsibility of executing sub transactions in sequence and also rollback in case of failure  
- **Outbox Pattern**  
  - Messages are first written to outbox table in microservice's db and then a publisher writes that to message bus  

#### Additional Resources  
- https://martinfowler.com/articles/microservices.html  
- 