# Distributed Systems


## Table of Contents

[Chapter 1 - Introduction](#Chapter1)
- [What is a Distributed System?](#1.1)
- [Design Goals](#1.2)
- [Types of Distributed Systems](#1.3)
<br>

[Chapter 2 - Architectures](#Chapter2)
<br>

[Chapter 3 - Communication](#Chapter3)
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
- 

<a name="1.3"></a>

### Types of Distributed Systems

---


<a name="Chapter2"></a>

## Chapter 2 - Architectures


<a name="Chapter3"></a>

## Chapter 3 - Communication

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
