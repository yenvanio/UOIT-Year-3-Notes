# Computer Networks


## Table of Contents

[Lecture 1 - Introduction](#Lecture1)
<br>
[Lecture 2 - The Physical Layer](#Lecture2)
<br>
[Lecture 3 - The Data Link Layer](#Lecture3)
<br>
[Lecture 4 - Medium Access Control (MAC) Sublayer](#Lecture4)
<br>
[Formulas](#Formulas)
<br>

<a name="Lecture1"></a>
## Lecture 1 - Introduction

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
- **Frequency Division Multiplexing**
  - Not as flexible as TDM
  - Fixed bandwidth usage at a given time
  - Latency (time it takes for data to get to destination) of FDM > TDM
- **Time Division Multiplexing**
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

<a name="Lecture2"></a>
## Lecture 2 - The Physical Layer
- Physical layer is the foundation for the other layers
  - Determines properties of network
    - Wires, Fiber, Wireless Limit
  - Determines throughput, latency and error rate
- Key problem is sending bits (digital) using signals (analog)
  - Called **Modulation**
- Can send information on wires by varying
  - Voltage, Current, Frequency or Phase

### Bandwidth
- Analog Bandwidth is measured in *Hz*
- Digital Bandwidth is the maximum data rate of a channel in *bps*

### Fourier Analysis
- Time varying signals can be represented as a series of components (harmonics)
  - Or represented by an infinite number *sines* and *cosines*
- **T** = Signal Period
- **F** = Fundamental Frequency = 1 / T

### Bandwidth Limited Signal
- Transmission of ASCII character `b` to `01100010`
- Less bandwidth means losing some of the harmonics
  - Degrades the received signal
- Can achieve higher data rates
  - Coding schemes that use several voltage levels

### Maximum Data Rate of a Channel
- **Nyquist's Theorem**
  - Signal goes through low-pass filter of bandwidth (B)
  - Filtered signal can be reconstructed by making exactly 2B samples per second
  - *Theorem Assumes: Noiseless channel*
  - Max Data Rate (R) = 2B * log(base 2) * V
    - Relates data rate (R) to the bandwidth (B) and number of signal levels (V)

- **Shannon's Theorem**
  - Max Data Rate (R) = B * log(base 2) * (1+ S/N)
    - Relates data rate (R) to the bandwidth (B) and signal power (S) relative to the noise power (N) or signal-to-noise ratio (S/N)
    - *B = How fast signal can change*
    - *S/N = How many levels can be seen*

### Guided Transmission Media (Wires & Fiber)
|Guided Media|Unguided Media|
|------------|--------------|
|**Copper Wire** <br> Twisted Pairs <br> Coaxial Cable <br> Power Lines| Terrestrial wireless <br> Satellite <br> Lasers through the air|
| **Fiber Optics** <br> Single Mode <br> Multimode | - |

**Full Duplex Link** - Used for transmission in both directions at the same time
<br>
**Half Duplex Link** - Both directions, not at the same time
<br>
**Simplex Link** - One fixed direction at all times
<br>

#### Wires - Twisted Pair
- Twists reduce interference
- Signal is carried as the difference in voltage between the wires
- Bandwidth depends on **thickness of wire** and **distance travelled**
- Categories
  - Cat 5
    - 4 Twisted pairs grouped together
  - Cat 6 (UTP) - Unshielded Twisted Pair
  - Cat 7 (STP) - Shielded Twisted Pair

#### Wires - Coaxial Cable
- Two concentric copper conductors
- Shielding, Bandwidth & rates > Twisted Pair
- Common Use: TV
- Bidirectional , Broadband (multiple channels on cable)
- Categories
  - 50-ohm: Digital Transmission
  - 75-ohm: Analog Transmission

#### Wires - Power Lines
- Convenient to use, but horrible for sending data
- Data is at much higher frequencies

#### Wires - Fibre Optic Cables
- Glass fiber carrying light pulses
  - pulse of light = a 1 bit
  - no light = a 0 bit


- Used for high-speed transmission from point to point
- Low error rate
  - Light is immune to EM noise


- 3 key components
  - Light Source
  - Transmission Medium
  - Photodiode (generates electrical pulse when exposed to light)


- Has huge bandwidth and low signal loss
  - high rates over long distances


- **Single Mode**
  - Core is narrow (10 um)
    - Light can't bounce around
  - Used with lasers for long distances

- **Multi Mode**
  - Core diameter is 50um
  - Light can bounce around
    - Each ray > critical incident has a different mode
  - Used with LED's for cheaper, shorter distance links


### Network Topology
- **Bus Topology**
  - All computers connected to a single communication line
    - Carries messages in both directions
  - Simple, Low Cost
  - Only one computers can message at a time


- **Star Topology**
  - All computers are centered around one hub node
  - If hub goes down, whole network done
  - Two or more computers can send messages at a time  


- **Ring Topology**
  - Connects all nodes in a closed loop
    - Messages travel in one direction
  - One computer fails, whole network fails
    - Hard to add computers to network
  - Each computer serves as a repeater to boost signals
  - Sending Data by tokens
    - Only computer who has token can send data

### Network Hardware
- **Network Interface cards**
  - Connects node to media
  - Unique MAC address  (6 bytes long)
- **Network linking device**
  - Connects nodes to network
- **Hub**
  - Center of a star network
  - All nodes receive transmitted packets
  - Slow & Insecure
- **Switches**
  - Replacement for hubs
  - Only intended node receives the transmission
  - Fast & Secure
- **Bridge**
  - Connects two or more LANs together
- **Router**
  - Connects internal networks to the internet
- **Gateway**
  - Connects two dissimilar networks


### Electromagnetic Spectrum
- Signal carried in electromagnetic spectrum
- **Frequency**
  - Number of oscillations per second (Hz)
- **Period**
  - Time between two consecutive maxima / minima
  - T = 1/f (seconds)
- **Wavelength**
  - Distance between two consecutive maxima / minima
  - Measured in meters
- Speed light
  - c = 3 x 10^8 m/sec
- Relationships
  - Wavelength = c/f

### Radio Transmission
- Radio signals penetrate buildings well and propagate for long distances without loss
- VLF, LF, MF Bands
  - Radio waves follow curvature of the earth
- HF band
  - Radio waves bounce off the ionosphere

### Microwave Transmission
- Travel in straight line
- Used indoors & outdoors
  - Wifi
  - 4G, Satellites
- Signal is reflected by everyday objects
- Do not penetrate buildings

### Light Transmission
- Line-of-sight light can be used for links
  - Light is highly directional
    - Used for LEDs, Lasers

### Communication Satellites
- Effective for broadcast distribution
  - Also for anywhere/anytime communications
- Receives signal on one frequency
  - Regenerates it
  - Amplifies it
  - Sends it back on different frequency
- Satellite placed in a specified orbit
  - Higher = Longer period
  - Orbit governed by *Van Allen Belts*
  - Any satellite flying within them will be destroyed by the belts

#### Geostationary (GEO) Satellite
- Orbits 35,000km above a fixed location
- Different bands
  - Higher frequency suffers greater spreading compared to lower frequency
  - Uplink band is always of higher frequency because connected to power
    - Helps compensate for poor performance
- Footprint
  - Shows radiated power of antenna at each point
- VSAT (Very Small Aperture Terminals)
  - Low cost micro station
  - Can communicate with hub to extend coverage

### Medium Earth Orbit (MEO) Satellite
- Lower altitude
  - Between the two Van Allen belts
- Used for navigation vs communication
  - GPS
- GPS receiver must observe 4 satellites
  - Three of them provide distance measurement
  - Fourth adjusts timing offsets

### Low Earth Orbit (LEO) Satellite
- Lower to the ground
  - Better for point to point communication
    - Better signal and less time delay


### Wireless vs Fiber vs Satellite
|Wireless|Fiber|Satellite|
|----|-----|-------------|
|**Pros** <br> Easy and inexpensive to deploy <br> Naturally supports mobility <br> Naturally supports broadcast|**Pros** <br> Easy to engineer a fixed data rate over point-to-point links <br> Enormous bandwidth over long distances| **Pros** <br> Can rapidly set up anywhere/anytime communications (after satellites have been launched) <br> Can broadcast to large regions|
|**Cons** <br> Transmissions interfere and must be managed <br> Signal strengths hence data rates vary greatly|**Cons** <br> Can be expensive to deploy <br> Doesn't readily support mobility or broadcast|**Cons** <br> Limited bandwidth and interference to manage

### Digital Modulation
- Process of converting data bits into signals


#### Baseband Transmission
- Signal occupies frequencies from 0 up to a max
  - Common for Wires

- **Non-Return-to-Zero (NRZ)**
  - Positive voltage = 1
  - Negative voltage = 0


- **Manchester Encoding**
  - Mixes clock signal w/ data signal
    - XOR's the signals together
  - When clock is XOR'd with 0 level
    - Makes it a low-to-high transition
  - When clock is XOR'd with 1 level
    - Makes it a high-to-low transition


- **Non-Return-to-Zero-Inverted (NRZI)**
  - Same as NRZ but
    - 1 = Transition
    - 0 = No Transition

#### Passband Transmission
- The signal occupies a band of frequencies around the frequency of the carrier signal
  - Common for Wireless
- Schemes that regulate the amplitude, phase or frequency of a carrier signal to convey bits


- **Amplitude Shift Keying (ASK)**
  - Two different amplitudes are used to represent 0 and 1.


- **Frequency Shift Keying (FSK)**
  - Two or more different frequencies are used


- **Phase Shift Keying (PSK)**
  - The carrier wave is systematically shifted a certain amount of degrees at each symbol period
  - If two phases, **Binary Phase Shift Keying (BPSK)**
  - If we use 4 shifts, **Quadrature Phase Shift Keying (QPSK)**


- Usually amplitude and phase are modulated in combination
  - **Quadrature Amplitude Modulation (QAM)**
  - QAM-16 uses 4 bits per symbol
  - QAM-64 uses 6 bits per symbol

### Frequency Division Multiplexing
- Share channels among many signals
  - Divides spectrum into frequency bands
  - Each user has possession of some band to send their signal


- **Orthogonal Frequency Division Multiplexing (OFDM)**
  - The channel bandwidth is divided into many subcarriers that independently send data


### Time Division Multiplexing (TDM)
- Users take turns (round robin)
  - Each one gets entire bandwidth for a little bit of time


### Code Division Multiple Access (CDMA)
- Allowing multiple signals from different users to share the same frequency band all the time
  - Users are separated by unique codes
  - Each bit time is subdivided into shorter intervals called *chips*


### Public Switched Telephone Network (PSTN)
- Structure
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/phone_structure.png)



---

<a name="Lecture3"></a>
## Lecture 3 - The Data Link Layer


---

<a name="Lecture4"></a>
## Lecture 4 - Medium Access Control (MAC) Sublayer


---

<a name="Formulas"></a>
## Formulas
|Name|Formula|Breakdown|Other|
|----|-------|---------|-----------|
|Packet Transmission Delay| L / R | L = Length of Packet (in bits) <br> R = Transmission Rate of Network (in bits/sec)||
|End-to-End Delay (Store & Forward - Packet Switching)| 2L / R |L = Length of Packet (in bits) <br> R = Transmission Rate of Network (in bits/sec)||
|Packet Propagation Delay| d / s | d = Length of physical link <br> s = Propagation speed in medium (~ 2x10^8 m/sec)||
|Packet Queueing Delay| (L * a) / R | L = Packet Length (bits) <br> R = Link Bandwidth (bps) <br> a = Average packet arrival rate | La/R ~ 0 -> Small Average Queueing Delay <br> La/R = 1 -> Average Queueing Delay Increases <br> La/R > 1 -> More work arriving than can be serviced, average delay = infinite!|
|Fundamental Frequency| 1 / T| T = Signal period||
|Fourier Analysis||||
|Max Data Rate (Nyquist)| R = 2B **x** log(base 2) **x** V| R = Max Data Rate (bits/sec) <br> B = Bandwidth (Hz) <br> V = Signal Levels ||
|Max Data Rate (Shannon)| R = B * log(base 2) * (1+ S/N)| R = Max Data Rate (bits/sec) <br> B = Bandwidth (Hz) <br> S/N = Signal to Noise Ratio (decibels dB)||
|Wavelength| Lambda = c / f | c = Speed of light <br> f = frequency ||



---
