# Software Quality Quiz 3 Notes


[Week 8 -  Trade offs for Software Quality, Principles of Test Planning and Test Execution](#Lecture8)
<br>
[Week 9 - Software Inspection: Systematic and Code Inspection](#Lecture9)
<br>



<a name="Lecture8"></a>
## Week 8 -  Trade offs for Software Quality, Principles of Test Planning and Test Execution

### Trade Offs & Their Implications
- **Robustness vs. Size**
  - To be robust need error handling and recovery
  - Means extra code a.k.a extra size

- **Make vs. Buy**
  - Might want to use existing code instead of making from scratch
  - Have to deal with existing bugs in platform

- **Feature Parity vs. Platform Disparity**
  - Software usually implemented for multiple platforms (iOS vs. Android)
  - Different platforms have different capabilities, so sometimes some features can't be on both

- **Security vs. Usability**
  - Don't need super extra security for something that doesn't need it
  - Sacrifice less important security depending on how it's meant to be used

- **Memory vs. Performance**
  - Performance is better with more memory
  - Construct software depending on whether platform can handle resource intensive vs. resource constrained

### Software Test Plan
- The Software Test Plan (STP) is designed to prescribe the scope, approach, resources, and schedule of all testing activities.

#### Structure of Software Test Plan ( STP )
- **1 - Introduction**
  - **1.1 Objectives**
    - Scope, Approach, Resources, Schedule. High Level Summary of everything
  - **1.2 Testing Strategy**
    - High Level Test plan for each level of testing
  - **1.3 Scope**
    - Plans for producing scheduled and unscheduled updates to the STP
  - **1.4 Reference Manual**
    - List of referenced sources
  - **1.5 Definitions & Acronyms**
    - Definitions of all terms and agency acronyms

- **2 - Test Items**
  - **2.1 Program Modules**
    - Outline testing for each module
  - **2.2 Job Control Procedures (JCL)**
    - Describe testing for JCL, production, scheduling, control, calls and job sequencing
  - **2.3 User Procedures**
    - Describe testing for user documentation
  - **2.4 Operator Procedures**
    - Describe testing procedures to ensure application can be run

- **3 - Features to be Tested**
  - Identify all software features to be tested and test design specs associated with each feature

- **4 - Features Not to be Tested**
  - Identify all features that are not being tested and why they are not

- **5 - Approach**
  - **5.1 Component Testing**
    - Like Unit Testing, test individual modules to ensure it works properly
  - **5.2 Integration Testing**
    - Like System Testing, test the integration of components together
  - **5.3 Conversion Testing**
    - Ensure all data is converted from old format to new format
  - **5.4 Job Stream Testing**
    - Ensure applications works in the production environment
  - **5.5 Interface Testing**
    - Ensure application operates efficiently and effectively with all interface systems
  - **5.6 Security Testing**
    - Ensure systems control and auditability functions work
  - **5.7 Recovery Testing**
    - Ensure application restart and backup / recovery operate correctly
  - **5.8 Performance Testing**
    - Ensure applications works as customer wanted it to
  - **5.9 Regression Testing**
    - Ensure new changes haven't affected old functions / features
  - **5.10 Acceptance Testing**
    - Ensure system satisfies all criteria laid out by customer
  - **5.11 Beta Testing**
    - Done by customer to see if everything is there before final release

- **6 - Pass/Fail Criteria**
  - **6.1 Suspension Criteria**
    - Criteria used to suspend all or part of the testing activity
  - **6.2 Resumption Criteria**
    - Criteria that must be met before resuming testing activities after suspension
  - **6.3 Approval Criteria**
    - Conditions that must be met to approve test results

- **7 - Testing Process**
  - **7.1 Test Deliverables**
    - Deliverables from test process: input/output data, logs, summary
  - **7.2 Testing Tasks**
    - Tasks needed to prepare and perform testing activities
  - **7.3 Responsibilities**
    - Identify groups responsible for the following during a test activity
      - Managing, Designing, Preparing, Executing, Witnessing, Checking, Resolving
  - **7.4 Resources**
    - Identify resources allocated for testing tasks
  - **7.5 Schedule**
    - High level schedule for each testing task

- **8 - Environmental Requirements**
  - **8.1 Hardware**
    - Hardware and Network requirements for testing activities
  - **8.2 Software**
    - Software requirements for testing activities
  - **8.3 Security**
    - Security and Asset Protection for testing activities
  - **8.4 Tools**
    - Special software tools, techniques and methodologies and the purpose of each for testing
  - **8.5 Publications**
    - Documents and publications to support testing activities
  - **8.6 Risks and Assumptions**
    - Constraints on testing activities and risks with each testing task

- **9 - Change Management Procedures**
  - STP change management process
    - Change Initiation
    - Change Review
    - Change Authorization

- **10 - Plan Approvals**
  - Identify plan approvers

### Test Execution
- Begin executing test plan after delivering the **Alpha Build**
  - Build that they feel is ready for release
- Process
  - 1st Iteration: Focuses on new functionality (compared to last round of testing)
  - Regression Test: Make sure new changes didn't affect old stuff
    - Re run all old test cases and new ones
    - At least 2 regression tests for any software project

---



<a name="Lecture9"></a>
## Week 9 - Software Inspection: Systematic and Code Inspection

### Inspection
- A formal review of a work product by peers
  - Used to detect defects early in the development life cycle
- **Best Known Method** for  increasing quality
- Inspections are used to find defects

### Defects
- A defect is a deviation from specific or expected behavior
- Any defect found is a defect
  - Not open to discussion
  - Based on opinion of the person doing the review
- Not all defects are bugs

### Review Methods
- **Presentation**
  - Present idea or proposal
- **Walkthrough**
  - Technical presentation of work
- **Inspection**
  - Formal review by peers

### Defect Detection Methods
- **Buddy**
  - Developers work in pairs
- **Testing**
  - Formal Testing
- **Inspection**
  - Formal review by peers

### Typical Inspection Process
- Planning
  - 45 mins
- Prep
  - 15 - 120 mins
- Log Defects
  - 60 - 120 mins
- Rework
- Follow Up

#### Roles
- Moderator
- Inspectors
- Scribe
- Work Owner

#### Owner Planning
- Owner decides what code to review
- Includes
  - Relevant Requirements
  - Common Errors List
    - Provided by moderator (specifics are added by owner)
  - Copy of Code listing Everyone
    - Send code few days before inspection

#### Preparation
- Inspectors need to have the materials required to inspect in advance
- Need to complete a defect log
- Rule of Thumb - Timing Estimate
  - 2 hours for 10 full pages of text
- Lots of projects means can't do detailed inspection on each one
  - Need to compromise and do just enough that it is useful
- Process
  - Everyone prepares by examining code
  - Owner will provide brief walkthrough
  - Scribe will log defects in real time after the walkthrough

#### Walkthrough
- Pre - Walkthrough
  - Owner sends code and relevant docs
  - Inspector prepare by inspecting code and documenting defects

- During - Walkthrough
  - Owner provides walkthrough for code
  - Inspectors search for defects
  - Round-Robin where each inspector describes a defect found

#### Defect Logging
- Performed by the scribe
  - Allows owner to concentrate on other tasks
- Moderator leads meeting and facilitates process
- Focus is finding defects
  - Categorize as High, Medium, Low
  - Brief Description ~ 7 words or less

|Severity: High / Medium / Low|Location|Description|
|-----------------------------|--------|-----------|
|1|||
|2|||
|3|||
|4|||
|5||||

#### Casual Analysis Meeting
- Brainstorm on the root cause of specific defects
  - Meeting is to support continuous improvement
  - Can help future defects from occurring

#### Rework
- Addresses defects found during the logging process
- Performed by product owner
- All defects are addressed
  - Doesn't mean all of them are fixed

#### Follow Up
- Work product is redistributed for review
- Unfixed defects are reported back to the team

### Code Review
- Special inspection where the team examines a sample of the code and fixes defects
  - Can make it more readable
  - Can improve performance
- Candidates for a code review
  - Tricky algorithms
  - Difficult API or Library to work with
  - Inexperienced coder
  - New programming technique is used

### Code Review Checklist
1. Clarity
  - Is it easy to understand?
  - Can it be refactored to make it clearer?
2. Maintainability
  - Well commented and documented?
3. Accuracy
  - Does the code do what it needs to do?
4. Readability & Robustness
  - Can it handle abnormal conditions
  - Does it fail "gracefully"
5. Security
  - Is it vulnerable to unauthorized access?
6. Scalability
  - Does the code allow for growing user base?
7. Reusability
  - Can it be made general? Reused in other applications?
8. Efficiency
  - Does it make good use of memory and stuff?
  - Can it be optimized?

### Automated Code Review
- Reduces cost of manual code reviews
- Fast, consistent, repeatable

### Gerrit & Jenkins
- Code Review tools
- Reviewers receive email asking them to review the change in code
- Can see changes side by side (like in github desktop mode)
- Can add comments to the code through gerrit Web UI
- Connect with Git
  - `git checkout -b change-4` - Switch to new Branch
  - `git fetch gerrit refs/changes/04/4/1` - Fetch from gerrit repo
- Changes require `+2` to be submitted
- Reviewers can give
  - `-1` bad
  - `0` - can be better
  - `+1` - good

### Gerrit Flow
- Developer pushes to gerrit
- Code gets approved in gerrit then is pushed to repo
- Code is downloaded by other developres
- Process
  - Create branch
  - Do work
  - Push to gerrit
  - Review
  - Fix if needed
  - Upstream to repo if approved



---
