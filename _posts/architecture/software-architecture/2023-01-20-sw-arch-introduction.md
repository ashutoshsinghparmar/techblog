---
layout: "post"  
title: "SW Architecture - Fundamentals"  
date: 2022-12-21  
permalink: "/architecture/intro.htm"
---

##### ility of SWA  
- Security  
- Performance  
- Legality  
- Scalability  
- Data  
- Auditability  
- Flexibility  
- Maintainability  
- Robustness  
- Resiliency  
- Reusability  
- Consistency  
** Structure, Abilities, Design Principles and Architectural Decision along with tradeoffs **

##### Expectations from an Architect  
- Defining Structure and Design principles which will **GUIDE** tech decisions for the enterprise  
- Constantly Analyse enterprise tech env and recommend improvements  
- Constantly follow and analyze the industry and technology trends  
- Ensure compliance with Architecture  
- Skill diversity: Have exposure to different tech, platforms, and environments  
- Have business domain expertise up to certain level  
- Possess exceptional interpersonal skills, negotiation and facilitation skils  
- Understand the political climate and navigate through it  

##### How you should approach this responsibility  
- Breadth vs Depth  
  - Breadth become more important than depth  
  - Knowing how many options are our there to solve a problem and how they differ with each other is more valuable skills than knowing how to implement all of them  
  - Its necessary to give up those desire to be deep in a particular area  
- Activties  
  - Identify charecteristics(-ilities) of the system under development  
  - Define guiding priciples  
  - Design pattern decision(Micro Service, micro kernel etc..)  
  - Identifying and outlining components  
  - Technology decisions  
- Communication between Architecture team and development team should be bidirectional  
- Handson Coding  
  - Do spikes to keep up with the coding  
  - Pair w/ development folks  
  - Implement some featuer(aviod to be a bottleneck)  
  - Do Code Reviews(helps w/ enforcing compliance)  

##### Designing ilities of System  
- These ilities will help you select the right architecture pattern  
- Always ask why  
- Dont confuse solutions with requirement(generally that comes from top)  
- Translating business decisions/requirements to ilities  


#### Architecture Design Patterns  

##### Layered Architecture(Monolith)  
- Enables  
  - Low Cost, Easy testability, Simplicity  
- Lacks  
  - Agility, deployability, Performance, Scalibility  

##### Microkernel Architecture(Moduler Monolith)  
- aka Plugin Architecture  
- A Core system and multiple plugin modules  
- Eg: Development IDEs, Web Browsers  
- Those plugin modules dont really have knowledge of others  
- Eg: Insurance Claim settlement system: Each region have plugin  
- Improves the blast radius of any change in plugins  
- Needs  
  - Need of Registry: to map plugin and its condition  
  - Standard Contract b/w plugin and core(Results into development of Adapters)  
- Enables  
  - Intermediate cost, Simplicity, testability, deployability, agility .
- Lacks  
  - Performance and Scalability  

##### Event Driven Architecture  
- 2 types  
  - Broker Topology  
  - Mediator Topology  

###### Broker Topology  
- Message Queue/Event Queue  
- Event Occurs  
- Event Processors process those events  
- Information flows in the form of event from one system to another via broker  
- **Error handling**: needs to be done separately and typically hard to implement  
- **Evolution** is easy in this  
- **Coordination**: Asyncronicity complicate it  

###### Mediator Topology  
- Events, Message Queue and then comes a Event Mediator  
- Mediator forwards the events to interested parties  
- Mediator holds the business process/workflow  
- Seen in SAGA-Coreographer Distributed transaction management  
- **Error Handling**: Mediator manages it  
- **Coordination**: Mediator manages it  
- **Evolution**: Multiple places to be changed  
- **Bottleneck**: Due to a single point to change for all services/components involved, it turns into a bottleneck  

###### CQRS(Command-Query Resposibility Seperation)  
- Separate DB for Command(write requests)  
- Separate DB for query(read requests)  
- Background sync between write and read db  
- **Eventual Consistency**: Due to DB sync  
- Not purely transactional  

- Enables  
  - Performance, agility, scalability, deploybility, bit costly  
- Lack  
  - Simplicity and testability  

##### Pipeline Architecture(Moduler Monolith)  
- aka pipe and filter architecture  
- Pipes  
  - Unidirectional  
  - Point-to-Point  
  - Any type of payload  
- Filters  
  - Self-contained  
  - Independent of other filters  
  - Apply some logic on payload and send forward  
  - Very lightweight  
  - Types  
    - Producer: Starting of the pipeline, Outbound only pipe  
    - Transformers: Apply some logic on data, both i/p and o/p pipes  
    - Testers: Either discard or forwards the data  
    - Consumer: Endpoint of pipeline, inbound pipe only  
- **Evolution**: Support highly  
- Enables  
  - Simplicity, Testability, Agility and cost effective  
- Lacks  
  - Performance, scalability, deployability  

##### Space Based Architecture  
- Objective in this style is get rid of DB, hence removing the bottleneck while scaling resources horizontally  
- DBs are replaced by In-memeory, combined w/ processing unit distributed caches  
- When we scale service we scale the DB with same amount, hence no bottle neck  
- Though data is maintained separately in a persistent place, which can be used for cache re-initialization in case of complete system down  

##### Microservice Architecture  
- Scalability  
- Agility  
- Hetrogeneous(Polyglot)  
- Interoperable  
- Protocol Aware Services(no middleware to abstract protocol)  
- Separate Deployability  
- Services are Small in size  
- Mix of Functional Services and operational services(logging, monitoring, auth etc..)  
- Service templates: A mechanism to address changes in common stuff across services(loggin, monitoring, json to xml converter etc)  
  - Everytime there is a change in Service Templates, all the services refering to service templates, will build and get the latest updated cross-cutting stuff  
  - Auth Functionality: putting it here saves the round trip overhead to A&A service  
  - It encourages Lower Coupling, more duplication  
- Size of Services  
  - Transactional Boundry  
  - Distributed Tx are complex, so try to avoid it at any cost  
  - Bounded Context: Business Process  
- Agility, deployability, testability, scalability are high  
- Performance and complexity is not that great  
- Cost is relatively high  

##### Service Oriented Architecture  
- Solves sharing resouces problem, eg: Address update of a customer across different type of products they are offering  
- Message bus is big part of it(Service Orchestration  and Process Choreography)  
- Various types of Services with in it  
  - Business Services: Owned and Defined by Business users on how they want to run their process, defined using WSDL, XML etc  
  - Enterprise Services: Owned by mainly Architectures, generally no granuality  
  - Application Services: Fine grained services  
  - Infrastructure Services: Auditing, logging, security etc  
- Ownership is with different teams for different types of teams, hence friction and coordination requirement  
- Expensive: Enterprise services buses are expensive  
- Protocol Agnostic: uses messeging middleware  
- Hetrogeneous Services  
- Contract Decoupling: Business drive IT and not the other way around  
- High Cost and Scalabilty  
- Low performance, agility, testability, deployability, simplicity  

