# Software Quality Quiz 3 Notes


[Week 6 - Test Automation, Inspections & Reliability Assessment](#Lecture6)
<br>

<a name="Lecture6"></a>
## Week 6 - Test Automation, Inspections & Reliability Assessment

### Software Test Automation
- The activities and efforts that intend to automate engineering tasks and operations in a software test process using well defined strategies and systematic solutions
- Test Automation is not a simple task
  - It is a software development task
  - Need to have some kind of programming background
- Commercial test tools are cheap

### Test Automation Framework
- Test Automation Framework is a set of assumptions, concepts and tools that provide support for automated software testing. This can reduce development and maintenance costs

### Data Driven Testing
- Data focused automation
- User just defines data sets to run tests with
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/ddt.png)

### Keyword Driven Testing
- Users decompose test cases into reusable action keywords
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/kdt.png)

### Hybrid Testing
- Combines best of data-driven and keyword-driven testing
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/hdt.png)

### Framework Components
- **Test Generation**: Tools might create specialized data such as randomized email messages or populate databases etc.
- **System Configuration**: Tools might preserve or reproduce system parameters
- **Test Execution**: Tools might operate the software itself, either simulating a user working through the GUI and using an alternative testable interface
- **Oracles**: Any mechanism by which we detect failure or success. Tools might automatically detect certain kinds of error conditions in a product.
- **Activity Recording & Coverage Analysis**: Tools might watch testing as it happens and retrospectively report what was and was not tested
- **Test Management**: Tools might record test results, organize test ideas or metrics

### Converting Manual Test Cases to Automated
- One or more rounds of manual testing already would be performed on the automated unit testing (AUT).
  - Basically manual test cases exist, and have been executed at least once

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/aa.png)

- **State of the AUT**: Particular state of the background to be set for a certain step to be executed
- **Test Steps**
  - Data Entry (input to AUT)
  - Change of AUT state steps
  - Combination (combination of the above two)
- **Verification & Validation (v&v)**
  - Follow up of testing stage
  - Should not be ambiguous
- **Test Data**
  - Data generated to ensure that the program is running properly
- **Result**
  - Result
- **Post Operations**
  - Clean up, process is done

```
Example of Step by Step Conversion

Step 1.         Precondition, Launch IE with gmail.com URL programmatically
Steps 2 & 7.    Sync Statement. Make sure AUT comes to desired state before next step
Steps 3 & 4.    Data Entry. Hard coded into script (not advisable, but good start)
Step 5.         Change of AUT. Click on sign in (no need for v&v)
Steps 6 & 8.    Comments
Steps 9 & 11.   Conditional Statement. v&v checkpoint, check if login successful
Step 10.        Message box (visibility purposes)
Steps 12 & 13.  These are cleanup activities. Sign out and close browser

```

### Availability vs Reliability
- **Availability**: Does the system give an answer?
  - Matters more when booking seats on aircrafts etc.
- **Reliability**: Is the answer correct?
  - Matters more when using tax software, want correct but its ok if it takes some time to submit the tax return.
  - Ways to measure
    - Counting failures in periodic intervals (cumulative failure count)
    - Failure intensity (number of failures per unit time)
      - `= derivative of cumulative failure count wrt to time `

### Software Reliability
- 2 Definitions
  - Probability of failure free operation of a software system for a specified time & environment.
    - `Example: Probability that a PC runs without crashing for 8 hours is 0.99`
  - Failure intensity is a measure of reliability of the reliability of a system in a given environment.
    - `Example: Air traffic control systems fails once in two years`

### Software Reliability Assessment
- A "survey" which predicts defect density
- **Application Type**: Inherent risks of product and release
- **Project Specific Practices**: Ability to schedule project and manage progress against schedule
- **Software Standards**: Standards & Processes for every phase and development activity
- Categories of Assessment (# of Fielded Defects)
  - `97% - 75%` = More risk than strengths
  - `50%` = Strengths and risk offset each other
  - `25% - 3%` = More strengths than risks

### Patient Monitoring Unit (PMU) - Example
- Requires high reliability
- Reliability Assessment
  - Patient ill, no alarm sounding
  - Bad range permitted
  - Log overflow, no alarm sounding
  - Database incorrect
  - Database failure
  - Undetected database corruption
  - Operating system failure






---
