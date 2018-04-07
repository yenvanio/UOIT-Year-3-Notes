# Software Quality Quiz 3 Notes


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


---

<a name="Lecture1112"></a>
## Week 11 & 12 - Software Metrics

### Software Quality Metrics Basics
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

- **Relative Efficiency of Testing Methods**

|Testing Type|Defects Found per hours|
|------------|-----------------------|
|Regular Use| 0.21|
|Black Box| 0.282|
|White Box|0.322|
|Reading / Inspections|1.057|

- **Classification of Software Failures**
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

- **Incident Types**
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

### Software Metrics Practice
- **Purpose**
  - To assess software products
    - Want to measure attributes
      - Reliability, Maintainability, Internal Complexity ...etc.
  - To assess software methods
    - Perform measurement based case studies to find cost-effective software engineering methods
  - To help improve software processes
    - Bulk of Software measurement activities come from here
    - Measurement for cost/effort estimation, quality control ...etc.

- **Goal Question Metric (GQM)**
  - Clearly defined needs for every measurement
  - Process
    - Start with overall goals for the project
    - For each goal, generate questions to see if goals are met
    - For each question, suggest measurements that can help answer them

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/gqm.png)

- **Metrics Plan**
  - Why (Metrics can address the goal)
  - What (Metrics will be collected, how they will be defined, and how they will be analyzed)
  - Who (Will do the collecting, who will do the analyzing, and who will see the results)
  - How (it will be done - what tools, techniques and practices will be used to support metrics collection and analysis)
  - When (In the process and how often the metrics will be collected and analyzed)
  - Where (The data will be stored)


- **LOC Measure**
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


- Complexity
  - **Problem Complexity**: Complexity of underlying problem
  - **Algorithmic Complexity**: Complexity of algorithm implemented to solve the problem
  - **Structural Complexity**: Measures the structure of the software used to implement the algorithm
  - **Cognitive Complexity**: Measures effort required to understand the software


- **Halstead's Software Science Metric**
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


- **McCabe's Cyclomatic Complexity Metric `v`**

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mcCab.png)


- **COCOMO**
  - Effort Prediction
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/cocomo1.png)
  - Time Prediction
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/cocomo2.png)


- **Regression Based Cost Modeling**
  - Use effort and size values from past projects
  - `log(E) = log(a) + b(log(S))`
  - `E = a * S * b`
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/rbcm.png)


- **Albrecht's Function Points**
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
      - F1   Reliable back-up and recovery      
      - F2   Data communications
      - F3   Distributed functions              
      - F4   Performance
      - F5   Heavily used configuration         
      - F6  On-line data entry
      - F7   Operational ease                   
      - F8  On-line update
      - F9   Complex interface                  
      - F10 Complex processing
      - F11 Reusability                         
      - F12 Installation ease
      - F13 Multiple sites                      
      - F14 Facilitate change
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/ycf.png)





---





<a name="Lecture12"></a>
## Week 12




----
