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
- Uses both path cost & heuristic values
- `cost(p)` is the cost of path `p`
- `h(p)` is the estimate cost from `p` to goal
- `f(p) = cost(p) + h(p)` which estimates total path cost from start to goal via `p`
- Treats frontier as a priority queue ordered by `f(p)`
  - Mix of lowest-cost-first and best-first searches
- Selects nodes from frontier such that...
  - Selected node has the lowest estimate distance from start to goal
  - The path goes through the selected node
- A* finds the optimal solution **if** ...
  - Branching factor is finite
  - All arc (path between two nodes) costs are above a value `e` and `e` > 0
  - `h(n)` is an admissible heuristic

#### Why is A* Admissible
- If a path `p` is selected from a frontier this means that it was selected because it's `f(p)` was better than the other paths SO...
  - `cost(p) <= f(p')` SO `cost(p) <= cost(p') + h(p')`
  - && `cost(p') + h(p') <= cost(p")`
- This proves that `cost(p)` will be less than any other subsequent paths


### Summary of Search Strategies
|Strategy|Frontier Selection|Complete|Halts|Space|
|--------|------------------|--------|-----|-----|
|Depth First|Last node added|No|No|Linear|
|Breadth First|First node added|Yes|No|Exp|
|Heuristic Depth-First|Local Min `h(p)`|No|No|Linear|
|Best-First|Global Min `h(p)`|No|No|Exp|
|Lowest-Cost-First|Minimal `cost(p)`|Yes|No|Exp|
|A*|Minimal `f(p)`|Yes|No|Exp|

**Complete** = If there is a path to a goal, it can find one (Even on infinite graphs)
**Halts** = On finite graph (Perhaps with cycles)
**Space** = As a function of length of current path

### Cycle Checking
- A searcher can remove a path `p` without removing an optimal solution given that...
  - `p` is a path that ends in a node already on the path

### Multiple Path Pruning (Removing)
- Remove a path to node `n` that the searcher has already found a path to
  - See diagram below

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/MPPrune.png)

### Multiple Path Pruning & Optimal Solutions
- What if a subsequent path to `n` is shorter than the first path to `n`?
  - Remove all paths from frontier that use longer path
  - Change initial segment of paths on frontier to use shorter path
  - Make sure this does not happen. Make sure shortest path is always found first

### Multiple Path Pruning & A*
- Suppose path `p` to node `n` was selected but there is a shorter path to `n`
  - Suppose the shorter path `p'` ends at node `n'`
  - `p` was selected before `p'` so
    - `cost(p) + h(n) <= cost(p') + h(n')`
  - If `cost(n', n)` is the actual cost of path from `n'` to `n` then
    - `cost(p') + cost(n', n) < cost(p)` because `p'` shorter than `p`
  - SO... `cost(n' n) < cost(p) - cost(p') <= h(n') - h(n)`
- To make sure this doesn't happen
  - Ensure that `|h(n') - h(n)|  <=  cost(n', n)`

### Monotone Restriction
- IF heuristic function `h` satisfies the following requirement it is known as a monotone restriction
  - `|h(m) - h(n)|  <=  cost(m, n)` for every arc `<m, n>`

### Direction of Search
- **Forward Branching Factor**: Number of arcs out of a node
- **Backward Branching Factor**: Number of arcs into a node
- Search complexity = `b^n`
  - Use forward or backward search depending on which one has smaller branching factor

### Bidirectional Search
- Search backward from goal and forward from start **at the same time**
- This is better because instead of `b^n` it becomes `2b^n/2`
- Have to make sure the frontiers meet
- Often done like this  
  - One direction uses breadth-first search to build a set of locations that can lead to goal
  - Another location finds paths to these locations

### Island Driven Search
- Find set of islands between start and goal
- The time complexity then becomes `m * b^k/m` vs `b^k`
  - Because `m` smaller problems rather than 1 big one
- Problem is the path must pass through islands
  - Harder to guarantee optimality
- Subproblems are solved using islands
  - **Hierarchy of Abstractions**

### Dynamic Programming
- For a statically stored graph, build a table of `dist(n)`
  - Contains the actual distance of shortest path from `n` to goal
- Can be used locally to determine what to do
- 2 big problems
  - Needs enough space to store graph
  - `dist()` function must be recomputed for each goal

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/dist.png)


### Bounded Depth First Search
- Does regular depth first search but does not exceed a set bound
  - Paths that exceed that bound are not expanded (don't even look at children nodes)
- Explores part of the search graph
- Uses linear space in the depth of the search

### Iterative Deepening Search
- Procedure
  - Start with bound `b = 0`
  - Do a bounded depth first search with bound `b`
  - If solution is found, return it
  - If not, increment `b` and repeat
- Complexity

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/idC.png)

### Depth First Branch-and-Bound
- Want to find a single optimal solution
  - Bound is set to be the cost of the lowest-cost path found so far
  - If a worse path is found then remove it
  - If a better path is found then make it the new best and update bound
  - Upon completion, will have a single optimal solution

#### Initializing Bound for Depth First Branch-and-Bound
- Can be initialized to infinity (very large number)
  - Something so that the first path found will override it
- Can be set to an estimate of the optimal path cost

---


<a name="Lecture4"></a>
## Lecture 4

### Constraint Satisfaction Problem
- CSP is characterized by
  - Variables `V1....Vn`
  - Each variables has associated domains `DV1....DVn`
  - Set of constraints for each variable
  - A solution to CSP is assigning values to each variable that satisfies the constraints

### Generate and Test Algorithm
- A method for solving a CSP
- Exhaustive method
- Tries all possible assignments
- Checks constraints at the end

### Backtracking Algorithm
- A method for solving a CSP
- Assign values to variables one at a time
- Evaluate each constraint as you add variables
- If a partial assignment violates constraints you can skip and not have to do full assignment because that will also violate

**Partial Assignment**: Assign values to some variables in a set
  - Ex: V1 = 2, V2 = 3, V3 = 7, V4, V5, V6
  - Can stop if v1, v2, or v3 already violate constraint

**Full Assignment**: Assign values to all variables in a set
  - Ex: V1 = 2, V2 = 3, V3 = 7, V4 = 9, V5 = 8, V6 = 4

### CSP & Graph Searching
- Parent node is empty
- All other nodes are variables
  - Each set of child nodes for a given parent is the domain of a variable
- Follow the path as long as it follows the constraint
- See picture below for clarity

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/cspTree.png)

### Consistency Algorithm
- Variable is **domain consistent** if none of the values in the domain violate a constraint

### Constraint Network
- Oval
  - Represents variable
  - Domain of values for each variable node
- Rectangle
  - Represents constraint
- Arc from each variable to its respective constraints

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/constraintNetwork.png)

### Arc Consistency
- An arc is **arc consistent** if for each value `x` there is a value y such that the constraint linking `x` and `y` is satisfied
- A network is **arc consistent** if all the arcs are consistent
- If there is a value in the domain `x` for which there is no corresponding `y` to satisfy the constraint then remove that `x` value to make the arc consistent

### Arc Consistency Algorithm
- Consider arcs one by one so they make each other consistent
- Only need to re-check an arc if domain changes
- To find solution when network is arc consistent
  - If domain has more than one element
    - Search
    - Split domain in half and recursively solve
- When network is consistent only 3 possible outcomes
  - One domain is empty = **No Solution**
  - Each domain has a single value = **Unique Solution**
  - Some domains have more than one value = **There may or may not be a solution**

### Hard & Soft Constraints
- Values assigned to a variable that...
  - Satisfies a set of constraints
    - Satisfiability Problems
    - **Hard Constraints**
  - Minimizes some cost function
    - Each assignment of value to variable has a cost
    - Optimization Problems
    - **Soft Constraints**

### Local Search
-

### Greedy Descent
-

### Complex Domains
- For small domains, neighbors of an assignment can choose other values for the variables
- For large domains, neighbors of an assignment should choose adjacent values for the variables
- For continuous domains, **Gradient Descent** changes variables proportionally to the gradient of the heuristic function in that direction

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/gradient.png)

### Randomized Greedy Descent
- **Random Steps**: Move to a random neighbor
- **Random Restart**: Reassign random values to all variables

### Stochastic Local Search
- Mix of
  - **Greedy Descent**: Move to a lowest neighbor
  - **Random Walk**: Taking some random steps
  - **Random Restart**: Reassigning values to all variables

### Random Walk
- When choosing best variable-value pair, sometimes do it randomly
- When selecting variable then value
  - Sometimes choose variable that participate in the most conflicts
  - Sometimes choose variable that participate in any conflict
  - Sometimes choose anything
- Sometimes best value, sometimes random value

### Variant: Simulated Annealing
- Procedure
  - Pick a variable at random
  - Pick a new value at random
  - If improvement, take it
  - If not improvement, take it based on a probability `T`

- Probability of moving from `n` to `n'`
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/moveP.png)

- Probability of accepting a change
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/tableP.png)

### Tabu Lists
- Prevents cycling
- Maintain list of the last `k` assignments
- Don't allow assignment if it's on the list
- If `k = 1` then cannot assign to same value as chosen variable

### Parallel Search
- *A total assignment is called an* **individual**
- Maintain a population of `k` individuals instead of one
- At each stage, update the individuals in the population
- If individual = solution, report it

### Beam Search
- Like Parallel Search, but choose `k` best individuals out of the neighbors
- If k = 1, greedy descent
- When k = infinity, breadth-first search

### Stochastic Beam Search
- Like Beam Search, but uses probability to choose `k` best individuals
- Probability of being chose depends on heuristic value
  - Reflects fitness value of individual
- The fittest ones survive

### Genetic Algorithms
- Like Stochastic Beam Search, but pairs of individuals are combined to create offspring
- Each generation
  - Randomly choose pairs where the fitness values are higher (more likely to be chosen)
  - Perform cross-over (Form two offspring each, taking different parts of the parents)
- **Crossover**
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Crossover.png)

### Variable Elimination
- Eliminate variables one-by-one passing the constraints to the neighbor



----
