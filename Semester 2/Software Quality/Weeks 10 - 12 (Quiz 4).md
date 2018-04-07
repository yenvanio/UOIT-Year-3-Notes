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

-

---





<a name="Lecture12"></a>
## Week 12




----
