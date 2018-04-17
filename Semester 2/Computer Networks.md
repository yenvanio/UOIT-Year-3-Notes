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
[Lecture 7 - Application Layer](#Lecture7)
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


  ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Protocol_Layers.png)

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

    ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Layers_Together.png)


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

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/NetworkOFNetworks.png)
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/NetworkOFNetworks2.png)

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

    ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Fourier_Analysis.png)

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

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Baseband_Transmission.png)

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

    ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Passband_Transmission.png)

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
  - Local Loops
    - Mostly analog twisted pairs going to houses
  - Trunks
    - Digital Fiber Optic links that carry calls between switching offices
  - Switching Offices
    - Where calls are moved from one trunk to another


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/phone_structure.png)


### Local Loop
- **Modems**
  - Modulator Demodulator
  - Types
    - DSL, Cable, Wireless, Telephone
  - Sends data to POTS (Plain Old Telephone Service)

- **Digital Subscriber Lines**
  - Sends data over the local loop to the local office using frequencies that aren't used for POTS


- **Fiber-To-The-Home (FTTH)**
  - Relies on deployment of fiber optic cables
  - One wavelength shared among houses


### Switching
- PSTN uses Circuit Switching
  - Set up, end-to-end path before any data can be sent
- Internet uses Packet Switching

### Cable Television
|Cable|ADSL|
|-----|----|
|**Pros** <br> Uses Coaxial Cable to customers (good bandwidth)| **Pros** <br> Bandwidth is dedicated for each customer <br> Point to Point link does not broadcast data|
|**Cons** <br> Data is broadcast ao all customers (less secure) <br> Bandwidth is shared over customers so may vary| **Cons** <br> Uses twisted pair to customers (lower bandwidth)|


---

<a name="Lecture3"></a>
## Lecture 3 - The Data Link Layer
- Uses physical layer to deliver frames of info over a single link
- Functions   
  - Handles transmission errors
  - Regulates flow of data
  - Provides service to network layer

### Frames
- Link Layer accepts packets from network layer
  - Puts them into frames
  - Sends using physical layer
  - Sends to a layer *physically adjacent* over a link
- MAC addresses used in frame headers to identify source and destination

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Data_Link_1.png)

### Services Provided to Network Layer
- Provides services to the layer above (Network Layer)


- **Unacknowledged Connectionless Service**
  - Frame is sent with no logical connection
    - No ACK or error recovery


- **Acknowledged Connectionless Service**
  - Frame is sent with no connection but with retransmissions if needed
    - Each frame sent is individually acknowledged by the receiver


- **Acknowledged Connection-Oriented Service**
  - Connection is set up first
    - Has 3 Phases
  - 1. Connection is established by having both sides initialize buffers and counters to keep track of the received frames
  - 2. Frames are transmitted and ACK by the receiver
  - 3. Releasing the connection, freeing up the resources


### Putting bits into Frames
- Byte Count
- Byte Stuffing
- Bit Stuffing

#### Byte Count
- Header has a field to put the number of bytes in it
  - Simple, but difficult to re-sync if an error occurs

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Byte_Count.png)


#### Byte Stuffing
- Special flag bytes delimit frames
  - Used as starting and ending delimiter
  - 2 consecutive flag bytes = end of one, start of another
- When the Flag shows up in the data, need to escape it
  - Can escape it by doubling up with the flag
- Longer process, but can be re-synced easier after error occurs

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Byte_Stuffing.png)


#### Bit Stuffing
- Stuffing done at the bit level
  - On Transmit: After five consecutive 1's in the data, a 0 is added
  - On Receive: A 0 after five consecutive 1's is deleted


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Bit_Stuffing.png)


### Error Control
- Repairs frames that are received in error
- Receiver sends an ACK for every packet that is received correctly
  - ACK = Acknowledgement packet sent by host in response to packet it received
- Timer protects against lost ACKs
  - Timeout signal occurs when an ACK has not been received for a sent packet within a certain timeframe
  - Timeout triggers retransmission of original packet


### Flow Control
- Prevents a fast sender from outpacing a slow receiver
-	Receiver gives the feedback to the sender on the data it can accept

### Error Detection and Correction
- Error codes add
  - Structured Redundancy to data
  - Allows errors to be detected or corrected


- **Error Correction Codes**
  - Hamming Codes
  - Binary Convolutional Codes
  - Reed-Solomon and Low-Density Parity Check codes


- **Error Detection Codes**
  - Parity
  - Checksums
  - Cyclic Redundancy Codes


#### Parity (Error Detection)
- Depending on if Even or Odd Parity is set
  - If EVEN when sending the number of 1s must be even
    - When received if the number of 1s is not even then there is an error
  - If ODD when sending the number of 1s must be odd
    - When received if the number of 1s is not odd then there is an error
- Some problems with parity check
  - If two bits are altered then can still come through as the correct parity with errors
  - If the parity bit is altered then it will still come through as correct


#### Checksums (Error Detection)
- Basically add up the message, and 1's complement it
  - This value is the internet checksum
- When passed to receiver if the sum after being 1's complemented is 0000 then no errors

```
Example

Message: 1001 1100 1010 0011
Sum (Start from Right End):
1. 0011 + 1010 = 1101
2. 1101 + 1100 = 1001 + 1 = 1010
3. 1010 + 1001 = 0011 + 1 = 0100

Internet checksum will be the 1's complement of the sum
Internet checksum = 1011

Message will be sent as: 1001 1100 1010 *1011*

Message will be received and summed again
0100 + 1011 = 1111
1's complimenting that will give us 0000 (a.k.a Error Free Data)


```

#### Cyclic Redundancy Check - CRC (Error Detection)
- Given Message, Divide it by generator polynomial
- Put remainder at end of message and send it
- When received, divide message by generator polynomial
  - If remainder = 0 then no error


### Error Control
- Acknowledgements and Timeouts
- Propagation Delay
  - Delay between transmission and receipt of packets b/w hosts
  - Can be used to estimate timeout period
- Timeout = AT LEAST twice the propagation delay  + processing time at the receiver and transmission of an ACK
  - Use (EWMA) Exponentially weighted moving average of the (RTT) Round Trip Time
  - Set Timeout = 2 x EWMA

### Automatic Repeat reQuest (ARQ)
- Sender waits for a positive ACK before moving onto next data item
- a.k.a Positive Acknowledgement with Retransmission (PAR)
  - Stop & Wait for Error Free Channel
  - Stop & Wait for Noisy Channel

#### Stop & Wait for Error Free Channel
- Protocol ensures sender can't outpace receiver
  - Sender waits for ACK after passing frame to physical layer
  - Receiver sends ACK after passing frame to network layer


#### Stop & Wait for Noisy Channel
- ARQ adds error control
  - Receiver acknowledges frames that are delivered correctly
  - Sender sets timer and resends frame if no ACK and the a timeout occurs
- Need to number ACKs
  - So receiver knows its retransmission


### Sliding Window Concept
- Allows for multiple un-ACK'd frames
  - Upper Bound = Window


- **Sender**
  - Assign SeqNum to each frame
  - 3 State Variables
    - SWS = Send Window Size (Upper Bound of outstanding frames)
    - LAR = Last Acknowledgement Receiver (Sequence Number of the last ACK received)
    - LFS = Last Frame Sent (Sequence Number of the last frame sent)
  - Process
    - Advance LAR when ACK arrives
    - Associate timer with each frame the sender transmits
    - Sender retransmits the frame if timer runs out
    - Buffer up to SWS frames
  - LFS - LAR <= SFS


- **Receiver**
  - 3 State Variables
    - RWS = Receive Window Size (Upper Bound of out-of-order frames the receiver will take)
    - LFA = Largest Frame Acceptable (Sequence Number of the largest acceptable frame)
    - LFR = Last Frame Received (Sequence number of last frame received and ACK'd)
  - Process
    - When Frame w/ SeqNum arrives
      - If LFR < SeqNum <= LFA, then ACCEPT
      - If SeqNum <= LFR or SeqNum > LFA, then DISCARD
  - LFA = LFR = RWS


- How to prevent sender overflowing receiver's buffer
  - Receiver tells sender its buffer size during connection setup


- How can we insure reliability in pipelined transmissions
  - **Go Back N**
    - Send all N un-ACK'd packets when a loss is signaled
    - Inefficient
  - **Selective Repeat**
    - Only send specifically un-ACK'd packets
    - Trickier to implement

---

<a name="Lecture4"></a>
## Lecture 4 - Medium Access Control (MAC) Sublayer
- Responsible for deciding who sends next on a multi-access link

### Multiple Access Protocol
- **Interference**: Two or more simultaneous transmissions by nodes
- **Collision**: If a node receives two or more signals at the same time
- **Multiple Access** Protocol: Determines how nodes share the channel
  - Determines when a node can transmit

### MAC Protocols: Taxonomy
- Channel Partitioning (Static)
- Random Access (Dynamic)
- "Taking Turns" (Predefined Order)

#### Static Channel Allocation
- **TDMA**: Time Division Multiple Access
  - Access to channel happens in rounds
  - Each station gets fixed length


- **FDMA**: Frequency Division Multiple Access
  - Channel is divided into frequency bands
  - Each station assigned fixed frequency band

#### Dynamic Channel Allocation
- Gives channel to a user when they need it
- Schemes vary with assumptions
- When node has packet to send
  - Transmit at full channel data rate (R)
  - No coordination among nodes
- Two or more transmitting nodes = collision

|Assumption|Implication|
|----------|-----------|
|Independent Traffic|Assume Poisson packet arrival rate from N users Often not a good model, but permits analysis|
| Single Channel| Only one channel available for all users No external way to coordinate the senders|
|Observable Collisions|All nodes sense the collision when it happens Needed for reliability; mechanisms vary|
| Continuous or slotted time|Slotting may improve performance since a frame can only be sent at the start of the slot|
|Carrier Sense|Stations can sense the channel if busy or not. If busy they should not use the channel Can improve performance|

- Random Access MAC Protocol specifies
  - How to detect collisions
  - How to recover from collisions
- MAC Protocols
  - ALOHA  (Pure / Slotted)
  - CSMA (Carrier Sense Multiple Access)
  - Collision Free Protocols
  - Limited Contention Protocols
  - Wireless LAN Protocols


### Pure ALOHA
- User transmits frames whenever they have data
- Retry after random time if there was a collision
- Collisions happen when
  - Users transmit during a vulnerable period
    - Vulnerable period is when a frame is sent in between the start of one frame and end of another frame
    - Collides with both

### Slotted ALOHA
- Twice as efficient as Pure ALOHA
- Assumes
  - All frames have same size
  - Time divided into equal size slots
  - Nodes start to transmit only at slot beginning
  - Nodes are synced
  - If 2 or more nodes transmit in the same slot, all nodes detect collision
- Process
  - When node obtains frame, it transmits it in the next slot
  - If no collision, send new frame in next slot
  - If collision, node retransmits in each subsequent slot until successful
    - Probability p of success with each subsequent slot

### Carrier Sense Multiple Access Protocols
- Improves ALOHA by sensing the channel
- Listens before transmitting
  - If it senses channel as idle, transmit frame
  - If it senses channel as busy, defer transmission
- Collisions can still occur
  - Due to propagation delay, two nodes may not hear each other's transmissions
- When a collision occurs
  - Transmitter sends a jam signal to let the receiver and other stations to know that there was a collision
- 3 actions to choose from when a channel is busy
  - 1-Persistent (Greedy)
    - Sends as soon as idle (probability 1)
  - P-Persistent (Probability)
    - Sends with probability p when idle
  - NonPersistent
    - Wait a random time then sense again

### Collision Free Protocols
- Token sent around a ring defines sending order
- Station with token can send frame before passing token

### Classic Ethernet - Physical Layer
- One shared coaxial cable that all hosts attach to
- Topology
  - Bus
    - All nodes in same collision domain
  - Star
    - Nodes do not collide with each other
    - Active switch in center

### Classic Ethernet - MAC Sublayer
- MAC Protocol is 1-Persistent
- Channel is divided into time slots (twice the propagational delay)
- Binary Exponential Backoff (BEB): Backoff a random number between 0 and 2^i - 1
  - i = attempt number (1-10)
- **Random Delay**
  - Backoff after collision is computed with Binary Exponential Backoff (BEB)
- **Connectionless**
  - No handshaking between sending/receiving NICs
- **Unreliable**
  - Receiving NIC doesn't send ACKs to sender

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Backoff.png)


- Frame format
  - Preamble
    - 7 bytes, used to synchronize receiver / sender clock rates
  - Addresses
    - 6 byte source / destination MAC addresses
  - Type  
    - Indicates higher layer protocol (IPv4, IPv6)
- If error is detected (FCS / CRC), frame is dropped

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Ethernet_Frame.png)


- Collisions can occur and take as long as 2(Propagational Delay)
  - Minimum packet size of data must be >= 46 for reliable detection
  - Min Frame size = 46 + 18 = 64 bytes (excluding Preamble)
  - All frames must take 2*PDelay, So the transmission is still happening when the noise burst gets back to the sender

### Fast Ethernet / Switched Ethernet
- Hubs wire all lines into a single CSMA collision domain
- Switches isolate each port into separate collision domains

### Wireless LANs
- Nodes have different coverage regions
- Nodes cannot detect collisions while sending
  - Because the received signal is weaker than transmitted one

#### Hidden Terminals
- Senders that cannot sense each other but collide at the intended receiver
- A & B are hidden terminals when sending to C

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Hidden_Terminal.png)

#### Exposed Terminals
- Senders who can sense each other but still transmit safely to different receivers
- Exposed Terminals are  
  - B sending to A;
  - C sending to D;

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Exposed_Terminal.png)

### Architecture / Protocol Stack
- Wireless clients associate to a wired Access Point (AP)
  - Called **Infrastructure Mode**
  - Client only sends / receives packets via the AP
- Sever AP's connected = **Distribution System** (DS)
- **SSID**
  - Unique
  - Case Sensitive
  - Alphanumeric value
  - 2-32 characters in length
  - Network Name
- Client must be configured for correct SSID to join network

### 802.11 MAC
- Algorithm = DFWMAC (Distributed Foundation Wireless MAC)
- 2 Algos
  - Distributed Access Protocols (Distributed Coordination Function **DCF**)
  - Centralized Access Protocols (Point Coordination Function **PCF**)
- Uses **CSMA/CA**
  - CA = Collision Avoidance (similar to Collision Detection)
  - Inserts backoff slots to avoid collisions
- **Process**
  - Stats sensing channel
  - If free during IFS (Inter Frame Space)
    - Send
  - If busy, wait for free IFS
    - Wait a random back-off time
  - If another station occupies medium during back-off time
    - Backoff timer stops
  - If transmission failed
    - Assume collision occurred


- **SIFS (Short IFS)**
  - Used for immediate response actions
- **DIFS (Distributed Coordination Function IFS)**
  - Used for all ordinary async traffic

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/CSMA_CA.png)

### Data Link Layer Switching
- Uses of Bridges
- Learning Bridges
- Spanning Tree
- Repeaters, Hubs, Bridges....Routers, Gateways
- Virtual LANs

### Uses of Bridges
- TO Join multiple physical LANs into a single logical LAN
- TO Divide one physical LAN into multiple logical LANs called VLANs (Virtual LANs)

#### Ethernet Switch (Bridge)
- Link-Layer Device
  - Store, Forward Ethernet frames
- Transparent
  - Hosts are unaware of the presence of switches
- Plug-And-Play
  - Switches do not need to be configured
- 2 Algos to make Bridges Transparent
  - Backward Learning Algorithm
    - Stop traffic being sent where not needed
  - Spanning Tree Algorithm
    - Break loops that can form when switches are cabled together

### Learning Bridges
- Operates as a switched LAN
- Switch allows multiple simultaneous transmissions
  - Each link is its own collision domain


- **Switch Forwarding Table (MAC Table)**
  - Switch learns which hosts can be reached through which interfaces

  ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/MAC_Table.png)

- **Backward Learning Algorithm**
  - Picks the output port
  - When frame received at the switch
    - 1. Record incoming link, MAC address of sending host
    - 2. Index switch table using MAC Destination Address
    - 3. If entry found for destination
      - If Destination on same segment, DROP
      - Else forward frame onto interface indicated by entry

### Spanning Tree Problem
- Each bridge periodically broadcasts a config message
  - Called **Bridge Protocol Data Unit (BPDU)**
  - Includes info about selected root bridge and distance of other bridges to root
- Bridges choose on to be the root of the Spanning Tree
  - The one with smallest MAC address is chosen
- Shortest path from root to every bridge is constructed
- Bridges turn off ports that are not part of shortest path

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/MST.png)

### Virtual LANs
- Splits one physical LAN into multiple logical LANs
  - Eases management tasks
  - Ports are colored according to their VLAN
- Switches that support VLAN can be configured to define multiple VLANs over a single physical LAN


- **Port Based VLAN**: Switch ports grouped so that single switch operates as multiple virtual switches
  - Traffic Isolation
    - Frames to/from ports 1-8 only
  - Dynamic Membership
    - Ports can be dynamically assigned among VLANs
  - Forwarding b/w VLANs
    - Done via routing

- **Trunk Port**: Carries frames between VLANs defined over multiple physical switches


---

<a name="Lecture6"></a>
## Lecture 6 - Transport Layer
- Sends data across networks
  - **Sender**: breaks app messages into segments and passes to network
  - **Receiver**: reassembles segments into messages passes to app layer
- Two protocols
  - **TCP**
  - **UDP**
- **Network Layer**: Communication betweens hosts
- **Transport Layer**: Communication between processes (within host)
  - Adds reliability to network layer

### Process of Transporting Elements
- **Addressing**
  - adds TSAPs (Transport Service Access Points)
    - Multiple clients and servers can run on a host with a single network (IP) address
    - TSAPs are ports for TCP/UDP
  - Hosts receives IP datagrams
    - Each datagram has source/destination IP addresses
    - Each datagram carries one transport layer segment
    - Each segment has source/destination port numbers
  - Uses IP address and Port Numbers of host to send to IP address and Port number of destination





---



<a name="Lecture7"></a>
## Lecture 7 - Application Layer
- Cannot write software for network-core devices
  - Because they work on Network layer and below
- Need to write software that will run on multiple *end systems* and communicate over networks
  - Can use C, Java, Python

### Network Application Architecture
- Designed by application developer
- Defines application structure over various end systems
- 2 Architectural paradigms
  - Client Server Architecture
  - Peer to Peer Architecture

#### Client-Server Architecture
- **Server**
  - Always-on
  - Permanent IP Address
  - Data Centers are used for scaling
- **Client**
  - ONLY communicates with server, not each other
  - May have dynamic IP Address
  - May be intermittently connected

#### P2P Architecture
- Little to no reliance on dedicated servers
- Services are
  - Requested from peers
  - Provided to peers
- Self scaling
  - New peers bring new capacity along with demands
- Issues with P2P
  - Complex to manage
  - Security Issues

### Processes Communicating
- **Process**: Program running within a host
- **Inter-process Communication**: Two processes of the same host communicating
  - Processes from different hosts communicate by exchanging messages
- **Client Process**: Process that initiates the communication
- **Server Process***: Process that waits to be communicated with

### Sockets
- The interface between the process and the computer network through which processes communicate
- Messages are sent/received to/from sockets
- Sending process relies on the other side to deliver the message to the socket at the receiving process
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/socketZ.png)
- Receiving processes are identified by the following
  - IP Address (host address)
  - Port Number (destination host identifier)
- Socket Number is a combo of the above two

### Transport Services
- An application needs the following transport services
  - **Reliable Data Transfer**
    - Some require 100% reliable transfer (File transfer)
    - Some can tolerate loss to an extent (Audio)
  - **Timing**
    - Some require low delay to be effective (Games)
  - **Throughput**
    - Require a minimum amount of throughput (Multimedia)
    - Others make use of whatever they get (Mail, File Transfer)
    - *Throughput: The amount of items passing through a system*
  - **Security**
    - Encryption, Data Integrity

### Transport Services Provided by the Internet
- **TCP**
  - Provides
    - Reliable Transport
    - Flow Control
    - Congestion Control
    - Connection Oriented
  - Does NOT Provide
    - Timing
    - Minimum Throughput  
    - Security

- **UDP**
  - Provides
    - Unreliable Data Transfer
  - Does NOT Provide
    - Reliability
    - Flow Control
    - Congestion Control
    - Timing
    - Minimum Throughput
    - Security
    - Connection Setup

- **So WHY is there even a UDP?**
  - Because it does not take into consideration any of these extra factors that ensure security, it allows computers to communicate much faster. It is up to the receiving user to ensure all packets are received correctly because if you miss it, too bad and no guarantee you're gonna get all of them either.

- **How do you secure these Transport Services?**
  - TCP and UDP do not provide any encryption or security
  - **SSL** Security Sockets Layer, adds security enhancement to TCP and it is developed at the application layer
  - SSL provides data integrity, encryption, authentication

### Application Layer Protocols
- Defines how processes of an application pass messages to each other
  - Processes are running on different end systems
- **Type of Message**
  - Request, Response
- **Message Syntax**
  - What fields and how the fields are delineated (separated)
- **Message Semantics**
  - Meaning of information in the fields
- **Rules**
  - When & How processes respond to messages
- **Note*:**
  - Some protocols are *open*
    - Allows for interoperability (exchange info b/w systems)
    - HTTP, SMTP
  - Some protocols are *proprietary*
    - Skype

### Web & HTTP
- **Web**: An application that revolutionized the internet
  - Works by demand
  - Uses get what they want, when they want it
  - Any user can become a publisher at a low cost

#### HTTP Overview
- Web Page consists of **objects** (files)
  - Objects can be: HTML File, JPEG, Audio File, Java Applet
  - Objects are addressable by a single URL that is made up of
    - Host Name
    - Object Path Name
  - `http://www.somesite.com/someFolder/somePic.png`
- **HTTP**: Hypertext Transfer Protocol
  - The application layer for the Web
  - Defines how clients request web pages
  - Defines how servers transfer web pages to clients
  - *Client Server Model* (HTTP Protocol)
    - Client = Browser that requests/receives and displays web objects
    - Server = Web server that responds to requests by sending objects
- Web uses HTTP Protocol but **HTTP used TCP Protocol**
  - Client initiates TCP connection (creates a socket to the server **Port 80**)
  - Server accepts TCP connection
  - HTTP messages are exchanged between browser and server
    - HTTP messages = application-layer protocol messages
- **HTTP is a stateless protocol**
  - Maintains no info about past client requests

### HTTP Connections
- **Non Persistent HTTP**
  - One object sent over TCP connection at a time
  - For multiple must close connection and open a new one
  - **Issues**
    - Requires 2 RoundTripTime's per object
    - OS overhead for each connection
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/nPers.png)

- **Persistent HTTP**
  - Multiple objects can be sent over a single TCP connection
  - Connection stays open so client sends requests as soon it encounters a referenced object
  - As little as 1 RoundTripTime for all referenced object

### HTTP Message Format
- **Request Message**
  - ASCII format human-readable)
  - General Format Below
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/htptreq.png)
  - Two ways to upload form inputs
    - `POST`: Form input uploaded to server
    - `URL`: www.somesite.come/animalsearch<b>?monkeys&banana</b>
  - Other request methods are below  

|Method|Description|
|------|-----------|
|GET|Fetch a web page|
|HEAD|Read a web page's header|
|POST|Send input data to a server program|
|PUT|Uploads file in entity body to path specified in URL field|
|DELETE|Deletes file specified in URL field|
|TRACE|Echo the incoming request |
|CONNECT|Connect through a proxy|
|OPTIONS|Query options for a page|

- **Response Message**
  - General Format Below
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/htptres.png)
  - Status Codes

|Code|Description|
|------|---------|
|200 OK|Request succeeded, object is later in this message|
|301 Moved Permanently|Requested object moved, new location is laster in this message|
|400 Bad Request|Request message not understood by server|
|404 Not Found|Requested document not found on this server|
|505 HTTP Version Not Supported|HTTP Version is not supported|

### Cookies
- HTTP is stateless but some web sites want to save information about users to identify them
  - HTTP uses **Cookies** for this
- 4 Components of Cookies
  - Header in the HTTP Response Message
  - Header in the HTTP Request Message
  - Cookie file kept on the user's end system and managed by their browser
  - Back end Database at the web site
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/coooK.png)

- **Cookies can be used for**
  - Authorization
  - Shopping Carts
  - Recommendations
  - User Session State (Web Email)

- **Maintaining state**
  - Protocol endpoints maintain state over transactions
  - Cookies are HTTP messages carrying state

- **Cookies and Privacy**
  - Cookies allows sites to learn about you
  - May supply: name, email, cc to sites

### Web Caching
- A network entity that satisfies HTTP requests on behalf of the web server
- User browser initiates TCP connection to the **Web Cache**
  - If cache has object it returns it
  - If not it gets the object from the server
    - Saves it in cache and sends to user
- Cache is a client and server
  - Client b/c requests from server
  - Server b/c responds to client browser
- Benefits
  - Reduces response time
  - Reduces traffic

- Sample Problem
  - Access Delay too high
  - A solution can be to increase access link rate but that would be expensive ($$)
  - Web cache is a cost effective solution

- Conditional `GET`
  - `GET` message and `If-modified-since: <date>`
  - Checks to see if modified from last cached date, otherwise return from cache
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/caches.png)


### eMail
- **User Agents**
  - Mail reader (Gmail, Apple, Outlook)
  - Lets you manage your mail (read, reply, save, compose)
- **Mail Servers**
  - Mailbox to hold incoming messages
  - Message queue of outgoing mail messages
- **SMTP (Simple Mail Transfer Protocol)**
  - Protocol to send email between mail servers
- **Process**
  - PersonA sends mail using *User Agent* to the *Mail Server*. It's placed in the *Mail Server's* outgoing queue. PersonA's mail server uses SMTP to deliver the message to PersonB's mail server. PersonB's *User Agent* retrieves the mail from their *Mail Server*.
  - If PersonA mail fails to send, will hold in queue and retry every 30mins or so and after a number of failed attempts, sends mail to personA saying failed.
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/proSez.png)

```
Example Transcript
Client Name: crepes.fr
Server Name: hamburger.edu

S: 220 hamburger.edu
C: HELO crepes.fr
S: 250 Hello crepes.fr, pleased to meet you
C: MAIL FROM: <alice@crepes.fr>
S: 250 alice@crepes.fr ... Sender ok
C: RCPT TO: <bob@hamburger.edu>
S: 250 bob@hamburger.edu ... Recipient ok
C: DATA
S: 354 Enter mail, end with “.” on a line by itself
C: Do you like ketchup?
C: How about pickles?
C: .
S: 250 Message accepted for delivery
C: QUIT
S: 221 hamburger.edu closing connection

```

### SMTP
- Uses **TCP** to transfer email messages from client to server (Port 25)
- Direct transfer: Sending server to receiving server
- Three phases
  - **Handshaking**
  - **Transfer of messages**
  - **Closure**
- Command/Response interactions
  - Commands are ASCII text
  - Responses are Status Codes + Phrases
- Uses persistent connections
- Requires header and body to be in 7-but ASCII
- Uses CRLF to determine end of message

- **HTTP vs SMTP**
|--|HTTP|SMTP|
|--|----|----|
|<b>Protocol Type</b>| Pull | Push |
|<b>Command/Response Interaction</b>| ASCII | ASCII |
|<b>Command/Response Interaction</b>| ASCII | ASCII |
|<b>Objects</b>| Each object encapsulated in its own response | Multiple objects sent into one message |


### Mail Message Format
- RFC 822: Standard for text message format
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mmmF.png)

### Mail Access Protocols
- SMTP is only used to push mail from sender agent to mail server
  - AND from mail server to other mail server
- Need mail access protocol to retrieve the mail from recipient mail server
- 3 protocols
  - **POP**
  - **IMAP**
  - **HTTP**: gmail, hotmail, yahoo

#### POP3 Protocol
- Begins when client opens TCP connection to mail server (Port 110)
- 3 Phases
  - **Authorization**
    - Authenticates users by username, password
    - Responds with +OK or -ERR
  - **Transaction**
    - User can
      - List message numbers
      - Retrieve messages
      - Delete messages
      - Quit  
  - **Update**
    - Occurs after quit command
    - Mail server deletes message that were marked for deletion in this stage
- 2 Modes
  - **Download-and-Delete**:
    - Server deletes messages after being downloaded
    - Client cant re-read messages if he changes the client machine
  - **Download-and-Keep**:
    - User agent leaves messages on server after downloading
    - Client can be read from different machines
- **POP3 is stateless across sessions**
- Problem: No way to create remote folders and assign messages to folders
  - Use IMAP for this

### IMAP (Internet Mail Access Protocol)
- Keeps all messages in one place @ the server
- Allows users to create folders and organize messages in folders
- Keeps user state across sessions
  - Names of folders and mappings between message IDs and folder name

### Web Based E-mail
- Protocol works in 2 modes
- Many users send and access email through browsers
  - User agent is now the browser that communicates with its remote mailbox via HTTP
  - Now the email is sent from mail server using HTTP vs POP3 and IMAP
  - Sender also sends email over HTTP vs SMTP too
- Mail servers still talk to each other using SMTP though  
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/baba.png)

### Domain Name System
- How to map between IP address and name
  - Domain Name System
- **Distributed Database**: implemented in hierarchy of many DNS servers
- **Application Layer Protocol**: Allows hosts and DNS servers to communicate to resolve the names (address/name translation)
- DNS protocol runs over UDP and on Port 53
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/DNSS.png)

- Services by DNS
  - Hostname to IP address translation
  - Host aliasing
    - rela1.west-cost-.enterprise.com could have two aliases : enterprise.com vs www.enterprise.com
    - DNS translates from simple aliases to canonical names and its IP address
  - Mail server aliasing
    - Translate from simple alias mail server names to its canonical name and its IP address
  - Load distribution
    - Many IP addresses correspond to one server name
    - DNS responds with the full set of IP addresses but rotates the ordering of the addresses within each reply

#### DNS - Distributed and Hierarchical Database
- **Root DNS Servers**
  - 400 root name servers managed by 13 different organizations
  - Provide IP addresses of the TLD servers
- **Top-Level Domain (TLD) DNS Servers**
  - Responsible for com, org, net etc
  - TLD servers provide IP addresses for authoritative DNS servers
- **Authoritative DNS Servers**
  - Organization's own DNS server(s) providing authoritative hostname to IP mappings for organizations names hosts
  - Can be maintained by organization or hosted by a Service Provider
- **Local DNS Name Server**
  - Does not belong to hierarchy
  - Each ISP has one
  - When hosts make DNS queries its sent to DNS server that acts as a proxy
    - It has a cache (can be out of date )
    - May forward to hierarchy

- If client wants the IP address of a website  (amazon.com)
  - Client queries one of the root servers to find the .com servers
  - Client queries one of the .com DNS servers to get amazon.com
  - Client queries amazon.com DNS server to get IP address for www.amazon.com
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/higherArc.png)
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/welp.png)

### DNS - Caching
- Once a server learns IP mapping it caches the mapping
- Cache entries disappear after TTL = 2 days
- TLD servers are also cached so root name servers are rarely visited
  - If a name host changes IP address wont know until all entries disappear

#### DNS - Records
- DNS is a distributed database that stores resource records (RR)
  - Stored in this format: (Name, Value, Type, TTL)
  - Name & Value depend on Type
    - type=A: Name is hostname and value is IP address
    - type=NS: Name is domain and value is hostname
    - type=CNAME: Name is alias, value is canonical name  
    - type=MX: Name is canonical name of mail server, value is hostname

#### DNS - Messages
- Query & Reply messages both have the same message format
- `nslookup` can be used to query a DNS server on Windows
- Identification
  - 16 bit number of query, and for reply
- Flags
  - Query(0) or Reply(1)

#### DNS - Inserting Records into DNS Database
- Need to register DNS
- Provide names and IP addresses
- Registrar inserts two RR's (NS & A typed)
- Need type A for web server
- Need type MX for mail server
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/bumdum.png)
- Example
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/welp2.png)

#### DNS - Vulnerabilities
- Attacks
  - DDoS
    - Bombards root servers with traffic
  - Redirect
    - Man in Middle to intercept query and reply with bogus
  - Exploit DNS for DDoS
    - Send queries with spoofed source address : targetIP





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
|Max Data Rate (Shannon)| R = B * log(base 2) * (1+ S/N)| R = Max Data Rate (bits/sec) <br> B = Bandwidth (Hz) <br> S/N is calculated by using SNR below||
|Signal to Noise Ratio (SNR)| SNR = 10 log10(S/N) | SNR = Signal to Noise Ration |
|Wavelength| Lambda = c / f | c = Speed of light <br> f = frequency ||



---
