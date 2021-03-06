# Software Quality Quiz 1 Notes


[Week 1 - Introduction ](#Lecture1)
<br>
[Week 2 - Processes, Methods, Techniques for Developing Quality Software](#Lecture2)
<br>
[Week 3 - Software Testing at the Unit, Module, Subsystem & System Levels](#Lecture3)
<br>


<a name="Lecture1"></a>
## Week 1 - Introduction

### Software Failure
- Caused by
  - Segmentation Faults
  - Deadlock
  - Wrong Implementation
  - Memory Leaks

### Software Quality
- The degree to which a system, component, or process...
  - meets specified requirements
  - meets customer or user needs or expectations
- Defined as an attribute of something
  - Refers to measurable characteristics we can compare to known standards
- Software Organization should minimize variation between predicted and actual values for **Cost**, **Schedule** and **Resources**
- Two kinds of quality are sought out
  - Quality of Design
  - Quality of conformance

#### Key Points
- Software Requirements
  - Foundation of how quality is measured
- Specified Standards
  - Development criteria to guide how software is engineered
- Implicit Requirements
  - Often are unmentioned requirements

#### Views
- Transcendental
  - Quality can be recognized (seen as ideal)
  - No definition for quality
- User
  - Product should meet user needs and expectations
- Manufacturing
  - Quality conforms to requirements
- Product
  - If product has good internal characteristics then external quality also good
- Value - Based
  - Quality depends on how much customer will pay for it

#### McCall's Quality Factors and Criteria
- Software Quality defined by two key concepts
  - Quality Factors
    - Represents the behavioral characteristics of a system
  - Quality Criteria
    - Attribute of a quality factor related to software development

|Quality Categories|Quality Factors|Broad Objectives|
|------------------|---------------|----------------|
|Product Operation |Correctness <br> Reliability <br> Efficiency <br> Integrity <br> Usability| Does it do what the customer wants? <br> Does it do it accurately all of the time? <br> Does it quickly solve the intended problem? <br> Is it secure? <br> Can I run it?|
|Product Revision  | Maintainability <br> Testability <br> Flexibility| Can it be fixed? <br> Can it be tested? <br> Can it be changed? <br>|
|Product Transition| Portability <br> Reusability <br> Interoperability| Can it be used on another machine? <br> Can parts of it be reused? <br> Can it interface with another system?|

### Fault, Error, Failure
- Fault: Code which could at some time in the future cause the program to perform in an unintended way
  - Faulty Code
  - Can lead to Error or Failure
  - Examples
    - Missing Initialization
    - Type Mismatch

- Error: Caused by a fault and represents the difference between the intended and actual results
  - Logic Error, Syntax Error
  - Examples
    - Infinite Loop
    - Missing Semicolon
    - Divide by 0

- Failure: External, incorrect behavior with respect to the expected behavior
  - Runtime Error

### Software Errors
- Faulty definition of requirements
- Client-Developer communication failures
- Deliberate deviations from software requirements
- Logical design errors
- Coding errors
- Non-Compliance with documentation and coding instructions
- Shortcomings of the testing process

### Quality Control
- Series of inspections, reviews and tests
- Ensures each product meets requirements
- Feedback loop to minimize errors

#### Quality Assurance Functions
- Auditing and Reporting functions that assess quality control
- Gives management insight on quality of products
  - Alerts them when quality issues need to be resolved

### Cost of Quality
- Costs incurred in trying to achieve quality
- Used to
  - Provide baseline for current cost of quality
  - Identify opportunities to reduce cost of quality
- Examples
  - **Prevention** costs
  - **Appraisal** costs
  - **Failure** costs
  - **Internal** Failure costs
  - **External** Failure costs

### Software Quality Assurance (SQA)
- Not the sole responsibility of the programmer
  - Extends to S.Eng, Project Managers, Customers, SQA Group
- SQA Group
  - Customer's In-House rep
  - Helps software team product high-quality product
  - Looks at software from customer point of view
- SQA Activities
  - **Prepare** plan for project
  - **Participate** in projects software process description
  - **Review** S.Eng activities
  - **Audit** software work products
  - **Ensures** deviations are documented
  - **Records** noncompliance and reports to management
  - **Coordinates** control and management of change
  - **Collects & Analyzes** software metrics

### Software Reviews
- Filter for the software process
- Applied throughout the software process
- Uncover errors
- Purify development process
- Catch large classes of errors that escape the programmer who wrote the code

#### Formal Technical Review (FTR)
- Uncover errors in
  - Function
  - Logic
  - Implementation
- Verify software meets requirements
- Achieve software developed in a uniform manner
- Make projects more manageable
- Promote backup and continuity
  - Helps other people become familiar with different parts of the software

#### The FTR Meeting
- 3 - 5 people
- Duration: < 2 Hours
- Focuses on specific work product
- Attendees include
  - Review Leader
  - All Reviewers
  - Producer
- At the End of the Meeting
  - Attendees must
    - Accept w/o modification
    - Reject due to sever errors
    - Accept Provisionally (w/ modification)
- After the Meeting
  - Identify problem areas with product
  - Meeting would have served as a checklist on what to fix
  - A report must be made that consists of
    - What was reviewed
    - Who reviewed it
    - What was concluded

#### FTR Guidelines
- Review the product (not the producer)
- Set and maintain an agenda
- Limit debate; Conduct in-depth discussions
- Find problem areas, but don't attempt to solve
- Take notes
- Limit # of participants
  - Insist on advance preparations
- Checklist to structure and focus the review
- Allocate resource / time for FTR's
- Review past FTR's to improve the review process

### SQA Plan
- Provides road map to establish software quality in an organization
- Template for SQA activities
- Structure
  - Purpose and Scope
  - Description
  - Standards and Practices
  - Actions and Tasks
  - Tools and Methods
  - Methods for Safeguarding and Maintaining SQA Records  
  - Organizational Roles and Responsibilities

### Software Reliability and Availability
- Reliability: Probability of failure-free operation in a specified environment for a specified time
  - Estimated using historical and development data
  - MTBF = MTTF + MTTR = Uptime + Downtime
  - Ex: MTBF = 68 + 3 days = 71 days
    - Failures per 100 days = 1/71 x 100 = 1.4
- Availability: Probability of operation according to requirements at a given point in time
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/r&a.png)

---

<a name="Lecture2"></a>
## Week 2 - Processes, Methods, Techniques for Developing Quality Software

### Implications of Maturity
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/CMM.png)

### Plan Driven & Agile Processes
- Plan Driven
  - Activities are planned in advance
  - Process is measured against the pre made plan
- Agile
  - Plan is made in increments
  - Can be changed as customer requirements change

### Waterfall Model
- One phase must be completed before moving onto next phase
- Harder to accommodate changes  
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/waterfall.png)

### Incremental Development
- Project is completed in versions
  - Each version implements new functionality
- Easier to accommodate changes compared to waterfall
  - Because versions are developed quickly it is costly to produce documentation for all the intermediate versions
- Easier to get customer feedback on the different versions
- System structure degrades without time spent refactoring it
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/increment.png)

### Reuse Oriented Software Engineering
- Reuses existing components or **COTS** (Commercial-Off-The-Shelf) systems
- Becoming a standard approach for building many types of business systems
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/reuse.png)

### Requirements Engineering Process
- Process of establishing needed services and necessary constraints
- Feasibility Study
  - Is it technically & financially feasible to build?
- Requirements Elicitation and Analysis
  - What do stakeholders require/expect from the system?
- Requirements Specification
  - Define requirements in detail
- Requirements Validation
  - Checking validity of requirements

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/reqengp.png)

### Software Design & Implementation
- Process of converting system specifications into an executable system
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/dp.png)

### Design Activities
- **Architectural Design**: Identify overall structure of the system, the principal components (subsystems / modules) and their relationships
- **Interface Design**: Define interfaces between system components
- **Component Design**: Take each system component and design how it will operate
- **Database Design**: Design system data structures and how they will be represented in a database

### Reducing costs of Rework
- **Change Avoidance**
  - While designing process, anticipate possible changes before significant rework is required
- **Change Tolerance**
  - Process is designed so changes can be made at a lower cost

### Software Prototyping
- Prototype is an initial version of a system used to demonstrate concepts and design options
- Benefits
  - Improved System Usability
  - Improved Design Quality  
  - Improved Maintainability
  - Reduced development effort
- Should focus on areas of the product that are not well understood
  - Can get clarity from customer when presenting a prototype
- Don't always need error checking and recovery in the prototype
- Focus on functional > non-functional requirements (Security / Reliability)

- Development Process
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/pd.png)

- **Throw Away Prototypes**: Discarded after development, will not be used in final product

### Incremental Delivery
- Instead of delivering one system
  - Break it down in increments
  - Each increment delivers part of the required functionality
- User requirements are included in early increments (higher priority)
- During development of an increment, requirements are frozen (no change until next increment)
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/id.png)
- Problems
  - Hard to identify what parts are needed by all increments until all of them are implemented
  - Specification is developed as the system is, but most places have a complete specification right at the start

### Boehm's Spiral Model
- Process represented as a spiral instead of sequence of activities
- Each loop in the spiral is a phase
- Sectors
  - **Objective Setting**
    - Specific objectives for the phase are identified
  - **Risk Assessment & Reduction**
    - Risks are assessed and activities put in place to reduce the key risks
  - **Development & Validation**
    - A development model for the system is chosen which can be any of the generic models
  - **Planning**
    -  The project is reviewed and the next phase of the spiral is planned
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/bsm.png)

### Extreme Programming
- Intended to improve software quality and responsiveness to changing customer requirements
  - Focuses on customer satisfaction
  - Delivers small features by priority in frequent intervals
- XP Practices
  - Pair Programming (Teams of 2)
  - Test Driven Development (Writing lots of tests and writing them early)
  - Continuous Integration (Putting code together as you write it, not at the last minute)
  - Coding Standards (Learn and follow well-established conventions)
  - Collective Code Ownership (You are responsible for your partner's code)
  - Simple Design (Eschew Obfuscation)

### Rational Unified Process
- Modern generic process derived from UML and associated process
- Brings together 3 generic process models
- Described from 3 perspectives
  - Dynamic perspective that shows phases over time
  - Static perspective shows process activities
  - Perspective that suggests good practice
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/rul.png)
- Phases
  - Inception
    - Establish business case for the system
  - Elaboration
    - Develop an understanding of the problem domain and the system architecture
  - Construction
    - System Design, Programming & Testing
  - Transition
    - Deploy system in its operating environment
- Iterations
  - In-Phase Iteration
    - Each phase is iterative with results developed incrementally
  - Cross-Phase Iteration
    - As shown by the loop in the diagram above, whole set of phases may be enacted incrementally

----

<a name="Lecture3"></a>
## Week 3 - Software Testing at the Unit, Module, Subsystem & System Levels

### Testing vs Debugging
- **Testing**: Evaluating software by observing its execution
  - Ways to test
    - Compile it
    - Run it on one input
    - Run it on many inputs
    - Run it on a representative set of inputs
    - Run it on all inputs
- **Debugging**: The process of finding a fault given a failure

### Definitions
- **Test Case**: Test case values, expected results, prefix values, and postfix values necessary to evaluate software under test
  - Specify input and expected output
- **Test Set**: Set of test cases
- **Expected Results**: The result that will be produced when executing the test if and only if the program satisfies its intended behavior
- **Test Case Values**: Input values necessary to complete some execution of the software under test
- **Prefix Values**: Inputs to prepare software for test case values
- **Postfix Values**: Inputs for software after test case values
- **Verification Values**: Inputs to show results of test case values
- **Exit Commands**: Inputs to terminate program or to return it to initial state
- **Test Requirement**: Specific element of a software artifact that a test case must satisfy or cover
- **Test Coverage**: A coverage criterion is a rule or set of rules that impose test requirements on a test set.
- **Unit Testing**: Tests individual subsystems, confirms that subsystems are correctly coded and carries out the intended functionality
- **Integration Testing**: Tests groups of subsystems, tests the interface among the subsystem
- **System Testing**: The entire system, determines if system meets the requirements (functional and global)
- **Acceptance Testing**: Demonstrate that the system meets customer requirements and is ready for use
- **Coverage Level**: Given a set of test requirements `TR` and a test set `T` the coverage level is the ratio of the number of test requirements satisfied by `T` to the size of `TR`
  - Example
  - `TR = {flavor=chocolate, flavor=vanilla, flavor=mint}`
  - `T = {3 chocolate, 1 vanilla}`
  - Coverage Level = 2/3 = 66.7%
- **Subsumption**: A test criterion C1 subsumes C2 if and only if **every** set of test cases that satisfies criterion C1 also satisfies C2

### Graph Coverage
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/gc.png)
- If `G'` is a subgraph of `G` then the nodes must also be a subset
  - Initial nodes of subgraph will be nodes of Nsub - N0 from parent graph  
  - Final nodes of subgraph will be nodes of Nsub - Nf from parent graph

### Path
- A sequence of nodes from a graph `G` whose adjacent pairs all belong to the set of edges `E of G`
  - Basically a path is formed with nodes that are neighbors
  - If a node is not a neighbor the path is invalid
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/path.png)
- **Subsequence**: Can be derived from another sequence by deleting some elements without changing the order of the remaining elements
- **Subpath**: All the edges must be in the path

### Control Flow Graph (CFG)
- Fundamental graph for source code
- **CFG Nodes**: Zero or more statement s
- **CFG Edges**: An edge `(s1, s2)` indicates that `s1` may be followed by `s2` during execution
- **Basic Block**: Has one entry point and one exit point

- CFG Example
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/selfCheck1.png)
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/selfCheck2.png)

- CFG Basic Block Example
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/basikBlok.png)





---
