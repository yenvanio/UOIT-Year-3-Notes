understanding# Software Quality Quiz 3 Notes


[Week 10 - Refactoring](#Lecture10)
<br>
[Week 11 & 12 - Software Metrics](#Lecture1112)
<br>


<a name="Lecture10"></a>
## Week 10 - Refactoring
- As software evolves and strays from original design
  - 3 things happen
    - Decreased understandability
    - Decreased Reliability
    - Increased Maintenance Cost
  - These happen due to
    - Increased complexity of code
    - Out-of-Date documentation
    - Code not conforming to standards

- Code is refactored to improve
  - Readability
  - Extensibility
  - Maintainability
  - Modularity

- **DOES NOT** Modify software functionalities
- Refactoring can be performed **WHILE** adding new features

### Refactoring Process
1. Identify what to refactor
2. Determine which refactoring to apply
3. Preserving the software's behavior
4. Apply the refactoring to the chosen entities
5. Evaluate the impacts of refactoring
6. Maintain consistency

#### Identify What To Refactor
- From source code, design documents and requirements documents
  - Focus on specific functions, classes methods
- **Code Smell** is used to detect what should be refactored
  - It is a symptom in the source code that indicates a deeper problem
  - Ex: Duplicate Code, Long Methods, Large Classes, Long Parameter List

#### Determine which Refactoring to Apply

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/10.1.0.png)

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/10.1.1.png)

#### Preserving Software's Behavior
- Need the functionality (input / output) of a program to be same before and after refactoring
- Also want to preserve non-functional requirements
  - **Temporal Constraints**
    - A temporal constraint over a sequence of operations is that the operations occur in a certain order
  - **Resource Constraints**
    - The software after refactoring does not demand more resources: memory, energy, communication bandwidth, and so on
  - **Safety Constraints**
    - It is important that the software does not lose its safety properties after refactoring
- Ways of showing that the behavior has been maintained
  - Testing before and after
  - Verification of preservation of call sequence

#### Impacts of Refactoring on Quality
- Impacts internal & external qualities of software
  - Internal Example: `size, complexity, cohesion, testability`
  - External Example: `performance, reusability, maintainability, scalability`
- Refactoring is usually highly specialized (very specific)
  - A refactor technique improves a small amount of quality attributes

#### Maintain Consistency
- Instead of evaluating impacts after refactoring
  - Select refactorings such that upon completion it has better quality attributes
- **Soft Goal Graph** used to select refactorings

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/SGG.PNG)

- The focused quality attribute is the root node (High Maintainability)
- The internal nodes represent successive refinements of the attribute
- Leaf Nodes represent refactoring that affects the soft goals above it
  - (Connected with dotted lines)

### Formalisms for Refactoring
- **Assertions**
  - Verifies assumptions made by programmer
  - Boolean Expression
  - 3 Kinds of Assertions
    - **Invariants**
      - Assertion that evaluates to true when invoked
      - *Class Invariant*: All instances of the class must satisfy
    - **Pre Conditions**
      - Condition to be satisfied before computation
    - **Post Conditions**
      - Condition to be satisfied after computation

- *These assertions help test the behavior preserving property of refactoring*

- **Graph Transformation**
  - Class Diagrams / State charts can be seen as graphs
  - Refactorings can be seen as graph production rules
  - Push Down Method
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/graphTrans.png)

### More Refactoring Techniques
- **Substitute Algorithm**
  - Replace algorithm X with algorithm Y because it is
    - Clearer
    - Performs better
  - Easy to replace if algorithms have same input/output behaviors

- **Replace Parameter with Methods**
  - Instead of passing 2 parameters from the same object, pass the object as a parameter
  - Want to avoid long parameter lists

- **Push Down Method**
  - If a subclass has a method used by one subclass and not the other, can push it down to the only subclass that needs it.

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/pushDown.PNG)

- **Parameterize Methods**
  - If multiple method do the same computation with different inputs
  - Make a new method with same computation but have a parameter that can invoke the other methods as well.

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/wifi.PNG)

### Factors Influencing Software Structure
- Code
- Documentation
- Tools
- Programmers

### Restructuring Techniques
- **Elimination of GoTo Approach**
  - GoTo statements basically causes a jump to another line in the program whereas functions return control
  - GoTo statements can be transformed into goto-less programs using `while` statements

- **Localization & Information Hiding Approach**
  -

---

<a name="Lecture1112"></a>
## Week 11 & 12 - Software Metrics

### Software Metrics: Basics
- No. of Lines of Code is the most popular software metric

- Software Quality Models Breakdown
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/sqm.png)


- **Human Error**: Designer's Mistake
- **Fault**: Encoding of an error into a software product
- **Failure**: Deviation of the software from expected behavior
- Example:
  - Human error: Failure to distinguish signed and absolute value numbers in an algorithm
    resulted in:
  - Fault: `X:=Y` is coded instead of `X:= ABS(Y)` which in  turn led to
  - Failure: Nuclear reactor shut down because it was determined wrongly  that a meltdown   was likely.
- **Processing Error**: An erroneous state that is triggered by a fault
  - Does not immediately crash
  - Example:
    - An operating system fault is triggered by a particular input resulting in a processing error that causes a another processing error in the word-processor which then crashes.
- **MTTF** = Mean Time To Failure
- Faults & Failures
  - ~35% of all faults only lead to very rare failures (MTTF > 5000 years)
  - Less than 2% of all faults lead to the common failures

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mttf.png)

- Most faults are benign
  - When fixed doesn't really improve reliability that much
  - Reliability only significantly improves when we hit the 2% of bugs

- **Defects** = `{Faults} U {Failures}` (Union)
- **System Defect Density** = `# of Defects Found / System Size (KLOC)`
- *The danger of associating a measure of fault density with software quality (especially if quality is synonymous with reliability which is defined as the probability of failure-free operation in a given time period under given operational conditions).*

- Popular belief is that with more lines of code, the defect density will increase, however in practicality with more lines of code the defect density decreases.

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/density.png)

#### Relative Efficiency of Testing Methods

|Testing Type|Defects Found per hours|
|------------|-----------------------|
|Regular Use| 0.21|
|Black Box| 0.282|
|White Box|0.322|
|Reading / Inspections|1.057|

#### Classification of Software Failures
- OS Crash
- Program Hang-up
- Program Crash
- Input Problem
- Output Problem
- Failed Required Performance
- Perceived Total Product Failure
- System Error Message
- Service Degraded
- Loss of Data
- Other
- Need to classify correctly otherwise some failures can be found in multiple categories leading to arbitrariness in the measurement process

#### Incident Types
- Failure
- Fault
- Change Request

- **Generic Data** *(Applicable to all incident types)*
  - What (Product Details)
  - Where (Where is it? Location?)
  - Who (Who found it?)
  - When (When did it occur? Time?)
  - What (End Result? What was observed?)
  - How (How did it occur? Trigger?)
  - Why (Why did it occur? Cause?)
  - Severity/Criticality/Urgency
  - Change

- **Failure Data Example**
  - What:  ABC Software Version 2.3
  - Where: Norman’s home PC
  - Who: Norman
  - When: 13 Jan 2000 at 21:08 after 35 minutes of operational use
  - End result: Program crashed with error message xyz
  - How: Loaded external file and clicked the command Z.
  - Why: <BLANK - refer to fault>
  - Severity: Major
  - Change: <BLANK>

- **Reactive Fault Data Example**
  - What:  ABC Software Version 2.3
  - Where: Help file, section 5.7
  - Who: Norman
  - When: 15 Jan 2000, during formal inspection
  - End result: Likely to cause users to enter invalid passwords
  - How: The text wrongly says that passwords are case sensitive
  - Why: <BLANK>
  - Urgency: Minor
  - Change: Suggest rewording as follows ...

- **Responsive Fault Data Example**
  - What:  ABC Software Version 2.3
  - Where: Function <abcd> in Module <ts0023>
  - Who: Simon
  - When: 14 Jan 2000, after 2 hours investigation
  - What happened: Caused reported failure id <0096>
  - How: <BLANK>
  - Why: Missing exception code for command Z
  - Urgency: Major
  - Change: exception code for command Z added to function <abcd> and also to function <efgh>. Closed on 15 Jan 2000.

- **Change Request Data Example**
  - What:  ABC Software Version 2.3
  - Where: File save menu options
  - Who: Norman
  - When: 20 Jan 2000
  - End result: <BLANK>
  - How: <BLANK>
  - Why: Must be able to save files in ascii format - currently not possible
  - Urgency: Major
  - Change: Add function to enable ascii format file saving

- **Tracking Incidents**
  - Incidents should be traceable to components
    - Units
    - Modules
    - Sub System
    - System
  - Need to know where it came from

### Software Metrics: Practice
- **Purpose**
  - To assess software products
    - Want to measure attributes
      - Reliability, Maintainability, Internal Complexity ...etc.
  - To assess software methods
    - Perform measurement based case studies to find cost-effective software engineering methods
  - To help improve software processes
    - Bulk of Software measurement activities come from here
    - Measurement for cost/effort estimation, quality control ...etc.

#### Goal Question Metric (GQM)
- Clearly defined needs for every measurement
- Process
  - Start with overall goals for the project
  - For each goal, generate questions to see if goals are met
  - For each question, suggest measurements that can help answer them

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/gqm.png)

#### Metrics Plan
- Why (Metrics can address the goal)
- What (Metrics will be collected, how they will be defined, and how they will be analyzed)
- Who (Will do the collecting, who will do the analyzing, and who will see the results)
- How (it will be done - what tools, techniques and practices will be used to support metrics collection and analysis)
- When (In the process and how often the metrics will be collected and analyzed)
- Where (The data will be stored)


#### LOC Measure
- LOC: Number of Lines of Code
- Measure of program size
- Used for
  - **Productivity Assessment** = `LOC / Effort`
  - **Effort Estimation** `Effort = f(LOC)`
  - **Quality Assessment** = `Defects / LOC`

- Similar Ways to Measure  
  - KLOC: Thousands of Lines of Code
  - KDSI: Thousands of Delivered Source Instructions
  - NCLOC: Non-Comment Lines of Code
  - Number of Characters or Number of Bytes

- Problems with LOC Measures
  - Measures length instead of size
  - Can't be used for different languages
  - Only available at the end of development life cycle
- **Length**: Physical size of the product
- **Functionality**: Measures the functions supplied by product to user


#### Complexity
- **Problem Complexity**: Complexity of underlying problem
- **Algorithmic Complexity**: Complexity of algorithm implemented to solve the problem
- **Structural Complexity**: Measures the structure of the software used to implement the algorithm
- **Cognitive Complexity**: Measures effort required to understand the software


#### Halstead's Software Science Metric
- Program (P) is a collection of tokens
- Classified as **Operators** or **Operands**
- `n1` = number of unique operators
- `n2` = number of unique operands
- `N1` = total occurrences of operators
- `N2` = total occurrences of operands
- **Length of P** `N = N1 + N2`
- **Vocabulary of P** `n = n1 + n2`
- **Estimate of N** = `N^ = n1(log(n1)) + n2(log(n2))`
- **Effort to generate P** = `E = (n1 * N2 * N(log(n))) / (2 * n2)`
- **Time to program P** = `T = E/18 seconds`
- Restricted to FORTRAN
- No convincing evidence that these laws are valid
- These were meant for predictive purposes


#### McCabe's Cyclomatic Complexity Metric `v`

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mcCab.png)


#### COCOMO
- **Effort Prediction**

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/cocomo1.png)

- **Time Prediction**

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/cocomo2.png)


#### Regression Based Cost Modeling
  - Use effort and size values from past projects
  - `log(E) = log(a) + b(log(S))`
  - `E = a * S * b`
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/rbcm.png)


#### Albrecht's Function Points
- Count the number of
  - External Inputs
  - External Outputs
  - External Inquiries
  - External Files
  - Internal Files
- Give each of scores a *Weighing Factor*
- **Unadjusted Function Count (UFC)** = Sum of the weighted scores
- **Adjusted Function Count (FP)** = `FP = UFC x TCF`
- **Technical Complexity Factor (TCF)**
  - The Technical Complexity Factor (TCF) is determined by first rating the following 14 factors on a ‘scale’ 0,1,2,3,4,5 where 0 means irrelevant and 5 means essential:


  |Factor|Description|
  |------|-----------|
  |F1   |Reliable back-up and recovery|      
  |F2   |Data communications|
  |F3   |Distributed functions|              
  |F4   |Performance|
  |F5   |Heavily used configuration|         
  |F6   |On-line data entry|
  |F7   |Operational ease|                   
  |F8   |On-line update|
  |F9   |Complex interface|                  
  |F10  |Complex processing|
  |F11  |Reusability|                         
  |F12  |Installation ease|
  |F13  |Multiple sites|                      
  |F14  |Facilitate change|
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/ycf.png)

- **Productivity** = `FP / Person Months Effort`
- **Quality** = `Defects / FP`
- **Effort Predication** = `E = f(FP)`

#### SEI Capability Maturity Model
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/SEI_CMM.png)

### Software Metrics: Framework
- **Measurement**: Process of empirical objective assignment of numbers to entities in order to characterize a specific attribute
- **Entity**: An object or event
- **Attribute**: A feature or property of an entity
- **Objective**: Measurement process must be based on a well defined rule whose results are repeatable
- Avoid mistakes in measurement!
  - Specify both entity and attribute
  - Entity must be defined precisely
  - Must have reasonable, intuitive understanding of attribute before proposing a measure

#### Types & Uses of Measurement
- 2 Types
  - **Direct Measurement**
    - Length of Source Code (LOC)
    - Duration of Testing Process (Hours)
    - Number of Defects
  - **Indirect Measurement**
    - Programmer Productivity
    - Defect Density
    - Requirements Stability
- 2 Uses
  - Assessment
  - Prediction
    - Requires a prediction system
    - Consisting of...
      - Mathematical Model
      - Procedures for determining model parameters
      - Procedures for interpreting results

#### Products, Processes & Resources
- **Process**: A software related activity
  - Coding, Testing, Designing ...etc.
- **Product**: An object which results from a process
  - Test plans, Design documents, Source code ...etc.
- **Resource**: An item which is input to a process
  - People, Hardware, Software ...etc.

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/rpr.png)

#### Internal & External Attributes
- `Let X be a product, process or resource`
- **External Attributes**: Attributes that are measured with respect to how X relates to its environment
  - Reliability or Maintainability of product
- **Internal Attributes**: Attributes that can be measured in terms of X alone
  - Length or Structure of source code

**Relation Diagram**
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/exfa.png)


### Software Metrics: Measurement Theory & Statistical Analysis
- **Purpose of Measurement Theory**
  - Scientific basis for all types of measurement
  - Used to determine
    - When we have really defined a measure
    - Which statements involving measurement are meaningful
    - What the appropriate scale type is
    - What types of statistical operations can be applied to measurement data


- **Key Components in Measurement Theory**
  - **Empirical Relation System**
    - Relations on entities in the real world
    - Characterize our understanding of the attribute
    - Example: `Fred is TALLER than Joe`


  - **Representation Condition**
    - Real world entities are mapped to a number
    - Preserves all Empirical relations and no new relations are created
    - Example: `M(Fred) > M(Joe) only when Fred is TALLER than Joe`
    ![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/repC.png)

  - **Uniqueness Theorem**
    - Different mappings satisfy the Representation Condition (each one is special)
    - Example: `Measure height in inches, feet, centimeters, meters ...etc.`

- **Meaningful Measurements**
  - Formally a statement involving measurement is meaningful if its truth value is invariant of transformations of allowable scales
  - Example: `Fred is twice as tall as Jane`
    - Meaningful because no matter what unit of measurement is used the truth value of the statement does not change
  - Example: `Temperature in Tokyo is twice that in London`
    - NOT Meaningful because maybe twice in `C` but not in `F`

#### Measurement Scale Types
- Nominal (Least Sophisticated)
- Ordinal
- Interval
- Ratio
- Absolute (Most Sophisticated)

#### Nominal Scale Measurement
- Simplest measurement
- Measurements are organized into different entities
- NO order for the entities
- Example:
  ```
  Measurement = Software Faults
  Can classify them by type of fault
  BUT, NO order on which class of faults is more sever than the other
  ```

#### Ordinal Scale Measurement
- A step above nominal
- Entities can be ordered
- NO arithmetic operations

#### Interval Scale Measurement
- Powerful, but rare in practical use
- Distances between entities
- NO ratios
- Must preserve order and intervals
- Example:
  ```
  Measurement = Timing of Events
  The time between project X starting and now is twice the time between project Y starting and now
  BUT, CAN'T SAY project X started twice as early as project Y
  ```

#### Ratio Scale Measurement
- Ordering, Distance & Ratios of entities
- Arithmetic applicable
- **Zero Element**: Representing total lack of the attribute

#### Absolute Scale Measurement
- Basically counting
- No. of occurrences of X in the entity

#### Validating Measures
- Validation of a software measure is the process of ensuring that the measure is a proper numerical characterization of the claimed attribute
- Example:
	- A valid measure of length of programs must not contradict any intuitive notion about program length
	- If program P2 is bigger than P1 then m(P2) > m(P1)
	- If  m(P1)  = 7 and m(P2) = 9 then if P1 and P2 are concatenated then m(P1;P2) must equal m(P1)+m(P2) = 16
- A stricter criterion is to demonstrate that the measure is itself part of valid prediction system


#### Summary of Scale Types
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/stSum.png)

#### Summary of Statistics
- Arithmetic cannot be used on Nominal and Ordinal data
- Following diagram shows statistic techniques to use based on the scale type

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/meanStat.png)

#### Non-Parametric Techniques
- Software measures cannot be assumed to be normally distributed
- Can use Non-Parametric Techniques
  - Pie Charts
  - Bar Graphs
  - Scatter Plots
  - Box Plots

#### Box Plot Example
- Split data by Median
  - Box Length: `b = u - l`
- Find Median of left side (Lower Quartile `l`)
  - Find Lower Tail = `l - 1.5b`
- Find Median of right side (Upper Quartile `u`)
  - Find Upper Tail = `u + 1.5b`
- Outside the tails are outliers

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/boPlo.png)

#### Scatter Plot Example
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/scaPlo.png)

#### Outlier Example
- Long Module with few errors can be caused by
  - High Quality Code
  - Simple Module
  - Code Reuse
  - Poor Testing
- Only poor testing requires action and is not an acceptable outliers

#### Control Chart Example
- Shows when data is within acceptable bounds
- Use to predict whether action needs to be taken to prevent a problem
- Uses mean, standard deviation and the control limits to make the chart
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/conPlo.png)

### Evaluating Software Engineering Technologies through Measurement
- Measurement is the only true means of establishing the efficiency of a method/tool/techniques
- Quantitative claims must be supported by empirical evidence
- **Cannot rely on anecdotal evidence**

### Software Metrics: Risk & Uncertainty

#### Bayesian Belief Nets (BBNs)
- Used to reason about uncertainty
- Nodes in the graph represent uncertain variables
- Arcs in the graph represent casual or influential relationships between variables
- Each node has a probability table (NPT)

- **Sample Diagram**
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/bbnsb.png)

#### Bayes' Theorem
- `p(A)` = Probability of A (Prior Probability)
- `p(B)` = Probability of B
- `p(A|B)` = Probability of A, given the probability of B (Posterior Probability)
- `p(B|A)` = Probability of B, given the probability of A (Likelihood)
- `p(A|B) = (p(B|A) * p(A)) / (p(B))`

#### Bayes' Propagation
- Applying Bayes' Theorem to update probabilities when new evidence is found
- Make predications even with incomplete data

#### Defect Modeling: Classic Approach
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/dmcs.png)


#### Resource Model: Classic Approach
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/clrm.png)

#### BBNs vs Classical Approach
- **Classical**
  - Mainly regression-based black-box models
  - Predicted_attribute = f(size)
  - Crucial assumptions often hidden
  - Obvious causal factors not modeled
  - Cannot handle uncertainty
  - Cannot be used for real risk assessment
- **BBNs**
  - Provide realistic alternative approach
  - Help risk assessment and decision making in a wide range of applications
  - Model cause-effect relationships, uncertainty
  - Incorporate expert judgement
  - Combine diverse types of information
  - All assumptions visible and auditable
  - Ability to forecast with missing data
  - Rigorous, mathematical semantics
  - Good tool support

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/bbnsb.png)


---
