# Software Project Management

## Table of Contents

[Chapter 7](#Lecture7)
<br>
[Chapter 8](#Lecture8)
<br>
[Chapter 9](#Lecture9)
<br>
[Chapter 10](#Lecture10)
<br>
[Chapter 11](#Lecture11)
<br>
[Chapter 12](#Lecture12)
<br>


<a name="Lecture7"></a>
## Lecture 7
- Risks relate to potential future problems, not current problems
- They involve a cause and an effect
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/spm1.png)

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
  - 1. Ask the estimators for two estimates
    - **Most Likely Duration**: 50% chance of meeting this
    - **Comfort Zone**: Additional time needed to have 95% chance
  - 2. Schedule all activities using most likely values and starting all activities on latest start dates
  - 3. Identify the critical chain
  - 4. Put a project buffer at the end of the critical chain with duration 50% of sum of comfort zones of the activities in the critical chain
  - 5. Wherever subsidiary chains of activities feed into the critical chain, add a feeding buffer
  - 6. Duration of the feeding buffer is same as the duration of the project buffer
  - 7. Wherever there are parallel chains, take the longest and sum those activities

- Executing the critical chain plan
  - No chain of tasks is started earlier than scheduled, but once it has started it is finished as soon as possible
  - This means that the activity following the current one starts as soon as current activity ends even if current activity ends early (known as the relay race principle)
  - Buffers are divided into three zones
    - Green: the first 33% (no action required)
    - Amber: the next 33% (plan is formulated)
    - Red: last 33% (plan is executed)
---

<a name="Lecture8"></a>
## Lecture 8





---

<a name="Lecture9"></a>
## Lecture 9





---

<a name="Lecture10"></a>
## Lecture 10





---

<a name="Lecture7"></a>
## Lecture 7





---

<a name="Lecture11"></a>
## Lecture 11





---

<a name="Lecture12"></a>
## Lecture 12





---
