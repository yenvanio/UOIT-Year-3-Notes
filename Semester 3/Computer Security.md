# Computer Security


## Table of Contents

[Chapter 1 - Computer Security Overview](#Chapter1)
- [Computer Security Concepts](#1.1)
- [Threats, Attacks and Assets](#1.2)
- [Security Functional Requirements](#1.3)
- [Fundamental Security Design Principles](#1.4)
- [Attack Surfaces and Attack Trees](#1.5)
- [Computer Security Strategy](#1.6)
<br>

---

<a name="Chapter1"></a>

## Chapter 1 - Computer Security Overview
- **NIST**: National Institute of Standards and Technology
  - U.S Federal agency dealing with measurement science, standards and technology.
- **ISOC**: The Internet Society
  - Professional membership society with worldwide organizational and individual membership
- **ITU-T**: The International Telecommunication Union
  - International Organization within the United Nations System
  - Governments and private sector coordinate global telecom networks and services
- **ISO**: The International Organization for Standardization (ISO)
  - Non-Governmental organization that promotes the development of standardization and related activities
  - Facilitating international exchange of goods and services

<a name="1.1"></a>

### Computer Security Concepts
- **Computer Security**: Measures and controls that ensure confidentiality, integrity and availability of information system assets including hardware, software, firmware and information being processed, stored and communicated
- **CIA Triad**
  - **Confidentiality**: Preserving authorized restrictions on information access / disclosure
    - Data confidentiality
    - Privacy
  - **Integrity**: Guarding against improper information modification or destruction
    - Data Integrity
    - System Integrity
  - **Availability**: Assures the system works properly and services is not denied to authorized users
  - Additional 2 properties
    - **Authenticity**: Verifying that users are who they say they are
      - Each input comes from a trusted source
    - **Accountability**: Ability to trace a security breach to a responsible party
      - System must keep records of activity
- **Levels of Impact on Organization and Individuals**
  - **Low**: Limited Adverse Effect
  - **Medium**: Serious Adverse Effect
  - **High**: Catastrophic Adverse Effect
- **Challenges**
  - Attackers only need to find a single weakness, developer needs to eliminate all weaknesses
  - Requires regular and constant monitoring
  - Often thought of as an impediment to an efficient and user-friendly operation
  - Often security is thought to be incorporated into a system after design is complete
  - Potential attacks on security features must be considered
- **Computer Security Model**
  - **Assets**
    - Hardware
    - Software
    - Data
    - Communication facilities and networks
  - **Vulnerabilities, Threats and Attacks**
    - Categories of vulnerabilities
      - **Corrupted**: Loss of Integrity
      - **Leaky**: Loss of Confidentiality
      - **Unavailable**: Loss of Availability
    - Threats
      - Capable of exploiting vulnerabilities
      - Represent potential security harm to an asset
    - Attacks
      - **Passive**: Attempt to make use of information from system, that doesn't affect system resources
      - **Active**
        - Attempt to alter system resources / affect their operation
      - **Insider**
        - Initiated by an entity inside the security parameter
      - **Outsider**
        - Initiated from outside the security perimeter
- **Countermeasures**
  - Means taken to deal with a security attack
  - Devised to prevent a particular type of attack
    - Or... at-least detect the attack and recover from the effects

<a name="1.2"></a>

### Threats, Attacks and Assets
| Threat Type | Threat Consequence | Threat Action (Attack) |
|-------------|--------------------|------------------------|
| <b>Threat to Confidentiality</b> | <b>Unauthorized Disclosure</b> <br> An entity gains access to unauthorized data  | <b>Exposure</b>: Sensitive data directly released to the entity <br> <b>Interception</b>: The entity directly access data traveling between authorized sources and destinations <br> <b>Inference</b>: The entity indirectly accesses data by reasoning from byproducts of communications <br> <b>Intrusion</b>: Entity gains access to data by circumventing a system's security protections
| <b> Threat to System Integrity or Data Integrity </b> | <b> Deception </b> <br> An event that may result in an authorized entity receiving false data | <b> Masquerade </b>: Unauthorized entity poses as an authorized entity <br> <b> Falsification </b>: False data deceives an authorized entity <br> <b>Repudiation</b>: Entity deceives another by falsely denying responsibility for an act
| <b> Threat to Availability or System Integrity </b> | <b> Disruption </b> <br> A circumstance or event interrupting correct operation of system services| <b>Incapacitation</b>: Prevents system operation by disabling a system component <br> <b>Corruption</b>: Alters system operation by modifying system functions or data <br> <b>Obstruction</b>: Threat action that interrupts delivery of system services by hindering system operation
| <b> Threat to System Integrity </b> | <b>Usurpation</b> <br> An unauthorized entity gaining control of system services and functions | <b>Misappropriation</b>: Entity assuming unauthorized logical or physical control of a system resource <br> <b> Misuse </b>: Causes a system component to perform a function or service that is detrimental to system security |

| | <b>Availability</b> | <b>Confidentiality</b> | <b>Integrity</b> |
|-|---------------------|------------------------|------------------|
| Hardware | Equipment is stolen or disabled, thus denying service | An unencrypted CD-ROM or DVD is stolen | |
| Software | Programs are deleted, denying access to users | An unauthorized copy of software is made | A working program is modified causing it to fail during execution or do an unintended task |
| Data | Files are deleted, denying access to users | An unauthorized read od data is performed | Existing files are modified or new files are fabricated |
| Communication Lines <br> and Networks | Messages are destroyed or deleted <br> Communication lines or networks are rendered unavailable | Messages are read, traffic pattern of messages is observed | Messages are modified, delayed, reordered or duplicated |


<a name="1.3"></a>

### Security Functional Requirements
-


<a name="1.4"></a>

### Fundamental Security Design Principles
-


<a name="1.5"></a>

### Attack Surfaces and Attack Trees
-


<a name="1.6"></a>

### Computer Security Strategy
-


---
