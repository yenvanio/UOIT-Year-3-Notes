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


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Agent.png)


----



<a name="Lecture3"></a>
## Lecture 3




---




<a name="Lecture4"></a>
## Lecture 4




----
