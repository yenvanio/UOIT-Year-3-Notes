# Computer Networks


## Table of Contents

[Lecture 1](#Lecture1)
<br>


<a name="Lecture1"></a>
## Lecture 1

### Network Hardware
Networks can be classified by
  - **Transmission Technology**
    - Point to Point: Connect individual pairs of machines (unicast)
    - Broadcast: The communication channel is shared by all machines on the network
  - **Network Scale**
    - Vicinity - PAN (Personal Area Network)
    - Building - LAN (Local Area Network)
    - City - MAN (Metropolitan Area Network)
    - Country - WAN (Wide Area Network)
    - Planet - The Internet (Network of all networks)
- **Internetwork** refers to networks made up of smaller networks. Internet is the set of all connected networks

### Internetwork
- A collection of interconnected networks
- Connected through gateways
- Types of Gateways
  - Low-Level: Prevent from making connections between different kinds of networks
  - High-Level: Connection will only work for particular applications
  - Network Layer (In the middle): Router is the gateway that switches packets at the network layer

### Network Software

#### Protocol Layers
- Main structuring method used to divide up network functionality
  - Each protocol talks to its peer
  - Each layer communicates only with the one below it
  - Low layer services are accessed by interface
  - At the bottom, messages are carried by the medium
- Each low layer adds its own header to the message to transmit and removes it, once it receives it.
- Layers can also split / join messages
- **Diagram shows the protocols adding headers to layer below it in the source machine and passing it to destination machine where it builds it back up**

### Design Issues

- Each layer solves a problem
  - Must include tools to take care of recurring design issues

|Issue|Example Mechanisms at Different Layers|
|-----|--------------------------------------|
|Reliability Despite Failures|Codes for error detection/correction <br> Routing around failures|
|Network Growth and Evolution| Addressing and Naming <br> Protocol Layering|
|Allocation of resources like bandwidth | Multiple Access <br> Congestion Control |
|Security against various threats | Confidentiality of messages <br> Authentication of communicating parties|

### Connection-Oriented vs Connectionless
- Connection Oriented
  - Connection must be set up for use and torn down after
  - Ex: Phone Call
- Connectionless
  - Messages are handled separately
  - Ex: Postal Delivery





---
