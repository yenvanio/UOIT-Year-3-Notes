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

[Chapter 3 - Uncertainty Management in Rule-Based Expert Systems](#Chapter3)
- [Introduction](#3.1)
- [Basic Probability Theory](#3.2)
- [Bayesian Reasoning](#3.3)
- [Bias of the Bayesian Method](#3.4)
- [Certainity Factors Theory and Evidential Reasoning](#3.5)

[Chapter 4 - Fuzzy Expert Systems: Fuzzy Logic](#Chapter4)
- [Introduction](#4.1)
- [Fuzzy Sets](#4.2)
- [Linguistic Variables and Hedges](#4.3)
- [Operations of Fuzzy Sets](#4.4)
- [Fuzzy Rules](#4.5)

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
- Conflicting rules
  - If traffic light is red
    - THEN action is STOP
    - THEN action is GO
- Confliction Resolution is a method for deciding which rule to fire when more than one rule can be fired in a given cycle
- In forward chaining
  - STOP will happen first because it is the topmost
  - GO will also happen because the 'traffic light is red' is still a fact in the database, so GO will overwrite STOP
- Methods of Conflict Resolution
  - **Priority**
    - Simple priority rule is taking the one that appears first in order
  - **Most Specific Rule**
    - The rule that has the most matching
    - `IF X then Y` vs `IF X & A & B THEN Y` 
  - **Timestamps**
    - The rule that uses the most recently entered data into the database
  - **Metaknowledge**
    - Knowledge about *knowledge*
      - More specifically it is knowledge about the use and control of domain knowledge in an expert sytem
    - Represented by **Metarules**
      - Determines the use of task-specific rules (Priority)
      - Rule #1
        - Rules provided by experts > non-experts
      - Rule #2
        - Rules for rescuing human lives > rules for clearning overloads on power system equipment
- **Advantages of Rule-Based Expert Systems**
  - Natural knowledge representation
    - Can naturally represent an experts problem solving procedure using `IF, THEN` production rules
  - Uniform Structure
    - All rules have `IF, THEN` structure
  - Seperation of knowledge from its processing
    - Possible to develop different applications using same expert system shell
  - Dealing with incomplete and uncertain knowledge
    - Can represent and reason with incomplete knowledge
      - Fuzzy Logic
- **Disadvantages of Rule-Based Expert Systems**
  - Opaque relations between rules
    - Logic interaction of rules within a large set, hard to tell the effect of each individual rule
  - Ineffective search strategy
    - Exhaustive search through all rules during each cycle
    - Large rule-based systems are unsuited for real-time applications
  - Inability to learn
    - Do not learn from experience 

---

<a name="Chapter3"></a>

## Chapter 3 - Uncertainty Management in Rule-Based Expert Systems

<a name="3.1"></a>

### Introduction
- Uncertainty 
    - Lack of exact knowledge that would enable us to reach a reliable conclusion

- Law of Excluded Middle
    - If `A` is true `THEN` `A` is not false

- Sources of Uncertainity
    - Weak Implications
        - Domain experts are tasked with establishing concrete correlations between `IF` and `THEN` parts of the rules
        - Expert Systems must be able to handle vague associations
            - Do this by accepting the degree of correlations as numerical certainity factors
    - Imprecise Language
        - Natural Language is ambiguous and imprecise
            - Terms like: *often*, *sometimes*, *frequently*, *hardly ever*
        - Difficult to express the knowledge precisely 
        - If the meaning of the facts is **quantified** it can be used in expert systems.

- Quantification of Ambiguous and Imprecise Terms
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/ambiTF.png)

- Unknown Data
    - Incomplete or missing data
    - Only solution is to accept the value as *unknown* and approximate reasoning with this value

- Combining Views of Different Experts
    - Large expert systems usually combine knowledge of a number of experts
    - This leads to conflicting rules and contradictory opinions 
    - To resolve this, need to attach a weight to each expert and then calculate
        - No systematic method to obtain the weights though


<a name="3.2"></a>

### Basic Probability Theory
- The **Probability** of an event 
    - Proportion of cases in which the event occurs
    - Also defined as the **Scientific Measure of Chance**
        - `P(success) = # of success / # of possible outcomes`
        - `P(failure) = # of failures / # of possible outcomes`
        - Probability Index between 0 and 1
        - `# of possible of outcomes` = `# of success + # of failure`
- Example
    - If area of a triangle inside a square is `1/2 x^2` and area of square is `4x^2`
    - What is the probability that a random point in the square is inside the triangle
        - `1/2x^2 divided by 4x^2`
- Monty Hall Problem
    - 3 doors
        - 2 Goats, 1 Car
    - You pick a door
    - Monty shows you a door with a goat
    - Switch or Stay?
        - Want to switch because initial choice has a 1/3 of car which means other door must have the remaining 2/3 chance of a car
        - Another way to look at it, the odds of picking the correct door on the first try is 1/3 and switching is 2/3
    - Monty opening a goat door, gives us new information to act on, which increases our chances
- Conditional Probability
    - When the probability of two events are not mutually exclusive
    - Probability of A happening given that B has occured
    - `p(A|B) = # of times A & B can occur / # of times B can occur`
        - `p(A|B) = p(A ∩ B) / p(B)`
        - The number of times A & B can occur at the same time is called **Join Probability**
- Bayesian Rule
    - `p(A|B) = p(B|A) x p(A) / p(B)`
    - Can get this by substiting conditional probabiltiy equations
- Joint Probability
    - When A depends on multiple events of B
        - Σ p(A ∩ B<sub>i</sub>) = Σ p(A | B<sub>i</sub>) x p(B<sub>i</sub>)
    - If A depends only on `B` and `NOT B`
        - `p(A) = p(A|B) x p(B) + p(A|¬B) x p(¬B)`
        - `¬` = NOT
    - Substituting this into the Bayesian rule gives us the following formula
        - `p(A|B) = p(B|A) x p(A) / [ p(B|A) x p(A) ] + [ p(B|¬A) x p(¬A) ]`


<a name="3.3"></a>

### Bayesian Reasoning
- `IF E is true THEN H is true {with probability p}`
    - Rule implies that if `E` occurs, then there is a probability `p` that `H` will occur
- In an expert system usually represents a `hypothesis` an E denotes `evidence` to support the hypothesis
- Bayesian Rule in terms of evidence and hypothesis
    - `p(H|E) = p(E|H) x p(H) / [ p(E|H) x p(H) ] + [ p(E|¬H) x p(¬H) ]`
        - `p(H)` is the prior probability of the hypothesis H being true
        - `p(E|H)` is the probability that the hypothesis H being true will result in evidence E
        - `p(¬H)` is the prior probability of the hypothesis H being false
        - `p(E|¬H)` is the probability of finding evidence E even when hypothesis H is false
- In expert systems the prior probabilities are provided by experts
    - `p(H)` and `p(¬H)` are given by experts
    - They also provide conditional probabilities for observing evidence E if hypothesis H is true or false
- The conditional probability `p(H|E)` is then computed by the expert systems based on user input of Evidence E
    - Based on given user input (observations about evidence E)
- There can be multiple hypothesis and multiple evidence
    - **Evidences/Hypotheses must be mutually exclusive**
    - Single Hypothesis and Multiple Evidence
    - Multiple Hypothesis and Multiple Evidence
    - To solve these, need to gather conditional probabilities of all possible combinations of evidences and hypothesis
        - Huge burden on the expert


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/multiCP.png)


<a name="3.4"></a>

### Bias of the Bayesian Method
- Bayesian method requires probability values as primary inputs
    - Assessment of these values is left up to human judgement
    - Research shows that humans cannot elicit probability values consistent with the Bayesian Rules
    - Suggests that conditional probabilities may be inconsistent with prior probabilities given by the expert
    - Reason for the inconsistency is that the expert usually makes different assumptions when assessing the conditional and prior probabilities

<a name="3.5"></a>

### Certainity Factors Theory and Evidential Reasoning
- Certainty Factors is an alternative to Bayesian Reasoning
    - (cf) = a number to measure the expert's belief
        - Max value +1.0 (definitely true)
        - Min Value -1.0 (definitely false)
    - The (cf) value assigned to a rule is propagated throughout the chain
- For Conjuctive Rules (AND) the (cf) value is calculated as follows
    - If E<sub>1</sub> ... AND E<sub>N</sub>
    - cf(H, E<sub>1</sub> ... ∩ E<sub>N</sub> ) = min[cf(E<sub>1</sub>) ... cf(E<sub>N</sub>)] * cf(H)
- For Disjunctive Rules (OR) the (cf) value is calculated as follows
    - If E<sub>1</sub> ... OR E<sub>N</sub>
    - cf(H, E<sub>1</sub> ... ∪ E<sub>N</sub>) = max[cf(E<sub>1</sub>) ... cf(E<sub>N</sub>)] * cf(H)
- If 2 rules support the same hypothesis with different certainty factors
    - `IF` A is X `THEN` C is Z {cf 0.8}
    - `IF` B is Y `THEN` C is Z {cf 0.6}
    - How would you determine the cf value of C having a value of Z if both rules are fired?
        - Because 2 rules are pointing to the same hypothesis, the cf should be higher
        - Can calculate using the following formula


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/doubleCF.png)

---

<a name="Chapter4"></a>

## Chapter 4 - Fuzzy Expert Systems: Fuzzy Logic

<a name="4.1"></a>

### Introduction
- Fuzzy logic is logic for describing fuzziness
    - Used to calibrate vagueness 
    - Represents how people think
        - We dont think in terms of strictly boolean (0 or 1)
    - Fuzzy logic is a set of mathematical principles for knowledge representation based on degrees of membership.
- Jan Lukaseiwicz came up with the **Possibility Theory** 
    - He used values that included all real numbers between 0 and 1
    - The numbers in the interval represent the probability that a statement was true or false
- Max Black claimed vagueness is a matter of probability
    - Line up countless chairs, each successive chair is less chair like until the last one which is a log
    - At what point does a chair become a log?
    - If a continuum is discrete a number can be allocated to each element
- Lotfi Zadeh
    - Master of Fuzzy Logic

<a name="4.2"></a>

### Fuzzy Sets
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/crispFuzz.png)

- A fuzzy set is a set with fuzzy boundaries 


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mbFunc.png)

- Set A of Universe X is defined by the membership function μ<sub>A</sub>(x)
    - The set allows for more than just a 1 or 0
    - The membership function represents the degree to which x is an element of set A a.k.a the **Degree of Membership** or **Membership Value** of element x in set A
- Representing Fuzzy Sets in a Computer
    - Example: Men's Heights
    - Can have fuzzy sets of `Tall` `Short` `Average`
    - Different heights are classified under different fuzzy sets
        - A height can be part of two fuzzy sets 
        - 184cm tall is a member of average men with a degree of membership = 0.1
        - 184cm tall is also a member of tall men with a degree of membership = 0.4

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/crispFuzz2.png)



<a name="4.3"></a>

### Linguistic Variables and Hedges
- A Linguistic variable is a fuzzy variable
    - `John is tall`
    - Implies that the linguistic variable *John* takes the linguistic value *tall*
- Fuzzy Rules use linguistic variables
    - `IF` wind is strong
    - `THEN` sailing is good
- Range of possible values of a linguistic variable represents the universe of discourse for that variable
    - Linguistic variable `speed` can have a range from 0km/h to 220km/h
    - Fuzzy subsets can be very slow, slow, medium, fast, very fast
- A linguistic variable has fuzzy set qualifiers called **Hedges**
    - Hedges are terms that modify the shape of fuzzy sets
    - `Very` `Somewhat` `Quite` `More` `Less` `Slightly`

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/veryduD.png)

<a name="4.4"></a>

### Operations of Fuzzy Sets
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/cantorSet.png)

- Complement
    - Complement of a set is an opposite of the set
        - A  = set of `tall men`
        - ¬A = set of `NOT tall men`
        - μ<sub>¬A</sub>(x) = 1 - μ<sub>A</sub>(x)
    - `Crisp Sets`: Who doesn't belong to the set
    - `Fuzzy Sets`: How much do elements not belong to the set
- Containment
    - `Crisp Sets`: Which sets belong to which other sets
        - All elements of a subset belong entirely to a larger set
    - `Fuzzy Sets`: Which sets belong to other sets
        - Each element can belong less to the subset than the large set
            - Smaller membership value in subset than large set
- Intersection
    - `Crisp Sets`: Which element belongs to both sets
        - Intersection of tall men set and fat men set is the area of overlap
    - `Fuzzy Sets`: How much of the element is in both sets
        - Elements may partly belong to both sets with different memberships
        - Intersection is the lower membership in both sets of the element
- Union
    - `Crisp Sets`: Who element belongs to either set
        - Union of tall men and fat men = all men who are tall or fat
    - `Fuzzy Sets`: How much of the element is in either set
        - Reverse of intersection
        - Union is the largest membership value of the element in either set

<a name="4.5"></a>

### Fuzzy Rules
- A fuzzy rule is a conditional statement in the form 
    - `IF x is A` : `THEN y is B`
        - `x` and `y` are linguistic variables 
        - `A` and `B` are linguistic values determined by fuzzy sets on the universe of discourses `X` and `Y`
- Fuzzy rules relate fuzzy sets 
- **Monotonic Selection**
    - Fuzzy inference when the output value is estimated from a corresponding output in the antecedent (IF OR/AND part of the rule)
- Fuzzy rules can have multiple antecdents and multiple consequents
    - `IF` service is excellent
    - `OR` food is delicious
    - `THEN` tip is generous; mood is happy;

<a name="4.6"></a>

### Fuzzy Inference
- Mamdani Fuzzy Inference
    - 4 Step Process
        - Fuzzification of Input Variables
        - Rule Evaluation
        - Aggregation of Rule Outputs
        - Defuzzification
    - Example
        - Rule 1:
            - `IF` x is A3
            - `OR` y is B1 
            - `THEN` z is C1
        - Rule 2:
            - `IF` x is A2
            - `AND` y is B12
            - `THEN` z is C2
        - Rule 3:
            - `IF` x is A1
            - `THEN` z is C3
    - Fuzzification

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/fuzzif.png)


    - Rule Evaluation

- Sugeno Fuzzy Inference
