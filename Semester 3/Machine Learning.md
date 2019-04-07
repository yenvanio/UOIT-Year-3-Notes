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
- [Fuzzy Inference](#4.6)

[Chapter 5 - Evolutionary Computation: Genetic Algorithms](#Chapter5)
- [Introduction](#5.1)
- [Simulation of Natural Evolution](#5.2)
- [Genetic Algorithms](#5.3)

[Chapter 6 - Artificial Neural Networks](#Chapter6)
- [Introduction](#6.1)
- [The Neuron as a Simple Computing Element](#6.2)
- [The Perceptron](#6.3)
- [Multilayer Neural Networks](#6.4)
- [Back Propagation Neural Network](#6.5)
- [Accelerated Learning in Multilayer Neural Networks](#6.6)

[Chapter 7 - Artificial Neural Networks: Unsupervised Learning](#Chapter7)
- [Introduction](#7.1)
- [Hebbian Learning](#7.2)
- [Self Organizing Computational Map: Kohonen Network](#7.3)

[Chapter 8 - Deep Learning](#Chapter8)
- [Introduction](#8.1)
- [Unsupervised Pre-Trained Networks (UPNs)](#8.2)
- [Convolutional Neural Networks (CNNs)](#8.3)
- [Recurrent Neural Networks (RNNs)](#8.4)
- [Recursive Neural Networks](#8.5)

[Chapter 9 - Hybrid Intelligent Systems](#Chapter9)
- [Introduction](#9.1)
- [Neural Expert Systems](#9.2)
- [Neuro-Fuzzy Systems](#9.3)
- [Evolutionary Neural Networks](#9.4)

[Chapter 10 - Introduction to Data Mining](#Chapter10)
- [Introduction](#10.1)
- [Data Mining Function](#10.2)
- [Issues in Data Mining](#10.3)

[Chapter 11 - Getting to Know your Data](#Chapter11)
- [Data Objects & Attribute Types](#11.1)
- [Basic Statistical Descriptions of Data](#11.2)
- [Data Visualization](#11.3)
- [Data Similarity vs Dissimilarity](#11.4)

[Chapter 12 - Clustering](#Chapter12)
- [Introduction](#12.1)
- [K-Means Clustering](#12.2)
- [Agglomerative Hierarchical Clustering](#12.3)
- [Mean Shift Clustering](#12.4)
- [DBSCAN](#12.5)

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


#### Mamdani Fuzzy Inference
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
        - `AND` y is B2
        - `THEN` z is C2
    - Rule 3:
        - `IF` x is A1
        - `THEN` z is C3
- 1.) Fuzzification

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/fuzzif.png)


- 2.) Rule Evaluation
    - Take fuzzified inputs and apply them to the antecedents of the fuzzy rules
        - μ<sub>(x = A1)</sub> = 0.5
        - μ<sub>(x = A2)</sub> = 0.2
        - μ<sub>(y = B1)</sub> = 0.1
        - μ<sub>(y = B2)</sub> = 0.7
    - If `OR` / Union then use `max`
    - If `AND` / Intersection then use `min`
    - Evaluating 
        - Rule 1: 
            - x is A3 = 0
            - y is B1 = 0.1
            - z is `C1(0.1)` (OR = max)
        - Rule 2:
            - x is A2 = 0.2
            - y is B2 = 0.7
            - z is `C2(0.2)` (AND = min)
        - Rule 3:
            - x is A1 = 0.5
            - z is `C3(0.5)`

- 3.) Aggregation of Rule Outputs
    - Process of unifying the outputs of all the rules 
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/aggZ.png)

- 4.) Defuzzification
    - Output of a fuzzy system must be a crisp number
    - Most popular defuzzification method is called the **Centroid Technique**
        - Finds the point where a vertical line slices the aggregated set into two equal masses.
        - This **Center of Gravity (COG)** can be expressed by the function below

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/COGF.png)

- Numerator Values
    - Points off of the x axis (summed) and multiplied by the degree of membership
- Denominator Values
    - Degree of Membership multiplied by number of points taken and used in the numerator

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/COGcalc.png)

#### Sugeno Fuzzy Inference
- The Mamdani-style inference is not computationally efficient
- The Sugeno methods uses a single spike vs integrating across a function
    - A fuzzy singleton is a fuzzy set with a membership function that is unity at a single point and 0 everywhere else
- Format of Sugeno Fuzzy Rule
    - `IF` x is A 
    - `AND` y is B 
    - `THEN` z is f(x,y)
        - x, y, z are linguistic variables
        - A & B are fuzzy sets 
        - f(x, y) is a mathematical function 
- Most common used zero-order Sugeno Fuzzy Model applies fuzzy rules in the following form 
    - `IF` x is A 
    - `AND` y is B
    - `THEN` z is `k`
        - `k` is a constant 
        - In this case the output of each fuzzy rule is constant 
        - All consequent membership functions are represented by fuzzy singletons
- Evaluating 
    - Rule 1: 
        - x is A3 = 0
        - y is B1 = 0.1
        - z is `k1(0.1)` (OR = max)
    - Rule 2:
        - x is A2 = 0.2
        - y is B2 = 0.7
        - z is `k2(0.2)` (AND = min)
    - Rule 3:
        - x is A1 = 0.5
        - z is `k3(0.5)`
- Defuzzification


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/waFuzz.png)

---

<a name="Chapter5"></a>

## Chapter 5 - Evolutionary Computation: Genetic Algorithms

<a name="5.1"></a>

### Introduction
- Evolutionary approach is based on computational models of natural selection and genetics
    - The result of this simulation is a series of optimisation algorithms, usually based on a simple set of rules
    - This optimisation happens iteratively and improves the quality of the solutions until an optimal solution is found
- Evolutionary Computation is an umbrella term that combines the following
    - Genetic Algorithms 
    - Evolution Strategies
    - Genetic Programming

<a name="5.2"></a>

### Simulation of Natural Evolution
- **Evolutionary Fitness**: A populations ability to survive in reproduce in a specific environment
    - It is also the organism's ability to anticipate changes in its environment
    - This ability is the quality that is optimised in natural life 
- Example: Rabbits and Foxes
    - The faster rabbits will survive due to their superior fitness
    - These superior fitness rabbits will produce offspring with even greater fitness
- Natural Evolution - General Process
    - Creating a population of individuals
    - Evaluating their fitness
    - Generating a new population through genetic operations
    - Repeating this process `n` number of times

<a name="5.3"></a>

### Genetic Algorithms
- Two mechanism link a genetic algorithm (GA) to the problem its trying to solve
    - Encoding
    - Evaluation
- GA uses the fitness of individual chromosomes to carry out reproduction
    - As reproduction happens...
        - Crossover Operator exchanges parts of two single chromosomes
        - Mutation Operator changes the gene value in some randomly chosen location of the chromosome
- Basic Genetic Algorithm Process
    - `Step 1`
        - Choose the Chromosome Population size `N`
        - Choose the Crossover Probability p<sub>c</sub>
        - Choose the Mutation Probability p<sub>m</sub>
    - `Step 2`
        - Define a fitness function that measures the fitness of an individual chromosome
        - The fitness function is the basis for selecting chromosomes to be mated
    - `Step 3`
        - Randomly generate an initial chromosome population of size `N`
    - `Step 4`
        - Calculate the fitness of each individual chromosome
    - `Step 5`
        - Select a pair of chromosomes for mating from the current population
        - Parent chromosomes are selected with a probability based on their fitness
            - Random Weighted Probability
            - Also known as *Roulette Wheel Selection*
    - `Step 6`
        - Create a pair of offspring chromosomes by applying the genetic operators 
            - Crossover Operator
                - One Point Crossover
                    - Swaps all the genes on the right side of the point between two chromosomes
                - Two Point Crossover
                    - Swaps all the genes in between the two points between two chromosomes
                - Uniform Crossover
                    - Simplest case
                        - Swaps genes at randomly selected points between two chromosomes
                    - Can be based on a given distribution
                - No Crossover
                    - Cloning takes place and the offspring created are exact copies of the parent
            - Mutation Operator
                - Represents a change in the gene
                    - Reciprocal Exchange
                        - Swaps two randomly selected genes
                    - Inversion Operator
                        - Selects two random points on the chromosome and reverses the order of genes between these points
                - Used to make sure the algorithm isnt trapped on a local optimum
                - It basically flips a randomly selected gene in a chromosome
                - Probability is pretty small, usuall between 0.001 and 0.01
    - `Step 7`
        - Place the created offspring chromosomes in the new population
    - `Step 8`
        - Repeat `Step 5` until the size of the new population equals `N`(size of the initial population)
    - `Step 9`
        - Replace the initial chromosome population with the new population
    - `Step 10`
        - Go to `Step 4` and repeat until termination criteria is satisfied
- Each iteration in the genetic algorithm = **Generation**
    - A GA can range from 50 to over 500 generations
    - Its common to end the GA after a specified  # of generations
- **Run** is the entire set of generations
    - If a solution isnt found after `n` generations then we do another run

---

<a name="Chapter6"></a>

## Chapter 6 - Artificial Neural Networks

<a name="6.1"></a>

### Introduction
- Main Applications of ANN
    - Pattern Classification
    - Prediction and Financial Analysis
    - Control and Optimization
- Sample Real World Applications
    - CC Fraud Detection
    - Optical Character Recognition (OCR)
    - Foreign Exchange Trading Systems
- A neural network is based on the reasoning model of the human brain
    - Brain consists of densely interconnected set of nerve cells 
        - Nerve Cells are basic information processing units a.k.a **Neurons**
    - Each neuron has a simple structure but using multiple simultaneously the brain performs functions at very fast rates
        - Faster than computers
        - Tremendous Processing Power
- Neuron consists of the following
    - Soma - Cell Body 
    - Dendrites - A Number of Fibers
    - Axon - Single Long Fiber
- The brain is a highly complex, non-linear and parallel information processing system
    - Information is stored and processed in a neural network
        - This means the processing and data are **global** not local
    - Leaning is a fundamental and essential part of neural networks
    - This is why it is being used in computing
- How a Neural Network Works
    - Consists of a number of simple processors (Neurons)
    - Neurons are connected by weighted links that pass signals between them
    - Output signal is split into branches 
        - The branches terminate at the incoming connections of other neurons
    - Structure
        - Neuron (Soma)
        - Input (Dendrite)
        - Output (Axon)
        - Weight (Synapse)

<a name="6.2"></a>

### The Neuron as a Simple Computing Element
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/neuron.png)

- Neuron computs the *weighted sum* of the input signals
- The function the neuron uses is called an **Activation Function** and is shown below along with the different types
- The sum is compared to a threshold value `θ`
    - If sum < threshold
        - `Output = -1`
    - If sum > threshold
        - `Output = +1`
    - This type of activation function is known as a **Sign Function**


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/acNeuron.png)

- The most basic ANN can be made up of just one neuron
    - Frank Roseblatt develop the first training algorithm for this ANN 
    - Called a **Perceptron**
- Perceptron is the simplest form of an ANN
    - Consits of
        - A single Neuron
        - Adjustable Synaptic Weights
        - A Hard Limiter


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/sl2ip.png)


<a name="6.3"></a>

### The Perceptron
- The model consists of
    - A Linear Combiner
    - A Hard Limiter
- Weighted sum of inputs is applied to hard limiter 
    - Output is either `+1` if its  positive
    - or `-1` if its negative
- The goal of the percepton is to classify inputs x<sub>1</sub> ... x<sub>n</sub>
    - For example lets say classes `A1` and `A2`
- An Elementry Perceptron its n-dimensional space is divided into **two decision regions** by a hyperplane
    - The hyperplane is define by a *linearly seperable function*
    - The sum of (x<sub>i</sub>w<sub>i</sub>) - θ = 0
- How does a perceptron learn?
    - It makes small adjustments in the weight values
    - The adjustments are made to reduce the difference between the actual and desired output
    - Inital weight is randomly assigned
        - Usually within a range of `[-0.5, 0.5]`
    - To figure out how to make the changes, we need to calculate the error
- Perceptron Error
    - For the p<sup>th</sup> training example presented to the perceptron
    - e(p) = Y<sub>d</sub>(p) - Y(p)
        - If the error `e(p)` is positive we need to increase the perceptron output Y(p)
            - If positive then Y(p) is less than desired output
            - Need to increase to get ideal error of 0
        - If the error `e(p)` is negative we need to decrease the perceptron outout Y(p)
            - If negative then Y(p) is greater than desired output
            - Need to reduce to get ideal error of 0


#### The Perceptron Learning Rule
- p = 1, 2, 3, ...
- α = Learning Rate
    - A positive constant less than unity
- e(p) = error of perceptron
- w<sub>i</sub>(p) = weight of perceptron
- Using this rule we can derive the training algorithm

#### Perceptron Training Algorithm
- `Step 1: Initialization`
    - Set initial weights w<sub>1</sub>...w<sub>n</sub>
        and the threshold θ to random numbers in the range [-0.5, 0.5]
- `Step 2: Activation`
    - Use this step function to calculate the actual output
    - Since it is a step function
        - IF `Y(p)` < 0 then `Y(p)` = 0
        - IF `Y(p)` >= 0 then `Y(p)` = 1

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/stepstep.png)


- `Step 3: Weight Training`
    - Depending on error `e(p)` need to increase or decrease the perceptron output Y(p)
    - `e(p)` = Y<sub>d</sub>(p) - Y(p)
    - If `e(p)` != 0
        - Need to calculate the Weight Correction Value
            - Δw<sub>i</sub>(p) = α • x<sub>i</sub>(p) • e(p)
        - Using the correction value you can calculate the weight at the next iteration `p+1`
            - w<sub>i</sub>(p+1) = w<sub>i</sub>(p) + Δw<sub>i</sub>(p)
- `Step 4: Iteration`
    - Go back to step 2 and repeat until `e(p)` = 0
    - The weight values will keep getting updated with each iteration until the actual output Y(p) = The desired output Y<sub>d</sub>(p)

- Perceptrons can learn `AND` and `OR` operations but not `XOR`

<a name="6.4"></a>

### Multilayer Neural Networks
- A neural network with one or more hidden layers
- Network consists of...
    - **Input Layer** of source neurons
    - At least one **Hidden Layer** of computational neurons
    - **Output Layer** of computational neurons
- Input signals propagate on a layer-by-layer basis

- Multilayer perceptron with two hidden layers
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mp22.png)

- The middle layer hides its desired output
    - Neurons in the hidden layer cant be observed
    - No way to know what the desired output of the hidden layer should be


<a name="6.5"></a>

### Back Propagation Neural Network
- Unlike the perceptron algorithm, Back Propagation has two phases in its algorithm
    - Phase 1
        - Training input pattern is passed to the input layer
        - Network propagates the input pattern, layer by layer until the output pattern is generated by the output layer
    - Phase 2
        - If the output is different from the desired output, the error is calculated
        - The error is then propagated backwards through the network from output to input
        - Weights get modified as the error is propagated

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/bpnn.png)


#### Back Propagation Training Algorithm
- `Step 1: Initialization`
    - Set weight and threshold levels to random numbers in the range
    [-2.4/F<sub>i</sub>  ,  +2.4/F<sub>i</sub>]
    - F<sub>i</sub> = total number of inputs of neuron `i`
    - Weight initialization is done on a neuron-by-neuron basis
- `Step 2: Activation`
    - Now we use a Sigmoid function instead of a step function
    - `2.1` Calculate the actual outputs of the neurons in the hidden layer (`j`)
        - `n` is the # of inputs of neuron `j` in the hidden layer
        - x<sub>i</sub> is the input to neuron `i`
        - w<sub>ij</sub> is the weight from neuron `i` to neuron `j` in the hidden layer
        - θ<sub>j</sub> is the threshold of neuron `j` in the hidden layer
        - ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/sigmoidfns.png)

    - `2.2` Calculate the actual outputs of the neurons in the output layer (`k`)
        - `m` is the # of inputs of neuron `k` in the output layer
        - x<sub>jk</sub> is the input to neuron `k` from the neuron `j` in the hidden layer
        - w<sub>jk</sub> is the weight from neuron `j` in the hidden layer to neuron `k` in the output layer
        - θ<sub>j</sub> is the threshold of neuron `k` in the output layer
        - ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/sigmoidfnr.png)

- `Step 3: Weight Training`
    - Two steps, output layer then the hidden layer, because back propagation
    - `3.1 - Output Layer`
        - Calculate Error Gradient for neurons in the output layer
            - 𝛿<sub>k</sub>(p) = y<sub>k</sub>(p) • [1 - y<sub>k</sub>(p)] • e<sub>k</sub>(p)
                - e<sub>k</sub>(p) = y<sub>d, k</sub>(p) - y<sub>k</sub>(p)
                - y<sub>d, k</sub>(p) = Desired output for neuron `k` in the output layer
        - Calculate the Weight Corrections
            - Δw<sub>jk</sub>(p) = α • y<sub>j</sub>(p) • 𝛿<sub>k</sub>(p)
        - Update the Weights
            - w<sub>jk</sub>(p+1) = w<sub>jk</sub>(p) + Δw<sub>jk</sub>(p)
    - `3.2 - Hidden Layer`
        - Calculate the Error Gradient for neurons in the hidden layer
            - 𝛿<sub>j</sub>(p) = y<sub>j</sub>(p) • [1 - y<sub>j</sub>(p)] • [ Σ 𝛿<sub>k</sub>(p) • Δw<sub>jk</sub>(p) ]
        - Calculate the Weight Corrections
            - Δw<sub>ij</sub>(p) = α • x<sub>i</sub>(p) • 𝛿<sub>j</sub>(p)
        - Update the Weights
            - w<sub>ij</sub>(p+1) = w<sub>ij</sub>(p) + Δw<sub>ij</sub>(p)
- `Step 4: Iteration`
    - Increase iteration and go back to `Step 2`
    - Repeat this until goal output is reached

- **We couldn't do `XOR` with a single layer perceptron but we can do it now with multilayers**

<a name="6.6"></a>

### Accelerated Learning in Multilayer Neural Networks
- Multilayer networks learn faster when the sigmoid function gets modified
    - By replacing the Sigmoidal function with a Hyperbolic Tangent
    - With constants `a = 1.716` and `b = 0.667`

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/ytanh.png)


- Another way to accelerate training is to include a momentum term in the weight correction equation
    - Δw<sub>jk</sub>(p) = `β` • Δw<sub>jk</sub>(p-1) + α • y<sub>j</sub>(p) • 𝛿<sub>k</sub>(p)
    - β is the momentum constant
        - 0 <= β < 1 
        - Typically set to 0.95
    - The equation is the **Generalized Delta Rule**

- We can apply two heuristics so that we can accelerate the process without compromising stability
    - **Heuristic 1**
        - If the change of `Sum of Squared Errors (SSE)` has the same sign (+/-) for several consequent epochs, then the learning rate parameter `α` should be increased
    - **Heuristic 2**
        - If the sign (+/-) of the change of `Sum of Squared Errors (SSE)` alternates for several consequent epochs, then the learning rate parameter `α` should be decreased

---

<a name="Chapter7"></a>

## Chapter 7 - Artificial Neural Networks: Unsupervised Learning

<a name="7.1"></a>

### Introduction
- The main purpose of a neural network is sot hat it can learn and improve its performance
- Unsupervised learning algorithms aim to learn rapidly and be used in real time
    - Doesnt require an external teacher
    - Able to recieve input patterns
        - Discover features in the patterns
        - CLassify the input data into categories
    - Follows the neuro-biological organization of the brain

<a name="7.2"></a>

### Hebbian Learning
- **Hebb's Law**: If `neuron i` is close enough to exicte  `neuron j` and repeatedly participates in its activation, the synaptic connection between these two neurons is strengthened and `neuron j` becomes sensitive to stimuli from `neuron i`
    - **Rule 1**: If two neurons on either side of a connection are *activated synchronously* ten the weight of the connection is increased
    - **Rule 2**: If two neurons on either side of a connection are *activated asynchronously* ten the weight of the connection is decreased

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/hebbianNN.png)

- Hebb's Law allows us to adjust the weight formulas to the following
    - Δw<sub>ij</sub>(p) = F[y<sub>j</sub>(p), x<sub>i</sub>(p)]
    - A special case of Hebb's law with the α (learning rate)
        - Δw<sub>ij</sub>(p) = α • y<sub>j</sub>(p) • x<sub>i</sub>(p)
    - Since the learning implies that weights can only increase
        - Need to resolve by limiting growth of synaptic weights with a **forgetting factor**
        - Δw<sub>ij</sub>(p) = α • y<sub>j</sub>(p) • x<sub>i</sub>(p) - φ • y<sub>j</sub>(p) • w<sub>ij</sub>(p)
            - We can factor out the y<sub>j</sub>(p) to get a general equation
            - Δw<sub>ij</sub>(p) = φ • y<sub>j</sub>(p) [λ• x<sub>i</sub>(p) - w<sub>ij</sub>(p)]
                - This equation is the **Generalized Activity Product Rule**
                - In this case λ = α / φ
                    - Because we factored out φ
            

#### Hebbian Learning Algorithm
- `Step 1: Initialization`:
    - Set initial synaptic weights and thresholds to random values within the interval [0, 1]
- `Step 2: Activation`:
    - Compute neuron output
    - `n` is the number of neuron inputs
    - θ<sub>j</sub> is the threshold value of neuron `j`


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/hebbianNN.png)

- `Step 3: Learning`:
    - Update weights in the network
        - Δw<sub>ij</sub>(p + 1) = w<sub>ij</sub>(p) + Δw<sub>ij</sub>(p)
    - The weight correction factor is given by the formula we derived above
        - Δw<sub>ij</sub>(p) = φ • y<sub>j</sub>(p) [λ• x<sub>i</sub>(p) - w<sub>ij</sub>(p)]
        - Where λ = α / φ
- `Step 4: Iteration`:
    - Increase iteration and go back to `Step 2` until goal output is reached

<a name="7.3"></a>

### Self Organizing Computational Map: Kohonen Network
- **Competitive Learning**
    - Neurons compete to be activated
    - In Hebbian learning, several neurons can be activated simultaneously
    - In Competitive learning only a single neuron is active at any time
- The output neuron that gets activated is basically the winner
- Special type of ANN called **Self-Organizing Feature Maps**
    - Based on Competitive Learning
- **Relation to the Brain**
    - Cerebral Cortex dominates the brain
        - Contains billions of neurons and hundreds of billions of synapses
        - The cortex contains area responsible for different human activities
            - Each area is associated with different sensory inputs
    - The cortex is a self-organising computational map in the human brain

#### Kohonen Network
- This model provides a topological mapping
- Places fixed # of input patterns from intput layer into a higher dimensional output (**Kohonen Layer**)
- Training starts with the *winner's* neighbourhood of a large size
    - With each iteration of the training, the neighbourhood size decreases

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/konan.png)

- The lateral connections (the connections between the blue circles ^)
    - This is to create competition between neurons 
    - The neuron with the largest activation level among all the output neurons is the winner
    - The winner is the only one that then produces an output signal
        - Rest of the neuron activity is supressed by the competition
- The lateral connections produce either one of the following depending on the distance from the winning neuron
    - **Inhibitory**
    - **Excitatory**
- To determine what is produced, we use a **Mexican Hat Function**
    - It describes synaptic weights between neurons in the Kohonen Layer

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mexicano.png)


- Learning in this network works by neurons shifting weights from inactive connections to active connections
    - Only winning neuron and its neighbourhood allowed to learn
    - If a neuron does not respond to a given input then, learning cannot occur at that neuron

#### Competitive Learning Algorithm
- `Step 1: Initialization`
    - Set initial synaptic weights to small random values in the range [0, 1]
    - Assign a small positive value to the learning rate α
- `Step 2: Activation & Similarity Matching`
    - Activate the Kohonen Network by finding the winning neuron (j<sub>x</sub>) using the minimum-distance Euclidean Criterion
        - After finding the distance, the winning one would be the minimum because of the shortest distance
    - j<sub>x</sub>(p) = min||x - w<sub>j</sub>(p)
        - = Σ {[x<sub>i</sub> - w<sub>ij</sub>(p)]<sup>2</sup>}<sup>1/2</sup>
- `Step 3: Learning`
    - Update the weights
    - w<sub>ij</sub>(p+1) = w<sub>ij</sub>(p) + Δw<sub>ij</sub>(p)
    - Δw<sub>ij</sub> (The change applied to the weight)
        - If Neuron `j` wins the competition
            - = α(x<sub>i</sub> - w<sub>ij</sub>(p))
        - If Neuron `j` loses the competition
            - = 0
- `Step 4: Iteration`
    - Increase iteration and go back to `Step 2` and repeat until criterion is satisfied

- **Summary of Self-Organizing Map (SOM)**
    - Trained using unsupervised learning 
        - Produces a low-dimensional (usually 2 dimensional) representation of the input
    - They differ from other ANN because they use competitive learning vs error-correction learning
        - Error correction is like backpropagation
    - The differ in the sense that they use a neighborhood function to preserve the topological properties of the input space


<a name="Chapter8"></a>

## Chapter 8 - Deep Learning

<a name="8.1"></a>

### Introduction
- Deep Learning is born from Big Data and Massive Computational Power
    - It is useful because it has higher performance for large amounts of data
- The idea was to build learning algorithms to mimic the brain
- The bigger the neural network the better the performance, with deep learning

<a name="8.2"></a>

### Unsupervised Pre-Trained Networks (UPNs)
- 

<a name="8.3"></a>

### Convolutional Neural Networks (CNNs)
- 

<a name="8.4"></a>

### Recurrent Neural Networks (RNNs)
- 

<a name="8.5"></a>

### Recursive Neural Networks
- 


<a name="Chapter9"></a>

## Chapter 9 - Hybrid Intelligent Systems

<a name="9.1"></a>

### Introduction
- **Hybrid Intelligent System**: combining two or more intelligent technologies
    - For example
        - Neural Network + Expert System
        - Neural Network + Fuzzy System
- Words are less precise than numbers but numbers carry a higher cost
    - Words are used when a system has a tolerance for imprecision 
- **Soft Computing**: An approach to building hybrid intelligent systems
    - Capable of reasoning and learning in an uncertain/imprecise environment
    - Core of Soft Computing consists of
        - Probabilistic Reasoning
        - Fuzzy Logic
        - Neural NEtworks
        - Evolutionary COmputation
    - It exploits the tolerance for unertainty and imprecision to achieve more robustness and lower the cost of solutions
- Comparison of the Systems

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/syscom.png)


<a name="9.2"></a>

### Neural Expert Systems
- Expert Systems
    - Rely on decision trees and model `human reasoning`
    - Treat the brain as a black-box
    - Represented by `IF-THEN` rules
        - Knowledge can be divided into individual rules
- Neural Networks
    - Rely on parallel data processing and model `human brain`
    - Look at the structure, function and ability of the brain to learn
    - Knowledge stored as `synaptic weights between neurons`
        - Knowledge cant be divided, it is embedded in the entire network
        - One Synaptic Weight wont give you any information but the entire network will
        - Basically a black-box for the user

#### Neural Expert System
- Structure of a Neural Expert System

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/nesSTUC.png)

- The heart of a neural expert system is the `inference engine`
    - It controls information flow (from the neural network)
    - It performs inference over the knowledge base (from the expert system)
    - Ensures **Approximate Reasoning**

- Approximate Reasoning
    - Instead of precisely matching rules with data from the database, we replace the knowledge base with a neural network so we can approximate the reasoning

- The following is an example of determining if something is a bird, using approximate reasoning

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/birdex.png)

- In the above example, each property (`Wings`, `Tail`, `Engine`) has a +1, 0 or -1 value to it
    - `+1` is true
    - `0` is unknown
    - `-1` is false
- This allows us to get a semantic interpretation for the activation of output neurons
- Basically sum the weights multiplied by the truth value (+1, 0, -1)
    - X<sub>Rule 1</sub> = 1•(-0.8) + 0•(-0.2) + 1•(2.2) + 1•(2.8) + -1•(-1.1) = 5.3
        - 5.3 > 0
        - Y<sub>Rule 1</sub> = Y<sub>Bird</sub> = +1
- Can make an inference if the `Sum of Weighted Known Inputs` is greater than `Sum of AbsoluteValue(Weights of Unknown Inputs)`
    - Σ x<sub>i</sub>w<sub>i</sub> > Σ | w<sub>j</sub> | 

- Multilayer Knowledge Base Example

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mlkbetch.png)

<a name="9.3"></a>

### Neuro-Fuzzy Systems
- Fuzzy Systems cannot learn by themselves and cannot adjust to new environments
    - By combining them with neural networks, they can now learn and adapt
    - Also neural networks become more transparent by combining them with fuzzy systems because they can use the explanation abilities of a fuzzy system
- They can be trained to
    - Develop `IF-THEN` fuzzy rules
    - Determine membership functions (how much of this is in set A)
        - Ex: `Rule 1(0.8)`
    - Incorporate expert knowledge
- The structure is similar to a multi-layer neural network
    - Input Layer
    - 3 Hidden Layers
        - These layers represent the membership functions and fuzzy rules
    - Output Layer

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/nfnazi.png)

- `Layer 1: Input Layer`
    - Each neuron transmits **crisp** signals to the next layer
    - y<sub>i</sub><sup>(1)</sup> = x<sub>i</sub><sup>(1)</sup>
        - The `(1)` represents which layer the variable is associated with
        - x<sub>i</sub><sup>(1)</sup> = Input to Layer 1
        - y<sub>i</sub><sup>(1)</sup> = Output of Layer 1

- `Layer 2: Fuzzification Layer`
    - Neurons represent fuzzy sets used in the `IF` statements of fuzzy rules
        - The `IF` condition
    - A fuzzification neuron takes a **crisp** input and determines the degree of membership (how much this input belongs in the neuron's fuzzy set)
        - This is determined by a Triangular Activation Function because we use triangular sets
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mfuckath.png)

- `Layer 3: Fuzzy Rule Layer`
    - Each neuron represents a single fuzzy rule
    - Takes inputs from the fuzzification layer
    - Outputs of the fuzzy rule layer are determined by intersections
        - Intersections can be implemented by the product operator
        - Outputs of Layer 3 are as follows
            - y<sub>i</sub><sup>(3)</sup> = x<sub>1i</sub><sup>(3)</sup> • x<sub>2i</sub><sup>(3)</sup>  •...• x<sub>ki</sub><sup>(3)</sup> 
            - Example from the structure above
                - y<sub>C1</sub><sup>(4)</sup> = μ<sub>R3</sub> • μ<sub>R4</sub> = μ<sub>C1</sub>

- `Layer 4: Output Membership Layer`
    - Each neuron represents a fuzzy set from the `THEN` part of fuzzy rules
        - The result of the `IF` condition 
    - Output neuron combines all its inputs by using the `Union` operation
        - Basically the `OR` operator
    - y<sub>i</sub><sup>(4)</sup> = x<sub>1i</sub><sup>(4)</sup> ⨁ x<sub>2i</sub><sup>(4)</sup>  ⨁...⨁ x<sub>ki</sub><sup>(4)</sup> 
    - Example from the structure above
        - y<sub>C1</sub><sup>(4)</sup> = μ<sub>R3</sub> ⨁ μ<sub>R4</sub> = μ<sub>C1</sub>
        - μ<sub>C1</sub> = Integrated Firing Strength of Fuzzy Rules R3 & R6

- `Layer 5: Defuzzification Layer`
    - Each neuron represents a single output of the neuro-fuzzy system
    - Takes the fuzzy sets and combines them into a single fuzzy set
        - Before combining, the fuzzy sets are clipped by the respective firing strength
    - Normal defuzzification techniques can be applied
        - Like the `Centroid Technique`
        - We're gonna use `Sum-Product Compostion`
- **Sum-Product Composition**
    - Caluclates the weighted average of centroids of all output membership functions
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/avgcent.png)

- Learning
    - Basically a multi-layer neural network so it can use standard learning algorithms like back-propagation
    - By incorporaing `IF-THEN` rules supplied by domain experts, the training can be expedited
- Neuro-Fuzzy Systems should be able to identify bad rules
    - Because experts do make mistakes and some rules may be false or redundant
- When a representative set of examples is available
    - Neuro-Fuzzy Systems should be able to automatically transform it into a set of fuzzy `IF-THEN` rules.

<a name="9.4"></a>

### Evolutionary Neural Networks
- Backpropagation sometimes creates a set of sub-optimal weights which make it hard to find a desirable solution
- The network topology is usually selected by heuristics
- By combining genetic algorithms with neural networks, we can
    - optimize weight
    - optimize topology selection
- `Step 1`: Encoding Weights in a Chromosome
- `Step 2`: Define a Fitness Function
    - Estimate performance of a neural network
    - Can apply the Sum of Squared Errors Function
        - Smaller the sum, fitter the chromosome
    - GA tries to find weights that minimise the sum of squared errors
- `Step 3`: Choose Crossover and Mutation Operators
    - Crossover takes two parents and creates a child
        - Child has genetic material from both parents
    - Mutation selects a gene in the chromosome and adds a random value (-1, 1) to the weights in the gene


- Genetic Algorithms help us search for a suitable network architecture in a population of potential candidates
    - This is needed because without it, it's basically trial and error
- First, Need to encode network architecture into a chromosome
    - Represented by a square connectivity matrix
    - `0` means no connection between neurons
    - `1` means connection with weight (that can be changed through learning)
    - To convert matrix to chromosome, string the rows together

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/encodeMatCh.png)

---

<a name="Chapter10"></a>

## Chapter 10 - Introduction to Data Mining

<a name="10.1"></a>

### Introduction
- Extraction of interesting patterns or knowledge from huge amounts of data
    - Example: Web Mining. It involves...
        - Data Cleaning
        - Data Integration from multiple sources
        - Data Selectiong for mining
        - Data Mining
        - Presentation of Results
        - Patterns to be stored in knowledge base

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/pyraMIDsch.png)

- Knowledge Discovery in Databases
    - `Step 1`: Input Data
    - `Step 2`: Data Pre-Processing
        - Normalization
        - Feature Selection
        - Dimension Reduction
    - `Step 3`: Data Mining
        - Pattern Discovery
        - Association & Correlation
        - CLassification
        - Clustering
        - Outlier Analysis
    - `Step 4`: Post Processing
        - Pattern Evaluation
        - Pattern Selection
        - Pattern Interpretation
        - Pattern Visualization
    - `Step 5`: Pattern Information Knowledge

- Multi-Dimensional View of Data Mining
    - Data to be Mined
        - Database data, Data Warehouse, Multi-Media, Graphs, Social/Information Networks
    - Knowledge to be Mined
        - Characterization, Association, Classification, Clustering
        - Descriptive vs Predictive Data Mining
    - Techniques Utilized
        - Machine Learning, Statistics, Pattern Recognition, Visualization
    - Applications Adapted
        - Retail, Telecommunications, Banking, Fraud Analysis

<a name="10.2"></a>

### Data Mining Function
- `Step 1`: Generalization
    - Information Integration & Data Warehouse Construction
        - Data cleaning
    - Data Cube Technology
        - Scalable methods for computing
    - Characterization & Discrimination
        - Generalize, Summarize, Contrast
- `Step 2`: Association & Correlation Analysis
    - Frequent Patterns
    - Association, Correlation vs Causality
- `Step 3`: Classification
    - Label Prediction
        - Describe & Distinguish classes or concepts for future predictions
        - Predict unknown class labels
    - Methods
        - Decision Trees, Bayesian Classification
    - Applications
        - CC Fraud Detection, Direct Marketing, Diseases
- `Step 4`: Cluster Analysis
    - Unsupervised learning
    - Group data to form new clusters
    - Goal is to **Maximize** intra-class similarity & **Minimize** interclass similarity
        - Maximize similarities within the group
        - Minimize similarities between other groups
- `Step 5`: Outlier Analysis
    - **Outlier**: Data that does not comply with general behavior of the data
    - **Noise**: Could be useful or an exception
        - One person's garbage could be another person's treasure
    - **Methods**: Clustering or Regression Analysis

<a name="10.3"></a>

### Issues in Data Mining
- Mining Methodology
- User Interaction
- Efficiency & Scalability
- Diversity of Data Types
- Data Mining & Society

--- 

## Chapter 11 - Getting to Know your Data

<a name="11.1"></a>

### Data Objects & Attribute Types
- Types of Data Sets
    - Record
        - Relational Records
        - Data Matrix
        - Transaction Data
    - Graph / Network
        - WWW
        - Social / Information Networks
        - Molecular Structure
    - Ordered
        - Time Series
        - Genetic Sequence Data
    - Spatial / Image / MultiMedia
        - Image
        - Video
- Characteristics of Structured Data
    - Dimensionality
    - Sparsity
    - Resolution
    - Distribution
- Data Objects
    - Data sets are made up of data objects
    - Data object is an entity
        - Example Data Set: Sales Database
        - Example Data Objects: Customers, Store Items, Sales
    - Objects are described by attributes
    - **Database Rows = Data Objects**
- Attributes
    - A data field, representing a feature of a data object
        - customer_ID, name, address
    - Types
        - Nominal
            - Basically categories
        - Binary
            - Nominal but with only 2 states
            - Symmetric: Both outcomes are equally important
                - Example: Gender
            - Asymmetric: Outcomes not equally important
                - Example: Medical Test (Positive vs Negative)
        - Ordinal 
            - Values have a meaningful order (Ranking)
                - Example: Grades
    - Discrete 
        - Finite or countable values
            - ZIP Codes, Set of words, collection of documents
            - **Binary Attributes are a special case of discrete attributes**
    - Continuous
        - Real numbers
            - Temperature, Height, Weight
    - **Database Columns = Data Attributes**

<a name="11.2"></a>

### Basic Statistical Descriptions of Data
- Measuring Central Tendency
    - Mean
        - Average
    - Median
        - Middle Value 
            - Average of Middle if two values in middle
    - Mode
        - Most Frequently appearing
    - Empirical Formula: `Mean` - `Mode` = 3 x (`Mean` - `Median`)
- Skewed Data
    - Positive Skew
        - The data skews to the right (positive direction)
            - Mound is to the left, dies down to the right
        - Mean > Median
    - Negative Skew 
        - The data skews to the left (negative direction)
            - Mound is to the right, dies down to the left
        - Mean < Median
    - **Mean is always further in the direction of the skew than the Median**

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/skewskew.png)

- Normal Distribution Curve
    - 68% of the measurements are within the range of the mean 
        - +- 1 * standard deviation
    - 95% of the measurements are within the range of the mean
        - +- 2 * standard deviation
    - 99.7% of the measurements are within the range of the mean
        - +- 3 * standard deviation
- Histogram
    - Graph that displays bars representing the frequencies
    - It shows which bars fall into what category
- Scatter Plot
    - Shows clusters of points, outliers
    - Correlation is shown below

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/correll.png)

<a name="11.3"></a>

### Data Visualization
- 

<a name="11.4"></a>

### Data Similarity vs Dissimilarity
- **Similarity**: Numerical measure of how alike two data objects are
    - Range of [0, 1]
    - Higher value = more similarity
- **Dissimilarity**: Numerical measure of how different two data objects are
    - Lower values when objects are more alike
    - Min value = 0 
- Data Matrix
    - `n` data points with `p` dimensions
- Dissimilarity Matrix
    - `n` data points but registers only the distance
    - Triangular Matrix

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/matrIX.png)

- Minkowski Distance
    - Positive Definiteness: `d(i,j)` > 0 if `i` != `j` and `d(i,i)` = 0
    - Symmetry: `d(i,j)` = `d(j,i)`
    - Triangle Inequality: `d(i,j)` <= `d(i,k)` + `d(k,j)`
- A distance that satisfies these properties is a metric
- Special Cases
    - `h = 1` Manhattan Distance
    - `h = 2` Euclidean Distance

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/minko.png)
- `i` and `j` are two p-dimensional data objects
- `h` is the order
    - Distance, also called the `L-h` norm

- **Cosine Similarity**
    - A measure of similarity between two vectors
    - `cos(d1, d2)` = `d1` • `d2` / ||d1|| ||d2||
        - Dot Prduct of `d1` and `d2`
            - Multiply each number from `d1` with `d2` in order
        - Divided by ||d1|| x ||d2||
            - Square each number and sum them
            - Then square root the sum
--- 


## Chapter 12 - Clustering

<a name="12.1"></a>

### Introduction
- Given a set of data points, group them into clusters so that...
    - Points within clusters are similar
    - Points from different clusters are dissimilar
- For points in high-dimensional spaces
    - Similarity is defined using distance measures
        - Eculidean, Cosine ...etc
- Importance
    - Real world science/engineering problems can be modeled as a clustering problem
    - Allows us to segregate data based on properties/features and group them
- Similarity for clustering
    - Based on set of observations
    - If the observations are in the same subset than they are similar in some sense

<a name="12.2"></a>

### K-Means Clustering
- Algorithm
    - Determine the number of clusters
    - Randomly initialize `k` data points to be cluster centers
    - Repeat the following until the centers are unchanged
        - `Step 1`: Allocate each data point to a cluster whose center is nearest
        - `Step 2`: Ensure every cluster has at least one point
            - For empty clusters, randomly select a point far from the cluster center
        - `Step 3`: Replace cluster center with the `mean` of the cluster
- Pros
    - Fast because less computations
- Cons
    - Starts with random choice of cluster centers
        - so results can lack consistency
    - `k` needs to be given
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/kkkm.png)

<a name="12.3"></a>

### Agglomerative Hierarchical Clustering
- Algorithm
    - Each point starts off as it's own clusters
    - Repeat the following until only 1 cluster remains
        - Find the pair of clusters that are closest to each other
            - To find closest you pick the points nearest to each other from each cluster
        - Merge the clusters
            - The height on the graph represents the distance between prior to merging
- Pros
    - No need to specify number of clusters
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/anglo.png)

<a name="12.4"></a>

### Mean Shift Clustering
- Algorithm
    - Repeat with multiple sliding windows until all the points lie within a window
        - For overlapping windows, higher points window will prevail
    - Each window represents a cluster of data points
        - Start with a circular sliding window at a randomly selected point `C` with radius `r`
        - Repeat the following until you reach a point where you can accommodate the maximum number of points within it
            - Shift window towards denser regions by changing centre point
                - The new centre point is the mean of the points within the window
                - Shifting the mean ensures the window moves towards denser regions
            - You will know this is the goal state by comparing it to the next and previous states
                - Greedy Algorithm type of shit
- Pros
    - Converging towards a maximum density point is desirable
        - Data Driven
- Cons
    - Selection of window size is not trivial to do

<a name="12.5"></a>

### DBSCAN
- Density-Based Spatial Clustering of Applications with Noise
