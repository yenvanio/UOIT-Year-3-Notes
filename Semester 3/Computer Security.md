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
      - **Passive**
        - Attempt to make use of information from system, that doesn't affect system resources
        - Eavesdropping or monitoring transmissions
        - Two types
          - **Release of Message Contents**
          - **Traffic Analysis**
      - **Active**
        - Attempt to alter system resources / affect their operation
        - Modification of data stream or creation of a false stream of data
        - Four types
          - **Replay**
          - **Masquerade** (Faking to be another entity)
          - **Modification of messages**
          - **Denial of Service**
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
| <b>Hardware</b> | Equipment is stolen or disabled, thus denying service | An unencrypted CD-ROM or DVD is stolen | |
| <b>Software</b> | Programs are deleted, denying access to users | An unauthorized copy of software is made | A working program is modified causing it to fail during execution or do an unintended task |
| <b>Data</b> | Files are deleted, denying access to users | An unauthorized read od data is performed | Existing files are modified or new files are fabricated |
| <b>Communication Lines <br> and Networks</b> | Messages are destroyed or deleted <br> Communication lines or networks are rendered unavailable | Messages are read, traffic pattern of messages is observed | Messages are modified, delayed, reordered or duplicated |


<a name="1.3"></a>

### Security Functional Requirements
- **Access Control**
  - Limit system access to authorized users
- **Awareness & Training**
  - Ensure managers and users are aware of security risks
  - Ensure personnel are trained to carry out information security related duties
- **Audit and Accountability**
  - Maintain information system audit records
  - Ensure actions of individual users can be traced back to them to be held accountable
- **Certification, Accreditation and Security Assessments**
  - Routine assessment of security controls to ensure effectiveness
  - Implement plans of action to correct deficiencies in the system
  - Authorize system operations and connections
  - Monitor system security controls to ensure continued effectiveness
- **Configuration Management**
  - Maintain configurations and inventories of systems throughout development life cycles
  - Enforce security configuration settings for products in the system
- **Contingency Planning**
  - Implement plans for emergency response and post-disaster recovery
  - Ensure availability of critical information during emergency situations
- **Identification & Authentication**
  - Identify users and authenticate those users as a prerequisite to allowing them access
- **Incident Response**
  - Response includes preparation, detection, analysis, recovery and user response activities
  - Track, document and report incidents to officials and authorities
- **Maintenance**
  - Perform regular maintenance on systems
  - Provide effective controls on tools, techniques and personnel used to conduct system maintenance
- **Media Protection**
  - Protect system media (paper & digital)
  - Limit access to system media by authorized users
  - Sanitize / Destroy system medium before disposal or release for reuse
- **Physical & Environmental Protection**
  - Limit physical access to system, equipment and operating environments
  - Protect physical plant and support system infrastructure
  - Provide supporting utilities for systems
  - Protect systems against environmental hazards
  - Provide appropriate environmental controls for systems
- **Planning**
  - Develop, document and update security plans for systems
  - Plans should describe security controls in place for the systems
    - As well as define rules for behavior of users accessing the systems
- **Personnel Security**
  - Ensure individuals occupying positions of responsibility are trustworthy and meet security criteria
  - Ensure information and systems are protected during personnel terminations and transfers
  - Employ formal sanctions for failing to comply with security policies and procedures
- **Risk Assessment**
  - Periodically assess risk to operations, assets and individuals
- **Systems & Services Acquisition**
  - Allocate sufficient resources to protect systems
  - Employ system development life cycle processes incorporating security considerations
  - Employ software usage and installation restrictions
  - Ensure 3rd party providers employ adequate security measures to protect the system
- **System & Communication Protection**
  - Monitor communications at internal and external boundaries of the system
  - Employ architectural designs, software development techniques and systems engineering principles that promote effect security within systems
- **System & Information Integrity**
  - Identify, report and correct system flaws in a timely manner
  - Provide protection from malicious code
  - Monitor system security alerts and take appropriate actions in response


<a name="1.4"></a>

### Fundamental Security Design Principles
- **Economy of Mechanism**
  - Make it simple, not complex
- **Fail Safe Defaults**
  - Access decisions based on permissions instead of exclusions
- **Complete Mediation**
  - Every access must be checked against access control mechanisms
- **Open Design**
  - Design of security system should be open instead of secret
- **Separation of Privilege**
  - Multiple privilege attributes are required to achieve access to restricted resources
- **Least Privilege**
  - Every user should operate with the least set of privileges necessary to perform a task
- **Least Common Mechanism**
  - Design should minimize functions shared by different users
- **Psychological Acceptability**
  - Security mechanisms shouldn't interfere with the work of users
- **Isolation**
  - Public access systems should be isolated from critical resources
  - Prevents disclosure or tampering
- **Encapsulation**
  - Encapsulating a collection of procedures in it's own domain
- **Modularity**
  - Security design should be modular so individual parts can be upgraded without modifying entire system
- **Layering**
  - Use multiple, overlapping protection approaches
- **Least Astonishment**
  - A program should respond in the way that is least likely to astonish the user


<a name="1.5"></a>

### Attack Surfaces and Attack Trees
- **Attack Surface**: Consists of reachable and exploitable vulnerabilities in a system
  - Examples: Open ports on outward facing web servers, Services inside a firewall, SQL / Web Forms
  - **Network Attack Surface**
    - Vulnerabilities over an enterprise network, wide-area network or the Internet
    - Network protocol vulnerabilities, DDOS, disruption of communications
  - **Software Attack Surface**
    - Vulnerabilities in application, utility or OS code
    - Particular focus on web server software
  - **Human Attack Surface**
    - Vulnerabilities created by personnel or outsiders
    - Social engineering / Insider attacks
- *Layering ↑ & Attack Surface ↓ = Low Security Risk*

- **Attack Tree**: Hierarchical data structure representing a set of potential techniques for exploiting security vulnerabilities
  - **Root Node**: Goal of the attack
  - **Sub Nodes**: Ways the attacker can reach the goal, each sub node has sub goals
  - **Leaf Nodes**: Ways to initiate an attack
  - A node that is not a *Leaf Node* is an **AND** node or an **OR** node
    - To achieve the sub goal of an **AND** node, all the sub goals must be achieved
    - To achieve the sub goal of an **OR** node, at least one of the sub goals must be achieved
  - Branches are labelled by cost / difficulty or other attack attributes
    - This allows us to compare different attacks

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/atreeb.png)


<a name="1.6"></a>

### Computer Security Strategy
- **Policy**: Formal statement of rules and practices that regulate how a system provides security services to protect system resources and sensitive data
  - Security Manager needs to consider
    - Value of assets being protected
    - Vulnerabilities of the system
    - Potential threats and likelihood of attacks
  - Must also take the following trade-offs
    - Ease of use vs. Security
    - Cost of security vs. Cost of failure / recovery
- **Implementation**: Security Implementation involves four courses of action
  - **Prevention**: Ideal security scheme is when no attack is successful
  - **Detection**: Absolute protection is not feasible, but practical to detect security attacks
  - **Response**: System response during ongoing attack to halt or prevent further damage
  - **Recovery**: Using backup systems to correctly restore data
- **Assurance & Evaluation**
  - Assurance is the degree of confidence of security measures
  - Evaluation is the process of examining a system with respect to certain criteria
    - Involves testing including formal analytics or math techniques 


---
