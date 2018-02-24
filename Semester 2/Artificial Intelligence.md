# Introduction to Artificial Intelligence

## Table of Contents

[Lecture 1](#Lecture1)
<br>
[Lecture 2](#Lecture2)
<br>
[Lecture 3](#Lecture3)
<br>
[Lecture 4](#Lecture4)
<br>


<a name="Lecture1"></a>
## Lecture 1

### Artificial Intelligence
- **Definitions**
  - The synthesis and analysis of computational agents that act intelligently
    - **Agent**: Something that acts in an environment
  - Characteristics of an Intelligent Agent
    - Actions are appropriate for it's goals and circumstances
    - Flexible to changing environments and goals
    - Learns from experience
    - Makes appropriate choices given perceptual and computational limitations
- **Examples**
  - **Organizations**: Microsoft, Al Qaeda, Government, CS Department
  - **People**: Teacher, Stock Trader, Engineering, Farmer, Waiter
  - **Devices**: Thermostat, UI, Airplane, Autonomous Car, Game
  - **Animals**: Dog, Mouse, Bird, Insect
- **Goals**
  - **Scientific Goal**: Understand the principles that make intelligent behavior possible in natural or artificial systems
    - Analyze natural and artificial agents
    - Formulate and test hypotheses about what it takes to construct intelligent agents
    - Design, Build, Experiment with computational systems that perform tasks that require intelligence
  - Engineering Goal: Design useful, intelligent artifacts

### Agents
- Agents have
    - Abilities
    - Goals / Preferences
    - Prior Knowledge
- Agent / Environment Interactions
  - Agent performs actions on environment
  - Agent makes observations about the environment
    - Current observations
  - Agent has past experiences with the environment
    - Past observations
- Example
  - Teacher
    - **Abilities**: Present new concepts, Prepare tests, Explain concepts
    - **Goals**: Particular knowledge, Skills, Social skills
    - **Prior Knowledge**: Subject material, Teaching strategies
    - **Observations**: Test results, Facial expressions
    - **Past Experiences**: Prior test results, Effects of teaching strategies
- Types of Agent Reasoning
  - **Single Agent Reasoning**: Other agents are part of the environment
  - **Multiple Agent Reasoning**: An agent reasons strategically about the reasoning of other agents
  - Agents can have their own goals
    - Cooperative
    - Competitive
    - Goals independent of each other


### Dimensions
- Research proceeds by making assumptions that simplify the problem, and then gradually reducing the assumptions
- Each time an assumption is made, it adds a dimension of complexity
  - Multiple values in a dimension (Range: Simple to Complex)
  - Simplifying assumptions can be relaxed in various combinations

### Modularity
- Levels of Modularity
  - Model with one level of abstraction = Flat
  - Model with interacting modules, that can be understood separately = Modular
  - Model with modules that are (recursively) decomposed into modules = Hierarchical
- Flat representations are adequate for simple systems
- Complex biological systems / Computer systems are all hierarchical
- Flat = Continuous or Discrete
- Hierarchical is usually hybrid of both

### Succinctness and Expressiveness
- Modern AI is about finding compact representations and exploiting it for computational gain
- Agents can reason in terms of
  - **Explicit States**
    - A state is one way the world could be
  - **Features / Propositions**:
    - Can be described using features
    - n binary features represent 2^n states
  - **Individuals & Relations**:
    - Every tuple of individuals have a relationship and each of these relationships have a feature
    - Agents can reason without knowing the individuals or if there are infinitely many individuals

### Planning Horizons
- How far the agent looks into the future when making a decision
  - **Static**: World does not change
  - **Finite Stage**: Agent reasons about a *fixed** finite number of time steps
  - **Indefinite Stage**: Agent reasons about a finite, but not predetermined number of time steps
  - **Infinite Stage**: Agent plans for going on forever

### Uncertainty
- 2 Dimensions for uncertainty, each dimension can have
  - **No Uncertainty**: Agent knows what's true
  - **Disjunctive Uncertainty**: Set of states that are possible
  - **Probabilistic Uncertainty**: A probability distribution over the worlds

#### Probability in Uncertainty
- Agents must act even when uncertain
- Predictions are needed
  - Definitive Predictions: *You will be run over tomorrow*
  - Disjunctions: *Be careful or you will be run over*
  - Point Probabilities: *Probability that you will be run over tomorrow is 0.002 if you are careful and 0.05 if you are not*
  - Probability Ranges: *You will be run over with the probability in the range of [0.001, 0.034]*
- Agents that use probabilities > Agents that do not
- Probabilities can be learned from data / prior knowledge

#### Uncertain Dynamics
- Given an initial state and action, Can the resulting state be predicted?
  - **Deterministic**: The resulting state is determined from the action and the initial state
  - **Stochastic**: There is uncertainty about the resulting state

#### Sensing Uncertainty
- Given observations, can the agent determine the state?
  - **Fully Observable**: The agent can observe the state of the world
  - **Partially Observable**: There are a number of possible states given the agent's observations

### Goals
- **Achievement Goal**: A goal to achieve
  - Can be a complex logical formula
- **Complex Preferences**: May involve tradeoffs between things that are needed or wanted
  - **Ordinal** = Only order matters
  - **Cardinal** = Absolute Values & Order matter

### Rationality
- **Perfect Rationality**: Agent can make the best course of action without having to worry about limited computational resources
- **Bounded Rationality**: Agent must make good decisions based on perceptual, computational and memory limitations

### Dimension Interaction
- Partial observability makes multi-agent and indefinite horizon reasoning more complex
  - Harder to reason without full observation
- Modularity interacts with uncertainty and succinctness
  - Some levels may be fully observable and some partially
- Three values of dimension that make reasoning easier for the agent
  - Hierarchical
  - Individuals and relations
  - Bounded Rationality

### Four Example Application Domains
- Autonomous Delivery Robot
  - Roams around office environment doing small deliveries
- Diagnostic Assistant
  - Helps troubleshoot problems and suggest repairs
- Intelligent Tutoring System
  - Teaches students in some subject area
- Trading Agent
  - Buys goods and services on your behalf

### Domain Tasks
- Modeling Environment
  - Build models of physical environment
- Evidential Reasoning
  - Given observations, determine what the world is like
- Action
  - Given model of world and goal, determine what to do
- Learning from Past Experiences
  - Learn about specific case and population of cases

### Representations
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Representations.png)

- Representations
  - Should be rich enough to express knowledge needed to solve problem
  - As close to the problem as possible
  - Should be changeable, to accommodate efficient computation
    - Point out areas that can be exploited for computational gain
    - Able to trade off between accuracy and computation time/space
  - Acquired from people, data, past experiences

### Solutions
- Optimal
  - Best solution
- Satisfying  
  - Good enough solution
- Approximately Optimal
  - Close to the best theoretically possible solution
- Probable
  - What is likely going to end up being the solution

### Symbols
- Meaningful pattern that can be manipulated
- **Symbol System**
  - Creates
  - Copies
  - Modifies
  - Destroys
- **Physical Symbol System Hypothesis**
  - Has necessary and sufficient means for general intelligent action
- 2 levels of abstraction
  - Knowledge Level
    - About the agent's external world
    - Is in terms of what agent knows and what agent's goals are
  - Symbol Level
    - About what an agent uses to implement the knowledge level
    - Is in terms of agent's reasoning

### Mapping from Problem to Representation
- Choosing abstraction level
  - High Level description is easier for human
  - Low level description is more accurate but more difficult to reason with
  - Can use multiple levels of abstraction
- Reasoning & Acting
  - Design Time Reasoning & Computation
    - Carried out by designer of agent
  - Offline Computation
    - Done by agent before it acts
  - Online Computation
    - Done by agent after receiving information and before acting

---

<a name="Lecture2"></a>
## Lecture 2

### Agent Systems
- Consists of
  - Agent
  - Environment
- Agent receives stimuli from environment
- Agent carries out actions in the environment

### Agent System Architecture
- Agent consists of
  - Controller (Receives percepts from the body)
  - Body (used to interact with environment)
- Body consists of
  - Sensors (Interpret Stimuli)
  - Actuators (Carry out actions)

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Agent.png)

- Body uses sensors to interpret stimuli and send it to controller which then sends commands to the body.

### Agent Functions
- T = Set of time points
- **Percept Trace**
  - Sequence of all past, present, future percepts received by controller
- **Command Trace**
  - Sequence of all past, present, future commands output by the controller
- **Transduction**
  - Function from percept traces to command traces
  - It is *casual* if command trace up to time `t` depends only on percept trace up to time `t`
- **Controller**
  - Implementation of a casual transduction
- Agent History at time `t` is a sequence of
  - Past & Present percepts
  - Past Commands
- A casual transduction specifies a function from an agent's history at time `t` into its action at time `t`

### Belief States
- Agent does not have access to entire history
  - Only what it can remember
- Memory / Belief State of an agent at time `t`
  - Encodes all of the agent's history that it has access to
- Belief State encapsulates information about its past that can be used for current and future actions
- Controller must decide the following
  - What to do
  - What to remember
  - How to update memory

### Controller

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Controller.png)

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Controller_Functions.png)

- For a discrete time controller implements
  - Belief State Function `remember(beleif_state, percept)`
    - returns the next belief state
  - Command Function `command(memory, percept)`
    - returns the command for the agent

```
Example: Snack buying agent that ensures you have a supply of chips

Percepts: Price, Number in Stock
Action: Number to Buy
Belief State: Average
Controller: If price < (0.9 * average) & instock < 60
              Then Buy 48
            Else If instock < 12
              Then Buy 12
            Else
              Buy 0

Belief State Transition Function
  average := average + (price - average) * 0.05


```

### Hierarchical Control
- Better to implement intelligent agents rather than 3 independent modules
- Each controller sees the controllers below as virtual bodies
  - They can get percepts from and sends commands to these bodies
- Lower level controllers
  - Run faster, react quicker
  - Deliver simple view of world to higher level controllers

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Hierarchical.png)

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/functions_1.png)

- Memory Function `remember(memory, percept, command)`
- Command Function `do(memory, percept, command)`
- Percept Function `higher_percept(memory, percept, command)`


### Delivery Robot Example
- 3 actions
  - Left
  - Right
  - Straight
- Can be given a plan
  - Consisting of locations where the robot needs to turn
- Whisker sensor
  - Can detect objects when whisker hits it
  - Robot can identify location of objects this way

#### Decomposition

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/decomposition.png)

#### Middle Layer

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/middleLayer.png)

```
Middle Layer Pseudocode

given timeout and target pos:
  remaining ← timeout
  while not arrived() and remaining 6= 0
    if whisker sensor = on
      then steer := left
    else if straight ahead(rob pos, robot dir, target, pos)
      then steer := straight
    else if left of (rob pos, robot dir, target, pos)
      then steer := left
    else steer := right
    do(steer)
    remaining ← remaining − 1
tell upper layer arrived()

```

#### Top Layer
- Given a plan
  - Consists of named locations
- Tells middle layer goal position of current location
- Needs to remember the goal position and the locations that still need to be visited
- When middle layer signals that robot arrived
  - Top layer takes next location from positions to visit and there is a new goal position

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/topLayer.png)

```
Top Layer Pseudocode

given plan:
  to do ← plan
  timeout ← 200
  while not empty(to do)
    target pos := coordinates(first(to do))
    do(timeout, target, pos)
    to do := rest(to do)

```

### Agent Belief State
- Agent decides what to do based on its belief state and what it observes
- Purely reactive agent does NOT have a belief state
- A dead reckoning agent doesn't perceive the world
  - Also don't work very well in complicated domains
- Useful for belief state to be a model of the world

----

<a name="Lecture3"></a>
## Lecture 3

### Directed Graphs
- Consists of
  - A set of `N` nodes
  - A set of ordered pair of nodes called `arcs`
- **Neighbors**: Two nodes are neighbors if there is arc from one node to another
- **Path**: Is a sequence of nodes
- **Length**: Length of a path `n0 - nk` = k
- Given set of start nodes and goal nodes
  - **Solution** is a path from start to goal

### Graph Searching
- Given a graph, start nodes and goal nodes
  - Incrementally explore paths from the start node
- Maintain a *frontier* of paths from the start node that have been explored
- Frontier expands into unexplored nodes until goal node is found
  - This frontier expansion defines the search strategy

```
Graph Search Algorithm

Input: Graph, Set of Start Nodes, Boolean Test for Goal Node

frontier := {hsi : s is a start node};

while frontier is not empty:
  select and remove path < n0, . . . , nk > from frontier;
  if goal(nk)
    return < n0, . . . , nk >;
  for every neighbor n of nk
    add < n0, . . . , nk , n > to frontier;
end while

```

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/GraphSearch.png)

### Depth First Search
- Treats frontier as a stack
- Always selects one of the last elements added to the frontier
- If the list of paths on the frontier is [p1,p2...]
  - p1 is selected
  - Paths that extend from p1 are added to the front of the stack
  - Once all paths explored
  - p2 is selected
- Basically asks one neighbor if it has path to goal
  - That neighbor asks all its children and responds (yes or no)
  - Then asks next neighbor and so on
  - Goes deep before going across

### Breadth First Search
- Treats frontier as a queue
- Always selects one of the earliest elements added to the frontier
- If the list of paths on the frontier is [p1,p2...pr]
  - p1 is selected
  - p1's neighbors are added to the end of the queue (after pr)
  - p2 is selected next
- Basically asks neighbors before asking their children
  - Goes across before going deep


[DFS & BFS Explained (Simple)](https://www.youtube.com/watch?v=zaBhtODEL0w)


### Lowest Cost First Search
- Costs can be associated with arcs
  - Numbers on the lines connecting neighbors
- Optimal solutions has minimum cost
- Each step
  - Select a path from frontier with lowest cost
  - Frontier is a priority queue ordered by path cost
  - If costs are all equal then BFS

### Heuristic Search
- Don't ignore the goal when selecting paths
- **Heuristics**: Extra knowledge that can be used to guide the search
- `h(n)` is an estimate of the cost of the shortest path from node n to goal node
  - Needs to be efficient
  - Can be extended to paths `h(< n0,...,nk >) = h(nk)`
  - **Underestimate**: If there is no path from node n to goal node
  - **Admissible Heuristic**: Non-negative function that is an underestimate of the actual cost of a path to a goal
- Does not guarantee best solution
  - Guarantees good solution in *reasonable time*

### Best First Search
- Select the path whose end is closest to a goal according to the heuristic function
- Selects a path on the frontier with minimal `h` value
  - Frontier is a priority queue ordered by `h`


### A* Search



---




<a name="Lecture4"></a>
## Lecture 4




----
