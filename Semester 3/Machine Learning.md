# Machine Learning


## Table of Contents

[Chapter 1 - Introduction to Knowledge-Base Intelligent Systems](#Chapter1)
- [Intelligent Machines](#1.1)
- [History of Artifcial Intelligence](#1.2)
<br>

[Chapter 2 - Rule Based Expert Systems](#Chapter2)
- [Rules - Knowledge Representation Technique](#2.1)
- [Main Players in the Development Team](#2.2)
- [Structure of Rule-Based Expert System](#2.3)
- [Characteristics of an Expert System](#2.4)
- [Forward Chaining and Backward Chaining](#2.5)
- [Conflict Resolution](#2.6)

----

<a name="Chapter1"></a>

## Chapter 1 - Introduction to Knowledge-Base Intelligent Systems

<a name="1.1"></a>

### Intelligent Machines
- Intelligence is the ability to **understand** and **learn** things
- Turing's Imitation Game
    - Phase 1
        - Interrogator, Man & Woman
        - Man tries to deceive the interrogator that he is a woman
        - Woman tries to prove to the interrogator that she is a woman
    - Phase 2
        - Man is replaced with a computer
            - Computer provides fuzzy answers to imitate human mistakes
        - If the computer fools the interrogator as much as the man
            - Passed the **Intelligent Behavior** test
    - *A program that is thought to be intelligent in a certain area of expertise, is evaluted by comparing its performance with a human expert.*

<a name="1.2"></a>

### History of Artifcial Intelligence
- Warren McCulloch & Walter Pitts, proposed **Artifical Neural Networks** in 1943
    - Demonstrated that simple network structures could learn
- John von Neumann designed the **Electronic Discrete Variable Calculator**
- Claude Shannon published the paper on chess-playing machines
    - Pointed out that a typical chess game involved about 10<sup>120</sup> possible moves
    - So using the Neumann-type computer it could examine one move per microsecond it would take 3 x 10<sup>106</sup> years to make it's first move.
    - So Shannon proved that you *need heuristics to while searching for the solution*
        - **Heuristic**: Enabling something to learn for itself
- Most funding for AI was stopped because there were no real world applications
    - The problems were always too broad and difficult
    - These were referred to as **Weak Methods**
    - Realized that to deliver practical results, was to solve cases in narrow areas of expertise

- **DENDRAL**
    - Developed at Stanford
        - Purpose was to determine the molecular structure of Martian soil
    - Tried to make computer perform at a human expert level
        - These programs were known as **Expert Systems**
    - Big Paradigm Shift
        - From General Purpose to Domain Specific
    - The team proved that computers can equal a human expert in narrow, well defined problem areas.
        - *Knowledge Engineering*: Techniques of capturing and expressing an experts "know-how" in rules.
- Expert Systems can show the sequence of rules they applied to reach a solution, but can't relate to any deepre understanding of the problem domain
    - Ex: A system designed for diagnosis of infectious blood disease
        - Can do that diagnosis only, not identify any other problems
- These systems also did not learn from previous experiences 

- **Evolutionary Computation (EC)**
    - Survival of the fittest, the fittest have a chance to reproduce and pass on genetic material
    - EC combines the three main techniques
        - Genetic Algorithms (GA)
        - Evolutionary Strategies (ES)
        - Genetic Programming (GP)

- **Fuzzy Logic**
    - Important when dealing with vague, imprecise and uncertain knowledge
        - Experts think in terms of *generally*, *sometimes*, *occassionally*
    - Fuzzy Logic uses the concept of a **linguistic variable**
        - Variable is words rather than numbers
        - Provides a means of computation with words
    - Benefits derived from fuzzy logic
        - **Improved Computational Power**
            - Expert Systems performed faster and needs fewer rules
            - Merges rules
            - Most Expert Systems used fuzzy logic to solve computationally difficult problems
        - **Improved Cognitive Modelling**
            - Easier to improve modelling because don't have to define strict boundaries for expert rules like *fast*, *slow*, *heavy*, *light*

---

<a name="Chapter2"></a>

## Chapter 2 - Rule Based Expert Systems

<a name="2.1"></a>

### Rules - Knowledge Representation Technique
- A **Rule** in AI can be defined as an *IF-THEN* structure
    - Consists of two parts 
        - **IF** = *Antecedent* (premise or condition)
            - Contains an Object and a Value, linked by an Operator
        - **THEN** = *Consequent* (conclusion or action)
    - Can chain antecedents using **AND**, **OR**

<a name="2.2"></a>

### Main Players in the Development Team
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mpDT.PNG)

- **Domain Expert**
    - Capable of solving problems in a specific area (domain)
    - Greatest experience in a given domain
        - Most important player in the team
- **Knowledge Engineer**
    - Capable of designing, building and testing an expert system
    - Gets reasoning methods from the expert and decides how to represent them in the system
    - Responsible for testing, revising and integrating the system into the workplace
- **Programmer**
    - Responsible for the actual programming, describing domain knowledge in terms that the computer can understand
- **Project Manager**
    - Leader of the team
    - Keeps the project on track, make sure deliverables and deadlines are met
- **End-User**
    - Basically the user of the expert system after development

<a name="2.3"></a>

### Structure of Rule-Based Expert System
- **Production Model**
    - Based on how humans apply knowledge (production rules) to a given problem
    - Production rules are stored in long term memory
    - Problem-Specific information is stored in short term memory
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/srbesS.PNG)
- **Knowledge Base**
    - Contains domain knowledge useful for problem solving
    - Represented by a set of rules
- **Database**
    - Contains facts used to match against the *IF* condition parts of rules from the knowledge base
- **Inference Enginer**
    - Carries out the reasoning
    - Links rules with facts
- **Explanation Facilities**
    - Enables user to ask *how* a conclusion is reached and *why* a fact is needed
    - Expert Sytem must be able to justify its conclusion
- **User Interface**
    - Means of communication between a user and the expert system.

<a name="2.4"></a>

### Characteristics of an Expert System
- **High Quality Performance**
  - Need to make sure result is correct, not just fast
- **Speed**
  - Althought quality is important, no use if result is too late
- **Heuristics**
  - Systems apply heuristics to guide the reasoning and reduce the search area
- **Explantion Capability**
  - Enables system to review and explain its own reasoning and decisions
- **Symbolic Reasoning**
  - Symbols are used to represent different types of knowledge (facts, concepts, rules)
- **Mistakes**
  - Expert systems should still be allowed to make mistakes
  - Afterall they are designed to imitate humans
- Expert systems split up knowledge and processing 
  - Knowledge base and inference engine are split up

<a name="2.5"></a>

### Forward Chaining and Backward Chaining
- Inference engine compares rules from the knowledge base with facts contained in the database
  - When the *IF* condition matches a fact the rule is fired and *THEN* is executed
  - The matching produces **Inference Chains**. 
    - Indicates how the sytem applies rules to reach a conclusion
- **Forward Chaining**
  - Data Driven Reasoning
  - Starts with known data
    - Each time only the topmost rule is executed
    - After every match & fire, a fact is added to the database
    - Stops when no more rules can be matched & fired
  - Used to gather information first then infer from it
  - May end up executing rules that have nothing to do with the goal
    - Not efficient if goal is to infer only one particular fact
- **Backward Chainng**
  - Goal Driven Reasoning
  - Starts with a goal (*hypothetical solution*)
    - Tries to find supporting evidence
    - Search knowledge base to find rules that might have the solution
      - Goal must be in their *THEN* action part
      - Ex: If Goal = X, find a rule where THEN x is true (lets say Z)
        - Next find a rule where THEN Z is true
      - Rules basically stack and sets up new goals until finds enough evidence

<a name="2.6"></a>

### Conflict Resolution
- 