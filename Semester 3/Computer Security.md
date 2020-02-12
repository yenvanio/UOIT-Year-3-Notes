initializedreceiver# Computer Security


## Table of Contents

[Chapter 1 - Computer Security Overview](#Chapter1)
- [Computer Security Concepts](#1.1)
- [Threats, Attacks and Assets](#1.2)
- [Security Functional Requirements](#1.3)
- [Fundamental Security Design Principles](#1.4)
- [Attack Surfaces and Attack Trees](#1.5)
- [Computer Security Strategy](#1.6)

<br>

[Chapter 2 - Cryptographic Tools](#Chapter2)
- [Symmetric Encryption](#2.1)
- [Message Authentication & Hash Functions](#2.2)
- [Public Key Encryption](#2.3)
- [Digital Signature & Management](#2.4)
- [Random & Pseudorandom Numbers](#2.5)
- [Practical Application : Encryption of Stored Data](#2.6)

<br>

[Chapter 3 - User Authentication](#Chapter3)
- [Electronic User Authentication Principles](#3.1)
- [Password Based Authentication](#3.2)
- [Token Based Authentication](#3.3)
- [Biometric Authentication](#3.4)
- [Remote User Authentication](#3.5)
- [Security Issues](#3.6)

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

<a name="Chapter2"></a>

## Chapter 2 - Cryptographic Tools
- **Cryptography**
  - Classified in 3 dimensions
    - Type of operations to transform plaintext to cipher-text
      - **Substitution**: Every element in plaintext is mapped to another element
      - **Transposition**: Elements in plaintext are rearranged
    - Number of keys used
      - **Symmetric**: Sender and receiver use the same keys
      - **Asymmetric**: Sender and receiver use different keys
    - How the plaintext is processed
      - **Block Cipher**: Processes input one block of elements at a time
      - **Stream Cipher**: Processes input elements continuously
  - Encryption is computationally secure if
    - Cost of breaking cipher > value of information  
    - Time needed to break cipher > useful lifetime of the information
- **Cryptanalysis**: Process of attempting to discover the plaintext or key

<a name="2.1"></a>

### Symmetric Encryption
- Universal technique for providing confidentiality for data
  - Single Key Encryption
- Two Requirements
  - Need a strong encryption algorithm
  - Sender / Receiver must have obtained the secret key securely and keep it secure
- 5 Step Process
  - Plaintext Input
  - Encryption Algorithm + Secret Key
  - Transmitting Cipher-text
  - Decryption Algorithm + Secret Key
  - Plaintext Output
- 2 Approaches to attacking a symmetric encryption scheme
  - **Cryptanalytic Attacks**
    - Relies on
      - Nature of Algorithm
      - Knowledge of general characteristics of the plaintext
      - Some sample plaintext-ciphertext pairs
    - Exploits algorithm to deduce a specific plaintext or the key being used
      - If successful, all messages encrypted with that key are compromised
  - **Brute Force Attack**
    - Try all possible keys until a proper translation into plaintext is found
    - On average, half of all possible keys must be tried to succeed

#### Symmetric Block Encryption Algorithms
- **DES**: Data Encryption Standard
  - Most widely used encryption scheme
  - Uses 64-bit plaintext block and 56-bit key to produce a 64-bit cipher-text block
  - Cons
    - Concerns about the algorithm itself
    - Concerns about using a 56-bit key
- **Triple DES**
  - Repeats DES using 3 unique keys
  - `(C) = E(K3, D(K2, E(K1, P)))`
    - Cipher Text = Encryption of (Decryption of (Encryption of P using K1) using K2) using K3
  - `(P) = D(K1, E(K2, D(K3, C)))`
    - Plain Text = Decryption of (Encryption of (Decryption of C using K3) using K2) using K1
  - Pros
    - 168-bit key length overcomes brute-force attack vulnerability of DES
    - Underlying encryption is same as DES
  - Cons
    - Algorithm is sluggish in software
    - Uses 64-bit block size, larger block size would be better
- **AES**: Advanced Encryption Standard
  - Substitute Bytes
    - S-Box
    - Performs a byte-by-byte substitution of the block
  - Shift Rows
    - *Encryption*: Shift each row to the left by `n` bytes, starting at 0
    ```
    87 | F2 | 4D | 97       =>    87 | F2 | 4D | 97     [ Moved 0 bytes ]
    EC | 6E | 4C | 90       =>    6E | 4C | 90 | EC     [ Moved 1 byte ]
    ```
    - *Decryption*: Shift each row to the right by `n` bytes, starting at 0
  - Mix Columns
    - Operate on each column individually
    - Map each byte to a new value that is a function of all 4 bytes in the column
  - Add Round Key
    - Bitwise XOR of current block with a portion of the key
- **Security Issues**
  - Symmetric usually used for larger data ( > 128-bit block)
  - Each block encrypted using same key

#### Block Cyphers
- Processes input one block of elements at a time
- Can reuse keys
- **ECB**: Electronic Codebook
  - Simplest mode
  - `b` bits a time and each block encrypted using same key
  - Called `codebook` because each b-bit block has unique cipher-text output
    - Security issue cause repeated plaintext can be seen in repeated cipher-text
- **Stream Cyphers**
  - Process input continuously
    - Produces one output element at a time
  - Faster, use less code
  - Uses **RC4** to generate a pseudo-random stream of bits (a key-stream)

#### Block Cipher Modes of Operation
|Mode|Description|Typical Application|
|----|-----------|-------------------|
|<b> Electronic Codebook (ECB) </b>|Input is processed a block at a time, each block encoded using the same key| Secure transmission of single values (an encryption key)|
|<b> Cipher Block Chaining (CBC) </b>|Input to encryption is XOR of next 64 bits of plaintext and previous 64 bits of cipher-text|Block Oriented Transmission, Authentication|
|<b> Cipher Feedback (CFB) </b>|Input processed <code>s</code> bits at a time. Previous cipher-text used to produce pseudorandom output which is XOR'd with the plaintext input to produce cipher-text|Stream Oriented Transmission, Authentication|
|<b> Output Feedback (OFB) </b>|Same as CFB, but input is the DES output| Stream Oriented Transmission over noisy channels (Satellite Communication)|
|<b> Counter (CTR) </b>|Each plaintext block is XOR'd with an encrypted counter, counter is incremented for each block|Block Oriented Transmission, High speed requirements|

#### Key Distribution
- How to deliver a key to `A` and `B` without allowing others to see the key
  - Selected by `A`, physically delivered to `B`
  - Third party selects key and delivers to both parties
  - If both parties have used a key recently, can transmit new key encrypted with old key
  - If both parties have an encrypted connection to `C`, they could deliver the key to `A` and `B` using an encrypted link

<a name="2.2"></a>

### Message Authentication & Hash Functions
- Protects us against active attacks (falsification of data / transactions)
- 2 Important Aspects of Message Authentication
  - Verify contents of message have not been altered
  - Verify source is authentic
- **Authentication without Encryption**
  - 3 situations where message authentication without confidentiality is preferred
    - Message Broadcast
    - Computer Program
      - Can be executed without having to decrypt every time
      - Waste of resources
    - Heavy Load
      - One side cannot afford to decrypt all messages due to heavy load
- **Message Authentication Code (MAC)**
  - Appended to a message
  - Assuming parties `A` & `B` share a secret key <code>K<sub>AB</sub></code>
    - When a message `M` is sent the MAC is calculated as a function of the message and the key
    - <code>MAC<sub>M</sub> = F(K<sub>AB</sub>, M)</code>
  - Recipient performs same calculations and compares codes
  - DES is used to encrypt the message
    - Last 16 / 32 bits are the code

- *Note: Authentication doesn't need to be reversible and because of the mathematical properties it's less vulnerable than encryption*

- **One Way Hash Function**
  - Produce a 'fingerprint' of a block of data (file, message, ...etc)
    - Alternative to `MAC`
  - Takes message `M` and produces fixed size message output `H(M)`
    - Message is always padded to a fixed length
    - The padding bits include the length of the original message
      - This is to increase difficulty of producing an alternate message with the same hash value
  - 3 Ways to Authenticate using Hash Code
    - Symmetric Encryption
    - Public Key Encryption
    - Keyed Hash MAC
      - Common key `K` combined with hash function
  - Computationally Infeasible
    - **Pre-Image Resistant**
      - Can't find `x` such that `H(x) = h`
    - **Second Pre-Image Resistant** (Weak Collision Resistant)
      - Can't find `H(y) = H(x)` where `y != x`
    - **Strong Collision Resistant** (Strong Collision Resistant)
      - Can't find a pair `(x, y)` where `H(x) = H(y)`

- **HMAC**
  - Developing a MAC from crypto hash code
    - Crypto hash functions execute faster
  - **Objectives**
    - Use existing hash functions
    - Be able to switch up hash functions as better ones come out
    - Simple way of handling keys
  - **Algorithm**
  ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/hmac.png)
  - **Security**
    - Depends on strength of hash function
    - Attacks on HMAC
      - Attacker computes the output of the compression function even with an IV that is secret and unknown to the attacker
      - Attacker finds collisions in the hash function

<a name="2.3"></a>

### Public Key Encryption
- Greater security from cryptanalysis than symmetric encryption
  - Strength of security depends on
    - Length of Key
    - Computational work needed to break a cipher
- General Purpose Technique
  - Makes symmetric encryption obsolete
  - Key distribution is simpler vs symmetric encryption
- **6 Step Process**  
  - Plain Text
  - Encryption Algorithm
  - Public & Private Key
    - One for encryption, One for decryption
    - Exact transformations depends on the key provided
  - Cipher Text
  - Decryption Algorithm
- **Requirements**
  - Easy to create key pairs
  - Easy for sender with public key to encrypt messages
  - Easy for receiver knowing private key to decrypt messages
  - Hard for someone else to determine private key from public key
  - Hard for someone to recover original message
  - Useful if either key can be used for either role  
- **Use Cases**
  - `A` sends a message to `B` using `B`'s public key for encryption and `B` decrypts it using their own private key
  - `A` encrypts data using private key and any corresponding public key can decrypt it
- **RSA Public Key Encryption**
  - Uses exponentiation of integers (modulo %) a prime number
  - Encrypt: <code> C = M<sup><i>e</i></sup> mod <i>n</i> </code>
  - Decrypt: <code> M = C<sup><i>d</i></sup> mod <i>n</i> = (M<sup><i>e</i></sup>)<sup><i>d</i></sup> mod <i>n</i> </code>
  - `PU = {e, n}  ; PR = {d, n}`
    - Both parties know values of `n` and `e`
    - Only receiver knows `d`
- **Security**
  - Brute Force Attacks
    - Try all possible private keys
  - Mathematical Attacks
    - Factoring the product of two primes
  - Timing Attacks
    - Exploits running time of decryption algorithm
  - Chosen Cipher Text Attacks
    - Exploits properties of the RSA algorithm

<a name="2.4"></a>

### Digital Signature & Management
- **Digital Signatures**
  - Created by encrypting hash code with a private key
    - Signature is appended to message and receiver hashes and checks
  - Used to authenticate source and data integrity
  - Does not provide confidentiality
    - Message is safe from alteration but not eavesdropping
- **Public Key Certificate**
  - Public keys are convenient because you can send them to a lot of people at once, but it also makes it easier for attackers
    - An attacker can fake a broadcast of someones public key
  - The way around this, is Public Key Certificates
  - Public Key + User ID
    - Whole block is signed by a trusted third party
    - Certificate also contains info about the third party and validity period of the certificate
- **Digital Envelopes**
  - Protects a message even before ensuring sender / receiver have the same keys  
    - Basically a sealed envelope with an unsigned letter
    - Useful when two users do not share a symmetric secret key
  - **5 Step Process**
    - Prepare a message
    - Generate a one-time use key
    - Encrypt message using one-time key
    - Encrypt the one-time key using other parties public key
    - Attach the encrypted one-time key to the encrypted message and send to other party
      - Other party can decrypt using their private key to get the one-time key to decrypt the message
- **Diffie-Hellman Key Exchange**
  - Exchange keys securely and use them for subsequent message encryption
  - Security is based on difficulty of computing discrete logarithms
    - Not protected against replay attack or Man-In-The-Middle attacks
    - Can overcome these with digital signatures and public-key certificates
  - **Process**
    - Select a prime number and a primitive root
      - A primitive root `a` of a number `p` is one whose powers generate all the integers from `1 -> p - 1`
      - <code> a mod p, a<sup>2</sup> mod p, .... a<sup>p-1</sup> mod p </code>
    - Compute public keys
    - Exchange and compute secret keys
- *Note: Other Algorithms - Digital Signature Standard (DSS), Elliptic-Curve Cryptography (ECC)*

<a name="2.5"></a>

### Random & Pseudorandom Numbers
- **Randomness**
  - Uniform Distribution
    - Frequency of each number should be approx. the same
  - Independence
    - No value in sequence can be inferred from another
    - Basically no patterns
- **Unpredictability**
  - Each number is statistically independent from other numbers in the sequence
  - Attacker should not be able to guess future numbers in sequence based on earlier ones
  - Again, no patterns
- **Uses**
  - Keys for public-key algorithms
  - Stream Key for stream ciphers
  - Symmetric Key for digital envelope
  - Session Key generation
- **Random vs Pseduorandom**
  - TRNG (True Random Number Generator)
    - Uses nondeterministic source to produce randomness
      - *Nondterministic: Even for same input, can exhibit different behaviour for different runs*
  - PRNG (Pseudo Random Number Generator)
    - Use math and computer programs to give the appearance of randomness
    - Statistically random

<a name="2.6"></a>

### Practical Application : Encryption of Stored Data
- **Pretty Good Privacy (PGP)**
  - User generates a key from a password and uses that to encrypt files
  - PGP does not store the password
    - To recover a file, user enters password, PGP generates key, PGP decrypts file
- **Back-end Appliance**
  - Hardware device sitting between servers and storage systems
  - Encrypts all data going from server -> storage and vice versa
- **Library Based Tape Encryption**
  - Based on co-processor board embedded in the tape drive and tape library hardware
- **Background Laptop & PC Data Encryption**
  - Software that provides encryption that is transparent to the user

---

<a name="Chapter3"></a>

## Chapter 3 - User Authentication
- Establishing confidence in user identities that are presented to a system
- 2 Steps
  - Identification
  - Verification

<a name="3.1"></a>

### Electronic User Authentication Principles
- Process of establishing confidence in user identities presented to the system electronically
- **Process**
  - Initial Requirement: User must be registered with the system
  - Applicant applies to Registration Authority (RA) to become a subscriber of a Credential Service Provider (CSP)
  - RA vouches to a CSP
  - CSP issues a credential to the subscriber
  - Credential can be used in subsequent auth events
- **Authenticating a User's Identity**
  - Something the user knows
    - Password, PIN
    - *Problems: Can guess or steal PINs and Passwords*
  - Something the user possesses
    - Key Cards, Physical Keys
    - *Problems: Can forge or steal tokens*
  - Something the user is (static biometrics)
    - Fingerprint, Facial Recognition
    - *Problems: False positives/negatives*
  - Something the user does (dynamic biometrics)
    - Voice Recognition, Handwriting / Typing Recognition
    - *Problems: False positives/negatives*
- **Risk Assessment**
  - Assurance Level: Certainty that the user using the credentials is the one that it was issued to
    - Level 1: Low Confidence
    - Level 2: Moderate Confidence
      - Requires some sort of authentication protocol
    - Level 3: High Confidence
      - Requires multi-factor authentication
    - Level 4: Very High Confidence
      - Requires multi-factor authentication and in-person registration
  - Potential Impact
    - Low: Limited adverse effects on operations
    - Moderate: Serious adverse effects
    - High: Catastrophic adverse effects
  - Areas of Risk
    - Low: Negligible financial/organizational loss
    - Moderate: Serious financial/organizational loss
    - High: Catastrophic financial/organizational loss

<a name="3.2"></a>

### Password Based Authentication
- User provides an id and a password
  - Systems compares it with stored password
  - ID determines user access, privileges ...etc
- **Salt & Hash**
  - Hashed passwords with a Salt value
  - Purpose of Salt
    - Duplicate passwords from being visible in the password file
    - Increases difficulty of offline dictionary attacks
    - Almost impossible to find out if a user used same password on multiple systems
- **Password Cracking**
  - Dictionary Attacks
    - Large dictionary of possible passwords
    - Each password must be hashed using each salt value before comparing
  - Rainbow Table Attacks
    - Pre-compute tables of hash values for all salts
    - Can counter this attack by using large salt and hash values
  - Guessable Passwords
    - Shorter password lengths are easier to crack
  - John the Ripper
    - Open source since '96
    - Brute Force + Dictionary tactics
- **Password File Access Control**
  - Deny attacker access to password file
- **Proactive Password Checking**
  - Rule Enforcement
    - Rules to force users to enter harder-to-crack passwords
  - Password Checker
    - Compile a dictionary of passwords not to use
  - Bloom Filter
    - Build a table of hash values
    - Compare password against the table

<a name="3.3"></a>

### Token Based Authentication
- **Token**: Object a user possess for authenticate purposes
- 2 Widely Used Types
  - **Memory Cards**
    - Store, but doesn't process data
    - Cons: Requires special reader, loss of token
    - *Ex: Magnetic Stripe Card*
  - **Smart Cards**
    - Physical Characteristics
      - Has an embedded microprocessor
    - Interface
      - Manual: Keypad and display for interaction
      - Electronic: Uses a reader/writer, contact or contactless
    - Authentication Protocol
      - Static
      - Dynamic Password Generator
      - Challenge-Response
    - Memory
      - Read Only Memory (ROM)
        - Stores data that never changes for the card's lifetime
      - Electrically Erasable Programmable ROM (EEPROM)
        - Holds application data and programs
      - Random Access Memory (RAM)
        - Holds temp data when applications are executed
- **Smart Card/Reader Exchange**
  - Card inserted into reader
    - A `reset` is initialized by the reader
    - This is to initialize parameters like clock value
  - Card responds with an `Answer To Reset (ATR)`
    - This message defines protocols, parameters and functions of the card
  - Terminal can use `Protocol Type Selection (PTS)` to change the protocol and other parameters
    - The card will confirm the changes with a `PTS Response`
  - Now the card can perform the desired application

<a name="3.4"></a>

### Biometric Authentication
- Authenticate a user based on *unique* physical characteristics
- Generic System
  - Registration associates a user with certain biometric characteristics
  - Verification involves checking that a claimed user is the actual user or identifying an unknown user

<a name="3.5"></a>

### Remote User Authentication
- Authentication over a network
  - More complex because of additional security threats  
- Relies on some form of challenge-response protocol to counter these threats
- **Challenge Response Protocol : Password**
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/ch_protec.png)

<a name="3.6"></a>

### Security Issues
|Attacks|Authenticators|Examples|Typical Defenses|
|-------|--------------|--------|----------------|
|<b> Client Attack </b>|Password  <br><br> Token <br><br> Biometric|Exhaustive Search, Guessing <br><br> Exhaustive Search <br><br> False Match|Large Entropy, Limited Guessing <br><br> Large Entropy, Limited Guessing <br><br> Large Entropy, Limited Guessing|
|<b> Host Attack </b>|Password  <br><br> Token <br><br> Biometric|Plaintext Theft, Exhaustive Search <br><br> Passcode Theft <br><br> Template Theft| Hashing, large entropy <br><br> Same as password, 1-time passcode <br><br> Capture device authentication, challenge-response|
|<b> Eavesdropping, Theft & Copying </b>|Password  <br><br> Token <br><br> Biometric|Shoulder Surfing <br><br> Theft, Counterfeiting hardware <br><br> Spoofing Biometrics|User need to keep a secrete and adminstrator needs to revoke compromised passwords <br><br> Multifactor Authentication <br><br> Copy detection at capture device and capture device authentication|
|<b> Replay </b>|Password  <br><br> Token <br><br> Biometric|Replay stolen password response <br><br> Replay stolen passcode response <br><br> Replay stolen biometric template response|Challenge-Response Protocol <br><br> Challenge-Response Protocol, 1-Time Passcode <br> Copy detection at capture device and capture device authentication via Challenge-Response Protocol|
|<b> Trojan Horse </b>|Password, Token, Biometric|Installation of rogue client or capture device|Authentication of client or capture device used within security perimeter|
|<b> Denial of Service </b>|Password, Token|Lockout by multiple|Multifactor with token|

- **Eavesdropping**
  - Learn password via an attack involving physical proximity of the user
- **Host Attacks**
  - Directed at the host, where password and biometric auth data is stored
- **Replay**
  - Repeating of user response (captured from before)
- **Client Attacks**
  - Trying to achieve user authentication without host access
- **Trojan Horse**
  - App / Physical device fakes being an authentic application to capture passwords or biometric credentials
- **Denial of Service**
  - Disable user authentication by flooding the service with tons of auth attempts


---
