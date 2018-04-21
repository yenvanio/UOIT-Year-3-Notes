# Software Project Management

## Table of Contents

[Lecture 7 - Risk Management](#Lecture7)
<br>
[Lecture 8 - Resource Allocation](#Lecture8)
<br>
[Lecture 9 - Monitoring & Controlling](#Lecture9)
<br>
[Lecture 10 - Contract Management](#Lecture10)
<br>
[Lecture 11 - Managing People in Software Environments](#Lecture11)
<br>
[Lecture 12](#Lecture12)
<br>


<a name="Lecture7"></a>
## Lecture 7 - Risk Management
- Risks relate to potential future problems, not current problems
- They involve a cause and an effect

### Risk Categories
- **Actors**: Relate to all those involved in the project
  - Risk could be that high staff turnover leads to important project information being lost
- **Technology**: The technology used to implement the project and that is embedded in the project deliverables
  - Risk could be that the technologies selected are not appropriate
- **Structures**: Includes management procedures
  - Risk could be that a group who needs to carry out a particular project task are not informed of a structural need because they are not a part of the project communication network
- **Tasks**: The work to be carried out  
  - Risk could be that the amount of effort needed to carry out the task is underestimated
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm2.png)

### Risk Planning
- **Risk Identification**

|Risk|Risk Reduction Techniques|
|----|-------------------------|
|Personnel Shortfalls|Staffing with top talent <br> Job matching <br> Team Building <br> Training and career development <br> Early scheduling of key personnel|
|Unrealistic time and cost estimates|Multiple estimation techniques <br> Design to cost <br> Incremental development <br> Recording and analysis of past projects <br> Standardization of methods|
|Developing the wrong software functions|Improved software evaluation <br> Formal specification methods <br> User surveys <br> Prototyping <br> Early user manuals|
|Developing the wrong user interface|Prototyping <br> Task analysis <br> User involvement|
|Gold plating|Requirements scrubbing <br> Prototyping <br> Design to cost|
|Late changes to requirements|Change control <br> Incremental development|
|Shortfalls in externally supplied components|Benchmarking <br> Inspections <br> Formal specifications <br> Contractual agreements <br> Quality controls|
|Shortfalls in externally performed tasks|Quality assurance procedures <br> Competitive design etc|
|Real time performance problems|Simulation <br> Prototyping <br> Tuning|
|Development technically too difficult|Technical analysis <br> Cost-benefit analysis <br> Prototyping <br> Training|

- **Risk Analysis and Prioritization**
  - Risk exposure `(RE) = (potential damage) * (probability of occurrence)`
  - In simpler terms: Likelihood x Impact = Risk
  - Probability Impact Matrix
    - X: Probability  
    - Y: Impact
    - Arrange Hazards accordingly
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm3.png)

- **Risk Planning**
  - **Methods to Deal with Risk**
    - **Risk Acceptance**
      - The cost of avoiding the risk may be greater than the actual cost of the damage that might be inflicted
      - *Example: Allowing a risk that is not too costly to manage*
    - **Risk Avoidance**
      - Avoid the environment in which the risk occurs
      - *Example: Buying Off the Shelf application avoids risks with software development*
    - **Risk Reduction**
      - The risk is accepted but actions are taken to reduce its likelihood
      - *Example: Prototypes reduce risk of incorrect requirements*
    - **Risk Transfer**
      - The risk is transferred to another person or organization
      - *Example: Risk of effort estimation can be transferred when negotiating with outside supplier*
    - **Risk Mitigation**
      - We try to reduce the impact if the risk does occur
      - *Example Taking backups to allow rapid recovery in case of data corruption*
  - **Risk Reduction Leverage**
    - `(RE) = (potential damage) * (probability of occurrence`
    - `RRL = (REbefore – REafter) / (cost of risk reduction)`
    - If `RRL` > 1, it would be worth doing
  - **Evaluating Risk to Schedule**
    - Use effort as a financial loss
- **Risk monitoring**

### Program Evaluation and Review Technique (PERT)
- Used to evaluate the effects of uncertainty
- Three estimates are produced for each activity
  - **Optimistic time** `a`: The shortest time that could be realistically expected
  - **Most likely time** `m`: The time we would expect the task to take normally o
  - **Pessimistic time** `b`: The worst possible time
- **Expected Time**
  - `(te) = (a + 4m + b) / 6`
- **Activity Standard Deviation**
  - `(S) = (b – a) / 6`
- **Z Value**
  - `z = (T - te) / S`
  - T would be the target days to completion
- *Example*
  - What would be the expected duration of the chain A + B + C?
    - 12.66 + 10.33 + 25.66
  - What would be the standard deviation for A + B + C?
    - Square Root of (1<sup>2</sup> + 1<sup>2</sup> + 3<sup>2</sup>)
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm4.png)

### Critical Chain Approach
- Estimators add a safety zone to the estimate to account for any difficulties
  - Developers work to the `estimate + safety zone`
  - They tend to start activities late because they can still meet the target date
  - So time is lost

- The safety zone could be used to provide a buffer for late activities
  - The safety buffer in the task duration estimate ends up being extra duration to the project as a whole

- Solution
  1. Ask the estimators for two estimates
      - **Most Likely Duration**: 50% chance of meeting this
      - **Comfort Zone**: Additional time needed to have 95% chance
  2. Schedule all activities using most likely values and starting all activities on latest start dates
  3. Identify the critical chain
  4. Put a project buffer at the end of the critical chain with duration 50% of sum of comfort zones of the activities in the critical chain
  5. Wherever subsidiary chains of activities feed into the critical chain, add a feeding buffer
  6. Duration of the feeding buffer is same as the duration of the project buffer
  7. Wherever there are parallel chains, take the longest and sum those activities

- Executing the critical chain plan
  - No chain of tasks is started earlier than scheduled, but once it has started it is finished as soon as possible
  - This means that the activity following the current one starts as soon as current activity ends even if current activity ends early (known as the relay race principle)
  - Buffers are divided into three zones
    - **Green**: The first 33% (no action required)
    - **Amber**: The next 33% (plan is formulated)
    - **Red**: Last 33% (plan is executed)
---

<a name="Lecture8"></a>
## Lecture 8 - Resource Allocation
- **Activity Schedule**: Indicates start and completion dates for each activity
- **Resource Schedule**: Indicates dates when resources are needed + level of resources
- **Cost Schedule**: Showing accumulative expenditure


### Resource allocation:
- Identify the resources needed for each activity and create a **Resource Requirement List**
- Identify **Resource Types**
- Allocate resource types to activities and examine the **Resource Histogram**
- Assumption: We are dealing with a standard employee with average productivity
  - When we allocate actual people they may be a trainee or an expert and this will affect productivity
 - A short-coming in productivity in an individual might be compensated for by a lower cost

#### Resource Histogram
- The resource histogram helps us identify where the demand for a resource exceeds the supply
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm5.png)

#### Resource Smoothing
- Adding extra weeks to stay within the limit of required staff
- Needed because we employ a constant number of staff on a project
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm6.png)
- To split a task or activity, it has to be on non-critical path
  - Splitting causes an increase task duration so by delaying the start of some tasks, we can uniformly distribute the resources over the total duration of the project

#### Resources Clashes
- When more than one activity is competing for the same limited resource at the same time
- The activities now need to be prioritized to decide who uses the resources when
- Can be resolved by:
  - Delaying some of the activities
  - Taking resource from a non-critical activity
  - Bringing in additional resources (increases cost)

#### Prioritizing Activities
- Resources have to be allocated on an *activty-by-activity* basis
- 2 ways to prioritize
  - **Total Float Priority**: Those with the smallest float have the highest priority
  - **Ordered List Priority**: This takes into account the duration of the activity as well as the float
- **Burman’s Priority List**
  - Shortest critical activities
  - Other critical activities
  - Shortest non-critical activities
  - Non-critical activities with lease float o Non-critical activities

#### Resource Usage
- Need to maximize usage of resources
  - Reduce idle periods between tasks
- Need to balance costs against early completion date
- Need to allow for contingency

#### Allocating Individuals to Activities
- Factors to consider
  - **Availability**
    - This will change over the project as some tasks are completed earlier or later than planned
  - **Criticality**
    - Try to put more experienced staff on critical activities
  - **Risk**
    - Try to put more experienced staff on activities with highest risk
    - Some activities off the critical path can still have risks
  - **Training**
    - Allocating slightly risky activities to develop capabilities or inexperienced staff
  - **Team Building**
    - Identifying people who work well together

### Cost Schedules
  - **Staff Costs**
    - Time sheets are often used to record actual hours spent
    - *Examples: Salary, Holiday Pay, Social Security Benefits, etc.*
  - **Overheads**
    - *Examples: Space Rental, Service Charges, etc.*
  - **Usage Charges**
    - *Examples: Pay as you go Charges*

### Cost Profiles
- Shows how much is going to be spent in each week
  - Important when projects are allocated by financial year or quarter and the project straddles more than one of these periods
- **Accumulative Costs**
  - Used to compare with actual accumulative costs to see if project is likely to meet cost target
- **Balancing Concern**
  - Due to inter-linking of different concerns, project planning needs to be iterative
  - Consequences of decisions need to be carefully assess and plans adjusted accordingly
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm7.png)



---

<a name="Lecture9"></a>
## Lecture 9 - Monitoring & Controlling
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm8.png)

### Responsibilities
- The details relating to the project progress have to originate with the people actually doing the work and then have to be fed up through the management structure
- **Information Overload**: May occur when information passes from the many to the few
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm9.png)

### Assessing progress:
- **Checkpoints**: Predetermined times when the progress is checked
  - **Event Driven**: Check takes place when a particular event has been achieved o
  - **Time Driven**: Date of the check is predetermined
- The higher the management level, the longer the gaps between checkpoints
- **Reporting**: Identify key tasks and break them down into sub tasks. Assess the subtasks as the following
  - Green = on target
  - Amber = not on target but recoverable
  - Red = not on target and recoverable only with difficulty
- **Critical Tasks**: Tasks on the critical path and/or reliant on critical resources
- **Slip Charts**: A Gantt chart with a vertical line through it.
  - Left of the line is completed activities
  - Right of the line is incomplete activities
  - *The more jagged the line, the more activities that are lagging as well as ahead of schedule*

### Getting Back on Track
  - Renegotiate the deadline, and if that is not possible, try to shorten the critical path to get things done more quickly by adding more staff
  - Reconsider activity dependencies:
    - Allowing activities to overlap often increases the risk of quality shortfalls
    - Overlap the activities so that the start of one activity does not have to wait for the completion of another
    - Split activities

### Cost Monitoring
- 2 Scenarios we want to avoid
  - **Behind Time & Under Budget**
    - The originally committed staff have not been deployed so will be within the budget but not on time
  - **On Time & Over Budget**
    - Added more resources to meet the deadline but went over the budget

#### Earned Value Analysis
- **Planned Value (PV) / Budgeted Cost of Work Scheduled (BCWS)**
  - The original estimate of the effort/cost to complete a task
- **Earned Value (EV) / Budgeted Cost of Work Performed (BCWP)**
  - The total of PVs for the work completed at this time
- **Schedule Variance (SV)**
  - `SV = EV - PV`
  - If `SV < 0` then project behind schedule
- **Schedule Performance Indicator (SPI)**
  - `SPI = EV / PV`
  - If `SPI < 1` then project behind schedule
- Earned Values for works started but not yet completed are assigned by:
  - **50/50**: half allocated at start and the other half on completion (proportions of start and end can vary)
  - **Milestone**: current value depends on the milestones achieved
  - **Units Processed**
- **Example**
```
Tasks
     Specify Module: 5 Days
     Code Module:    8 Days
     Test Module:    6 Days

At the beginning of day 20, PV = 19 Days

If @ Day 20 everything but testing done, EV = 13 Days
    SV= EV - PV = 13 - 19 = -6
    SPI = EV/PV = 13/19 = 0.68

SV < 0 OR SPI < 1 = Project behind schedule

```
- **Actual Cost (AC) / Actual Cost of Work Performed (ACWP)**
  - The actual time it took to finish a task
- **Cost Variance (CV)**
  - `CV = EV - AC`
  - If `CV > 0` then project within budget
- **Cost Performance Indicator (CPI)**
  - `CPI = EV / AC`
  - If `CPI > 1` then project within budget
- **Budget At Completion (BAC)**: Current budget allocated to total costs of project
- **Estimate At Completion (EAC)**: Updated Estimate
  - `EAC = BAC / CPI`
- **Time Variance (TV)**: Difference between time when EV should be reached vs when it was actually reached

- **Schedule and Cost Variance**
  - `SV = EV - PV`
  - `CV = EV - AC`
  - If (+) then Good
- **Schedule and Cost Indicator**
  - `SPI = EV / PV`
  - `CPI = EV / AC`
  - If (>1) then Good

### Prioritizing monitoring:
- **Critical Path Activities**: If these are late, the project as a whole will be delayed
- **Activities with no Free Float**: If delayed, dependent activities are also delayed
  - However, project end date may not be directly threatened
- **Activities with Less than a Specified Float**
  - Project execution is dynamic
  - Some will take longer and some will take less time
  - This can cause critical shifting
- **High risk activities**: Large uncertainty about duration of these activities
  - Uncertainty is large if standard deviation is large
- **Activities using Critical Resources**: Some resources are only available for a limited time and if these activities are delayed, the needed resources may become unavailable

### Exception Planning
Changes that could affect users and the business
  - Delivery Date, Scope, and Cost
- An exception report is generated for these changes
- Stages
  1. Write an exception report for sponsors
      - Explains problems and sets out options for resolution
  2. Sponsor selects an option
    - Project manager produces an exception plan implementing the selected option
    - Exception plan is reviewed and accepted/rejected by sponsors/project board

### Example Question
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm10.png)
- What is the `PV` at the end of Tuesday?
  - 250
- What is the `EV` at the end of Tuesday?
  - 170
- What is the `AC` at the end of Tuesday?
  - 200
- Calculate the `SV`, `CV`, `SPI` & `CPI`
  - `SV` = 170 - 250 = -80 ($80 behind where we should be)
  - `CV` = 170 - 200 = -30 (Behind schedule that will cost us $30)
  - `SPI` = 170 / 250 = 0.68 (We are only achieving 68% of the work that should be done)
  - `CPI` = 170 / 200 = 0.85 (We are spending money at an efficiency rate of 0.85)



---

<a name="Lecture10"></a>
## Lecture 10 - Contract Management
Software from external suppliers
  - **Bespoke System**: created specifically for the customer
  - **Off-the-shelf**: bought “as is”
  - **Customer off-the-shelf (COTS)**: a core system is customized to meet the needs of a particular customer

### Contracts
- **Fixed Price Contract**: A fixed price is paid for the whole project
  - **Pros**
    - Known Expenditure
    - Supplied motivated to be cost-effective
  - **Cons**
    - Supplier will increase price to be contingencies
    - Hard to modify requirements
    - Cost of changes after buying the project could be higher
    - Threat to system quality

- **Time and Materials Contract**: Divide the project into smaller tasks and pay different amounts for each task
  - **Pros**
    - Easy to change requirements,
    - Lack of price pressure can assist product quality
  - **Cons**
    - Customer liability - the customer absorbs all the risk associated with poorly-defined or changing requirements
    - Lack of incentive for supplier to be cost-effective

- **Fixed Price per Delivered Unit**: Divide the project into smaller tasks and pay the same price for each task
  - The bigger the project, the higher the cost per function point because there are more technical issues to consider
  - **Pros**
    - Customer understanding of how price is calculated
    - Comparability between different pricing schedules
    - Emerging functionality can be accounted for
    - Supplier incentive to be cost-effective
  - **Cons**
    - Difficulties with software size measurement – may need independent FP counter
    - Changing (requirements: how to measure price for new changes?
- **Example**

|Function Point Count| Function Design cost per FP| Implementation cost per FP| Total cost per FT|
|--|--|--|--|
|Up to 2000|$242|$725|$967|
|2001-2500|$255|$764|$1019|
|2501-3000|$265|$793|$1058|
|3001-3500|$274|$820|$1094|
|3501-4000|$284|$850|$1134|

- What would be the charge for 3,200 FPs?
  - 2000 Fps at $967
  - 500 FPs at $1019
  - 500 FPs at $1058
  - 200 FPs at $1094
- Basically move through the table multiplying cost by how many FPs fall into that category


### Tendering Process
- **Open Tendering**
  - Any supplier can bid in response to the invitation to tender
  - All tenders must be evaluated in the same way
  - Government bodies may have to do this by local/international law
- **Restricted Tendering Process**
  - Bids only from those specifically invited
  - Can reduce suppliers being considered at any stage
- **Negotiated Procedure**
  - Negotiate with one supplier

### Contract Placement Stages

1. **Requirements Analysis**
    - Introduction
    - Description of existing system and current environment
    - Future strategy or plans
    - System requirements
      - Mandatory / Desirable Features
    - Deadlines
    - Additional information required from bidders
2. **Evaluation Plan**
    - Methods could include: Reading Proposals, Interviews, Demonstrations, Site Visits, Practical Tests
    - Need to assess value for money (VFM) for each desirable feature
    - Example: A Feeder file saves data input, 4 hours a month, $20 saved/hr, System to be used for 4 years. If cost is $1000, worth or not?
      - Saved Amount = 4 x 20 x 12 x 4
        - = $3,840
        - So, yes worth.
3. **Invitation to Tender**:
    - Acceptance of bidder’s offer creates a contract
    - Customer may need further information
4. **Evaluation of Proposals**


### Memoranda of Agreement (MoA)
- Customer asks for technical proposals
- Technical proposals are examined and discussed
- Agreed technical solution in MoA
- Tenders are then requested from suppliers based in MoA
- Tenders judged on price
- Fee could be paid for technical proposals by customer

### Contract Checklist
- **Definitions**: The precise meaning of words
- **Form of Agreement**: Could be a sale, lease, or license to use a software (also mentions if license can be transferred)
- **Goods and Services to be Supplied**
- **Timetable of Activities**
- **Payment Arrangement**: Payments may be tied to completion of specific tasks
- **Ownership of Software**: Who owns the software if supplier goes out of business?
- **Environment**: Who is responsible for various aspects of site preparation?
- **Customer Commitments**: providing access, supplying information
- **Standards to be met**

### Contract Management
- Some terms of contract will relate to management of contract, for example:
- Progress reporting
- Decision points (could be linked to release of payments to the contractor)
- Variations to the contract (i.e. how are changes to requirements dealt with?
- Acceptance criteria
---


<a name="Lecture11"></a>
## Lecture 11 - Managing People in Software Environments





---

<a name="Lecture12"></a>
## Lecture 12





---
