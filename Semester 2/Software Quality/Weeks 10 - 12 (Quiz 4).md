# Software Quality Quiz 3 Notes


[Week 10 - Refactoring](#Lecture10)
<br>
[Week 11 - Software Metrics](#Lecture11)
<br>
[Week 12 ](#Lecture12)
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

### Impacts of Refactoring on Quality




---




<a name="Lecture11"></a>
## Week 11 - Software Metrics





---





<a name="Lecture12"></a>
## Week 12




----
