# Distributed Systems


## Table of Contents

[Chapter 1 - Introduction](#Chapter1)
- [What is a Distributed System?](#1.1)
- [Design Goals](#1.2)
- [Types of Distributed Systems](#1.3)
<br>

[Chapter 2 - Architectures](#Chapter2)
- [Architectural Styles](#2.1)
- [Middleware Organization](#2.2)
- [System Architecture](#2.3)
<br>

[Chapter 3 - Communication](#Chapter3)
- [Foundations](#3.1)
- [Remote Procedure Call](#3.2)
<br>

[Appendix](#Appendix)
- [Sockets Programming with Java](#a.1)
- [Multithreaded Programming with Java](#a.2)
- [Code Migration](#a.3)
- [Java RMI](#a.4)

---

<a name="Chapter1"></a>

## Chapter 1 - Introduction

<a name="1.1"></a>

### What is a Distributed System?
- **Distributed System**: Collection of nodes collaborating to appear as a single coherent system
  - **Node**: Autonomous computing element
    - Each node has its own clock
    - Leads to synchronization issues because no global clock exists
- Nodes communicate with each other nodes (neighbours) in the same system
  - **Structured**: Well defined set of neighbours
  - **Unstructured**: Each node references randomly selected nodes from the system
- **Distribution Transparency**: Nodes operating the same no matter *when*, *where*, or *how* a user interacts with the system
  - Cannot tell
    - Where a computation takes place
    - Where data is stored
- **Partial Failures**: Only a part of the distributed system fails at a time
    - Hard to recover
    - Impossible to hide
- Distributed systems contain a middleware that serves as an OS for the individual systems
  - It contains components and functions that don't need to be implemented by applications separately

<a name="1.2"></a>

### Design Goals
- **Sharing Resources**
  - Cloud based storage
  - Peer-to-Peer assisted media streaming
  - Shared mail services
  - Shared web hosting
- **Distribution Transparency**
  - Types
|Transparency|Description|
|------------|-----------|
|Access|Hide data representation & how object is accessed|
|Location|Hide where an object is located|
|Relocation|Hide that an object may change locations during use|
|Migration|Hide that an object may move to another location|
|Replication|Hide that an object is replicated|
|Concurrency|Hide that an object may be shared by multiple users|
|Failure|Hide the failure / recovery of an object|

  - Full distribution transparency is too much
    - Will cost performance
  - Some communication delays can't be hidden
  - Impossible to completely hide failures
- **Openness**
  - Conforming to well defined interfaces
  - Easily interoperate
  - Portability
  - Extensible
- **Scalability**
  - 3 Components to scale
    - **Size Scalability**
      - Number of users
    - **Geographical Scalability**
      - Distance between nodes
      - Difficult to transition between LAN & WAN
        - WAN links are also unreliable
      - No multipoint communication
        - Search broadcast requires its own naming/directory service
        - The above service will have its own scaling problems
    - **Administrative Scalability**
      - Number of admin domains
      - Computational grids share expensive resources between domains
      - Managing shared equipment
  - **Root causes of scalability problems**
    - Limited computational capacity (limited by CPUs)
    - Limited storage capacity (and transfer rate to store)
    - Limited networking between user and central service

- **Scaling Techniques**
 - Using Asynchronous Communication
 - Separate handler for incoming response
  - However, not all applications can implement this model
- Partitioning Data & Computations
  - Move computations to the clients
  - Decentralized naming services (DNS)
  - Decentralized information systems (WWW)
- Replication & Caching
  - Replicated file servers and databases
  - Mirrored Web Sites
  - Web Caches
  - File Caching (at server & clients)
  - **Cons of Replication**
    - Having multiple copies can lead to inconsistencies
    - Requires global synchronization

- **Pitfalls of Developing Distributed Systems**
  - Many distributed systems are needlessly complex
    - Caused by false assumptions
  - Some of the common assumptions
    - Network is reliable
    - Network is secure
    - Network is homogeneous
    - Topology does not change
    - Latency is zero
    - Bandwidth is infinite
    - Transport cost is zero
    - Only one administrator


<a name="1.3"></a>

### Types of Distributed Systems

### High Performance Distributed Computing Systems
- **Parallel Computing**
  - High performance computing started with parallel computing
- **Cluster Computing**
  - Homogeneous (Same OS, Near-Identical Hardware)
  - 1 Master Node (Managing Node)
    - Multiple Compute Nodes
- **Grid Computing**
  - Heterogeneous
  - Dispersed over organizations, can span WAN
  - Allow collaborations by using virtual organizations
    - Authorization on resource allocation based on users (ID's)
- **Cloud Computing**
  - Hardware
    - Processors, Routers, Power Systems
  - Infrastructure
    - Allocating / Managing virtual storage devices and servers
  - Platform
    - Higher level storage abstraction (Amazon S3 Buckets)
  - Application
    - The actual app

### Distributed Information Systems
- **Integrating Applications**
  - Basic Networked application follows client-server model
    - Server makes the services available to remote clients
  - Integration: clients combine multiple requests to different applications, collect responses and present final result to user
  - Next Step: **Enterprise Application Integration** Allowing direct application to application communication
  - Ways to Integrate
    - **File Transfer**
      - Simple but not flexible
        - Need File Format / Layout information
        - Need to figure out file management
        - Update propagation and notifications
    - **Shared Database**
      - More flexible but needs common data scheme
      - Risk of bottleneck
    - **Remote Procedure Call**
      - Effective for executing a series of actions
    - **Messaging**
      - Caller / Callee need to be running at the same time
      - Allows separation in time & space
- **EAI: Enterprise Application Integration**
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/eai.PNG)
- **Transaction Processing Monitor (TPM)**
  - Transactions often distribute data over several servers
  - Need to coordinate and execute the transaction properly
  - TPM fulfills that role
- **Remote Procedure Call (RPC)**
  - Requests are sent through a local procedure call
  - Packaged as a message
  - Processed
  - Responded through the message
  - Returns result as a return from the call
- **Message Oriented Middleware (MOM)**
  - Messages sent to logical contact point and forwarded to applications

### Distributed Systems for Pervasive Computing
- Nodes are small, embedded in larger systems
  - System naturally blends into the user's environment
- 3 Subtypes
  - **Ubiquitous Computing Systems**
    - Continuous interaction between system and user
    - Distribution
      - Devices are networked and transparently accessible
    - Interaction
      - Interaction between user / device is unobtrusive
    - Context Awareness
      - System is aware of user's context to optimize interaction
    - Autonomy
      - Autonomous operation, without human intervention, highly self managed
    - Intelligence
      - System can handle a wide range of dynamic actions / interactions
  - **Mobile Computing Systems**
    - Inherently Mobile
    - Disruption-Tolerant Networking
    - Implied that device location is ever-changing
      - Change of local services, reachability
  - **Sensor & Actuator Networks**
    - Collaboration between sensing and actuation of the environment
    - 1 : Many relationship between nodes and sensors
    - Simple, Small, Battery Powered Sensors 
---


<a name="Chapter2"></a>

## Chapter 2 - Architectures

<a name="2.1"></a>

### Architectural Styles


<a name="2.2"></a>

### Middleware Organization


<a name="2.3"></a>

### System Architecture


---


<a name="Chapter3"></a>

## Chapter 3 - Communication

<a name="3.1"></a>

### Foundations


<a name="3.2"></a>

### Remote Procedure Call


---

<a name="Appendix"></a>

## Appendix

<a name="a.1"></a>

### Sockets Programming with Java

<a name="a.2"></a>

### Multithreaded Programming with Java

<a name="a.3"></a>

### Code Migration

<a name="a.4"></a>

### Java RMI
