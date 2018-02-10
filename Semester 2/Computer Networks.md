# Computer Networks


## Table of Contents

[Lecture 1](#Lecture1)
<br>
[Lecture 2](#Lecture2)
<br>
[Lecture 3](#Lecture3)
<br>
[Lecture 4](#Lecture4)
<br>
[Formulas](#Formulas)
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
- **Connection Oriented**
  - Connection must be set up for use and torn down after
  - Ex: Phone Call
  - **Types of Reliability for Connection Oriented**
    - Reliable Message Stream
    - Reliable Byte Stream
    - Unreliable Connection
- **Connectionless**
  - Messages are handled separately
  - Ex: Postal Delivery
  - **Types of Reliability for Connectionless**
    - Unreliable Datagram
    - Acknowledged Datagram
    - Request - Reply
- Each service is characterized by its reliability
  - Reliability means the message is acknowledged

### Service Primitives
- Layer provides operations (Primitives) to the layer above
  - If protocol stack is in the OS then the operations are system calls
    - The calls cause a trap to kernel mode
    - This turns control of the machine to the OS to send the required packets

### Service Protocol Relationship
- A layer provides a set of operations to the layer above it (Vertical)
- A protocol is a set of rules about format and meaning of packets exchanged within a layer
  - Layer talks to its peer using a protocol (Horizontal)

### OSI Reference Model
|Number|Layer|Purpose|
|------|-----|-------|
|7|Application| Provides functions needed by users|
|6|Presentation| Converts different representations|
|5|Session| Manages task dialogs|
|4|Transport| Provides end-to-end delivery|
|3|Network| Sends packets over multiple links|
|2|Data Link| Sends frames of information|
|1|Physical| Sends bits as signals over the channel|

- **Physical Layer**
  - Determines specs for all physical components
    - Type of Cabling
    - Interconnect methods
    - Data encoding
    - Electrical properties
- *Ex: Physical Layer Components of a Computer?*
  - NIC: Network Interface Card
  - It has a MAC Address (Physical Address) of a computer


- **Link Layer**
  - Data transfer between network elements
    - Moving frames from one node to another
    - Ex: Move from physical to network and vice versa
  - Has Error Detection / Correction capabilities
  - Control access to the shared channel
  - Has Sub Layers
    - **MAC (Media Access Control)**
      - Gives data to the Network Interface Card
      - Controls access to media through the following
        - Uses Carrier Sense Multiple Access / Collision Detection
        - Token Passing
    - **LLC (Logic Link Layer)**
      - Manages data link interface (Service Access Points (SAPs))
      - Detects transmission errors using a Cyclic Redundancy Check (CRC)
        - Ask sender to resend packet if it's bad


- **Network Layer**
  - Controls subnet operations
  - Responsibilities
    - Network Addressing
    - Routing of datagrams (packets) form source to destination
    - Handling congestion in conjunction with higher layers
    - *Ex: IP, Routing Protocols*

- **Transport Layer**
  - Data Transfer
  - Reliable data delivery
  - Receives info from upper layers and *segments* into packets
  - Error detection and correction
  - *Ex: TCP, UDP*


- **Session Layer**
  - Allows applications to maintain ongoing session
  - Synchronization
    - Checkpoints, allows users to pickup where they left off incase of crash
  - *Ex: Operating Systems, Scheduling*


- **Presentation Layer**
  - Data Representation
  - Allow application to interpret data
  - *Ex: ASCII / EBCDIC, JPG, MP3*


- **Application Layer**
  - Supports network applications
  - Network processes -> applications
  - Gives user applications access to network resources
  - *Ex: FTP, SMTP, HTTP, Telnet*


- **Layers Working Together**
  - Each layer has a Protocol Data Unit (PDU)
    - Used for peer to peer contact between layers
  - **Data is handled** by Application, Presentation, Session layers
  - **Data is segmented** by Transport layer
  - Network layer **puts data into packets**
  - Link layer **frames the packets** for transmission
  - Physical layer **converts packets into bits** and send it out
  - The computer that receives this, reverses the process.


- *Pros and Cons*
  - **(+)** Very influential model with clear concepts
  - **(-)** Models, protocols and adoption all bogged down by politics and complexity

### TCP/IP Reference Model
|Number|Layer|Purpose|Contents|
|------|-----|-------|--------|
|5|Application| Provides functions needed by users|HTTP, SMTP, RTP, DNS|
|4|Transport| Provides end-to-end delivery|TCP, UDP|
|3|Internet| Defines IP and ICMP Protocols (ICMP helps IP)|IP, ICMP|
|2|Link| Describes what links (Serial Lines / Ethernet) need to do to meet needs of the internet layer|DSL, SONET, 802.11, Ethernet|
|1|Physical| Sends bits as signals over the channel||

- Physical, Link, Internet are defined above
- **Transport Layer**
  - Allows source and destination hosts to carry on a conversation between peer entities
  - Defines Two Protocols
    - **TCP**
      - Reliable, Connection Oriented Protocol
      - Handles flow control so fast sender cant swamp slow receiver
    - **UDP**
      - Unreliable, Connectionless Protocol
      - Used when we need prompt delivery > accurate delivery
      - *Ex: Transmitting Video or Speech*

- **Application Layer**
  - Contains all the higher level protocols
  - **TELNET**: Provides a bidirectional interactive text-oriented communication facility using a virtual terminal connection
  - **FTP**: File Transfer Protocol
  - **SMTP**: Simple Mail Transfer Protocol
  - **DNS**: Domain Name Systems, mapping host names onto their network address
  - **HTTP**: Hyper Text Transferee Protocol, fetching pages on the World Wide Web
  - **RTP**: Real Time Protocol, delivering real-time media such as voice or movies

- *Pros and Cons*
  - **(+)** Very successful protocols that worked well and thrived
  - **(-)** Weak model derived after the fact from protocols

### Internet
- Before Internet was **ARPANET**
  - Advanced Research Projects Agency Network
  - Decentralized, packet-switched network
- Modern Internet more complex
- ISP (Internet Service Provider) networks are the backbone
    - They connect or peer to exchange traffic at IXPs (Internet Exchange Point)
    - Between networks, traffic exchange is set by business agreements
    - Customers connect at the edge through   
      - Cable, DSL, 3G/4G wireless
- Data centers concentrate many servers ("The Cloud")
- Most traffic is content from data centers (especially videos)

**IXP** Internet exchange point where ISPs connect networks to exchange traffic

### Internet Architecture
- **Network Edge**
  - Hosts - Clients & Servers
  - Servers often in data centers
- **Access Networks, Physical Media**
  - Wired, Wireless communication links
- **Network Core**
  - Interconnected Routers
  - Network of Networks

#### Host
- Host sending function
  - Take application message
  - Breaks it into packets of *length L* bits
  - Transmits packet into network at *transmission rate R*
- Packet Transmission Delay
  - = time needed to transmit *L-bit* packet into link
  - = L(bits) / R(bits/sec)

#### Physical Media
- **Bit**
  - Propagates between transmitter / receiver pairs
- **Physical Link**
  - What lies between transmitter & receiver
- **Guided Media**
  - Signals propagate in solid media: Copper, Fiber, Coax
- **Unguided Media**
  - Signals propagate freely: radio

#### Network Core
- Mesh of interconnected routers
- **Packet Switching**
  - Hosts break application-layer messages into *packets*
  - Forward packets from one router to next; from source to destination
  - Each packet transmitted at full link capacity
- Two Key Functions
  - **Routing** - Determines route taken by packets (from source to destination)
  - **Forwarding** - Moves packets from router input to appropriate router output

##### Packet Switching - Store & Forward
- Takes L/R seconds to transmit L-bit packet into link at R-bits/sec
- **Store and Forward**
  - Entire packet must arrive at router before it can be transmitted to next link
- *End-to-End Delay = 2L/R*

##### Packet Switching - Queueing Delay, Loss
- If bits arrive faster than the transmission rate of the link
  - Packets will queue (wait to be transmitted)
  - Packets can be lost if buffer fills up

#### Alternative Core - Circuit Switching
- End-to-End resources reserved for 'call' between source & destination
- If a circuit is not used, it is idle
- Used in traditional telephone networks

#### FDM vs TDM in Circuit Switching
- Frequency Division Multiplexing
  - Not as flexible as TDM
  - Fixed bandwidth usage at a given time
  - Latency (time it takes for data to get to destination) of FDM > TDM
- Time Division Multiplexing
  - More flexibility and efficiency
  - All of the bandwidth is used at a given time
  - Dynamically allocates time periods to signals that need more bandwidth and reduces time periods for signals that do not need it

#### Packet Switching vs Circuit Switching
- Packet
  - Allows more users to use network
  - Packet Delay & Loss Possible
  - Need protocols for reliable data transfer
- Circuit
  - Limited users
  - All resources being used during a 'call' between source and destination
  - Reliable connection (even though all resources being used for it)

#### Network of Networks
- How to connect millions of access ISPs (Internet Service Provider)?
  - Don't want to connect each ISP to each other because O(n^2) not scalable
  - Connect Access ISP's to Global ISP (will be multiple due to business competition)
  - Must interconnect all the Global ISPs using Internet Exchange Points and Peer links
  - To handle multiple access ISPs, create regional nets then connect those to Global ISP
  - Content Providers (Google) will have private network to bring content closer to customer

### 3G Networks
- Based on spatial cells
  - Each cell provides wireless service through the base station cell
- Base stations connect to core network
  - Finds other mobiles and send data to the phone network
- As mobiles move, base stations hand them off from one to cell to the next
  - Network tracks their location

### Wireless LANs
- Clients communicate through an Access Point that is *wired* to the rest of the network
- ISM = Industrial, Scientific & Medical
  - ISM Bands defined by ITU-R
    - 902-928 MHz
    - 2.4-2.5 GHz
    - 5.725-5.825 GHz


- Signals in ISM band vary in strength
  - Due to multipath fading caused by reflections
  - OFDM (Orthogonal Frequency Division Multiplexing)
    - Complex transmission scheme to fight against multipath fading


#### RFID (Radio Frequency Identification)
- Tag (no battery) are placed on objects
- Readers send signals
  - Tags reflect the signals to communicate

#### Sensor Networks
- Small devices spread out over an area
  - The devices send data via wireless hops


### Network Standardization
|Body|Area|Examples|
|----|----|--------|
|ITU <br> International Telecommunication Union| Telecommunications| G.992, ADSL <br> H.264, MPEG4|
|IEEE <br> Institute of Electrical and Electronics Engineers| Communications| 802.3, Ethernet <br> 802.11, WiFi|
|IETF <br> Internet Engineering Task Force| Internet| RFC 2616, HTTP/1.1 <br> RFC 1034/1035,DNS|
|W3C <br> World Wide Web Consortium| Web |HTML5 standard <br> CSS standard|

**Powers of 10 for Rates**
**Powers of 2 for Storage**
**B = bytes**
**b = bits**

### Delay, Loss, Throughput in Networks
- Delay of Nodal Processing =
  - (+) Processing Delay
  - (+) Queueing Delay
  - (+) Transmission Delay
  - (+) Propagational Delay


- Throughput
  - Rate at which bits transferred between sender/receiver

### Network Security
- Can get malware from
  - Virus: Self-replicating infection by receiving / executing object
    - Ex: Email
  - Worm: Self-replicating infection by passively receiving object that gets itself executed
- Spyware malware can record keystrokes and internet activity


- **Denial of Service (DoS)**
  - Make resources unavailable by overwhelming resource with fake traffic
  - Steps:
    1. Select Target
    2. Break into hosts around the network
    3. Send packets to target from compromised hosts


- **Packet Sniffing**
  - Network interface that reads/records all packets (even passwords)


- **IP Spoofing**
  - Send packet with false source address



---

<a name="Formulas"></a>
## Formulas
|Name|Formula|Breakdown|Other|
|----|-------|---------|-----------|
|Packet Transmission Delay| L / R | L = Length of Packet (in bits) <br> R = Transmission Rate of Network (in bits/sec)||
|End-to-End Delay (Store & Forward - Packet Switching)| 2L / R |L = Length of Packet (in bits) <br> R = Transmission Rate of Network (in bits/sec)||
|Packet Propagation Delay| d / s | d = Length of physical link <br> s = Propagation speed in medium (~ 2x10^8 m/sec)||
|Packet Queueing Delay| (L * a) / R | L = Packet Length (bits) <br> R = Link Bandwidth (bps) <br> a = Average packet arrival rate | La/R ~ 0 -> Small Average Queueing Delay <br> La/R = 1 -> Average Queueing Delay Increases <br> La/R > 1 -> More work arriving than can be serviced, average delay = infinite!|



---
