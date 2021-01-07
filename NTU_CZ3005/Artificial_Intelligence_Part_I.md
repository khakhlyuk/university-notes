# Artificial Intelligence Part I

## Intelligent Agents
### What is an agent?
- An **agent** is an entity that
	- **perceives** its environment through sensors (e.g. eyes, ears, cameras, infrared
range sensors)
	- **acts** on its environment through effectors (e.g. hands, legs, motors)
- A **rational agent** is one that does the right thing.
	- **Rational Action:** action that maximises the expected value of an objective performance measure (utility) given the percept sequence to date.
	- Rationality depends on:
		- **Performance** Measure (utility)
		- Prior knowledge about the **Environment**
		- **Actions** that are available
		- Percepts coming through **Sensors**
- An **autonomous agent** does not rely entirely on built-in knowledge about the environment. It adapts to the environment through experience i.e.a *learning*.
- An **agent program** is a function that implements the agent mapping from percepts to actions.

### Types of Environment
- **Accessible (vs Inaccessible):** The agent’s sensory apparatus gives it access to the complete state of the environment.
- **Multi (vs Single) Agent :** Both cooperative and adversary games
- **Static (vs Dynamic):** The environment does not change while an agent is deliberating.
- **Deterministic (vs Stochastic):** The next state of the environment is completely determined by the current state and the actions executed by the agent.
	- **Sensing Uncertainty**: Can the agent fully observe the current state of the world?
	- **Effect Uncertainty**: Does the agent know what the effects of its actions are?
	- **External Uncertainty**: Dynamic unpredictable Environment.
- **Episodic (vs Sequential):** Each episode is not affected by the actions taken in previous episodes.
- **Discrete (vs Continuous):** There are a limited number of distinct percepts and actions.

### Types of Agents
#### Simple Reflex Agent
1. state	<- INTERPET(percept)
2. rule		<- RULE_MATCH(state, rules)
3. action <- RULE_ACTION(rule)

#### Reflex Agents with State (Model-Based)
1. state	<- UPDATE(state, percept)
2. rule		<- RULE_MATCH(state, rules)
3. action <- RULE_ACTION(rule)
1. state	<- UPDATE(state, action)

**Note:** The *state* is a description of the current world environment. It contains all the necessary information to predict the effects of an action and to determine if the state is a goal state.

#### Goal-Based Agents
1. Find the action that will get me closer to the goal state from my current state.
2. Perform that action.

**Note:** A *goal* can be specific (explicit destination), abstract (speed, safety) or numerous.

#### Utility-Based Agents
- There may be many action sequences that can achieve the same goal.
- Which action sequence should the agent take?
	- The one with the maximum utility i.e. lowest cost.

#### Representation and Reasoning
##### Representation
- The Environment:  
	- Possible states  
- How the world works:  
	- Actions: preconditions and effects  
	- Constraints  
	- Causality of events  

##### Reasoning
 - Planning
 - Constraint Satisfaction
 - Answering a Query

## Problem Formulation
### Types of Problems
1. **Single-State Problem**
	- accessible world state (sensory information is available)
	- known outcome of action (deterministic)
2. **Multiple-State Problem**
	- inaccessible world state (with limited sensory information) i.e. agent only knows which set of states it is in
	- known outcome of action (deterministic)
3. **Contingency Problem**
	- limited or no sensory information (inaccessible)
	- limited agent knowledge, action result is not predictable
	- effect of action depends on what is found to be true through perception/monitoring (non-deterministic)
	- problem solving requires sensing during the execution phase
4. **Exploration Problem**
	- no information is known about the world state or outcome of action
	- experimentation is often needed
		- hypotheses as actions, search in the real world
		- *learning* builds the agent's knowledge of states and actions progressively

### Steps
1. Goal Formulation
	- Define and organise objectives (goal states).
2. Problem Formulation
	- Define what states and actions (transitions) to consider.
3. Search for a Solution
	- Find a sequence of actions that lead to a goal state.
	- No Knowledge → Random Search
	- Knowledge → Directed Search
4. Execution
	- Actually carry out the recommended actions.

### Problem Formulation
- **Initial State**
- **Actions** available
- **Successor function** from which State Space can be derived
- **Goal Test**
- **Cost Function** *g(n)*

### Search for Solution
- **Solution**  
	- A path (a sequence of actions) that achieves the goal  
- **Optimal Solution**  
	- Solution with lowest path cost *g(n)*
- **Search Cost**
	- Does the agent find a solution?
	- Is it a good solution? (i.e. with a low path cost)
	- What does it cost to find the solution?
- **Total Cost** of Problem-Solving = *Search Cost* + *Path Cost*
	- Trade-off between finding better solution and finding it quicker.
		- Search for a very long time for an optimal solution.
		- Search for a shorter time for a **good enough** solution.

## Search
- A **search algorithm** explores the state space by generating successors of already-explored states i.e. expanding the states.
- A **search strategy** is defined by picking the order of node expansion. Performance of strategies are evaluated by the following metrics:
	- **Time Complexity:** How long does it take to find a solution?
	- **Space Complexity:** How much memory is needed to perform the search?
	- **Completeness:** Does it always find a solution if one exists?
	- **Optimality:** Does it always find the best (least-cost) solution?

### Performance Evaluation
- Measuring difficulty of an AI problem:
	- **b** - Branching Factor (number of successors of a node)
	- Avg. Branching Factor (Total Branches &divide; Num of Non-Leaf Nodes)
	- **d** - Depth of Shallowest Goal Node
	- **m** - Maximum Length of Any Path in State Space
- Time Complexity
- Space Complexity
- Search Cost
	- time and space complexity
- Total Cost
	- combines the search cost and solution cost (path cost of solution found)

### Search Strategies
- Uninformed Search Strategies
	- use only the information available in the problem definition
		- Breadth-First Search
		- Uniform-Cost Search
		- Depth-First Search
		- Depth-Limited Search
		- Iterative Deepening Search
- Informed Search Strategies
	- use problem-specific knowledge to guide the search
	- usually more efficient

## Uninformed Search
### Variables
- *b*: Max. Branching Factor
- *d*: Depth of Least-Cost Solution
- *m*: Max. Depth of State Space

### Breadth-First Search
- Expand shallowest unexpanded node.
	- Can be implemented using a *FIFO queue*.
- **Time:** *1 + b + b<sup>2</sup> + b<sup>3</sup> + ... + b<sup>d</sup> = **O(b<sup>d</sup>)***
- **Space:** Assuming every node is kept in memory, ***O(b<sup>d</sup>)***.
- **Complete:** Yes
- **Optimal:** Yes, when all steps cost equally

##### When is BFS appropriate?
- Space is not a problem
- It's necessary to find the solution with the fewest arcs
- although all solutions may not be shallow, some are  

##### When is BFS inappropriate?
- space is limited
- all solutions tend to be located deep in the tree
- the branching factor is very large

### Uniform-Cost Search
- Modification of BFS, explore nodes considering edge costs.
- Instead of a *FIFO queue*, use a *Priority queue* with path cost *g(n)* to order the elements.
- BFS = UCS if *g(n)* = *Depth(n)* for all nodes.

### Depth-First Search
- Expand deepest unexpanded node.
	- Can be implemented using a LIFO stack.
	- Backtrack only when no more expansion is possible.
- **Time**: *O(b<sup>m</sup>)*
- **Space**: *O(bm)*
- **Complete**:
	- Infinite-depth Spaces: No
	- Finite-depth Spaces w/ Loops: No
	- Finite-depth Spaces w/o Loops: Yes
- **Optimal**: No

##### Appropriate
- Space is restricted (complex state representation e.g., robotics)
- There are many solutions, perhaps with long path lengths, particularly for the case in which all paths lead to a solution

##### Inappropriate
- Cycles
- There are shallow solutions

### Depth-Limited Search
- Modification of DFS with a cutoff on a max. depth *l* to avoid infinite searching,
- **Time**: *O(b<sup>l</sup>)*
- **Space**: *O(bl)*
- **Complete**: Yes, if *l* &ge; *d*
- **Optimal**: No

### Iterative Deepening Search (IDS)
- Improvement on Depth-Limited Search. Iteratively estimate the max. depth *l* of DLS one-by-one.
- **Time**: *O(b<sup>d</sup>)*
- **Space**: *O(bd)*
- **Complete**: Yes
- **Optimal**: Yes

**Note**: *IDS* is basically the best out of all mentioned above if arc lengths are equal.  
It uses less space then *BFS* and is only b/(b-1) times slower due to exponential
growth of the search tree.  
[Quora: IDS vs BFS](http://tinyurl.com/yyljwgcc)

## Informed (heuristic) Search
- Uninformed search strategies
	- Systematic generation of new states.
	- Do not take into account the goal until they reach it.
	- -> *Inefficiency*
- Informed search strategies
 	- Use problem-specific knowledge to determine which node to expand next.

### Heuristic Function
- **Path Cost Function** ***g(n)***:
	- Cost from initial state to current state *n*.
- **Heuristic Function** ***h(n)***:
	- Estimate of the cost of the shortest (cheapest) path from node *n* to a goal node.
	- Non-negative
	- If *n* is a goal node, then *h(n) = 0*.
	- Depends only on the state at that node.
	- Additional knowledge of the problem is imported to the search algorithm.
- **Admissible Heuristic**
	- ***h(n) &le; h&ast;(n)*** for all *n*.
	- i.e. *h(n)* never overestimates the actual cost of a path through node *n* to the goal.
- **Dominance**
	- *h2* dominates over *h1* if:
		- ***h<sub>1</sub>(n) &le; h<sub>2</sub>(n)*** for every state
		- Both admissible.
	- If no heuristic dominates, ***h(n) = max(h<sub>1</sub>(n), h<sub>2</sub>(n), ... , h<sub>m</sub>(n))*** can be used.
	- The dominant Heuristic is better for search (closer estimate)
- **Heuristic / Search trade-off**
	- There is always a trade-off between spending more time computing
	better heuristic or discovering more (deeper) nodes.
	- Both are important for search efficiency.

### Relaxed Problem
- A problem with fewer restrictions than the original one.
	- Dropping some of the constraints.
	- Ex: Robot can move through walls
- State space graph of the relaxed problem is a supergraph of the original state space.
	- Removal of restrictions creates more edges in the graph.

#### Heuristics from Relaxed Problems
- The cost of an optimal solution to a relaxed problem is an admissible heuristic for the original problem.
	- Relaxed problem adds edges to the state space.
	- Any optimal solution in the original problem is also a solution (non necessary optimal) for the relaxed problem.

### Best First Search
- A generic Informed Search algorithm (example are GBFS, A*)
- Expand most desirable unexpanded node.
	- Use an evaluation function *f(n)* to estimate the cost of each node.
	- Nodes are ordered so that the one with the lowest *f(n)* is expanded first.
	- The choice of *f* determines the search strategy.

### Greedy Best-First Search
- Expands the node that appears to be closest to the goal.
	- Only uses the Heuristic
	- Evaluation Function: *f(n) = h(n)*
- Useful but potentially fallible.
- Time: *O(b<sup>m</sup>)* (Worst Case)
- Space: *O(bm)* (Worst Case)
- Complete: No
- Optimal: No
- With a good heuristic function, the complexity can be reduced substantially.
- **Objective**: **Quick Solution** (but may be suboptimal)

### A* Search
- **Uniform-Cost Search**:
	- *g(n)*: Path cost to reach node *n* from the start node (Past Experience).
	- Optimal & Complete, but inefficient.
- **Greedy Best-First Search**:
	- *h(n)*: estimated cost of the cheapest path from node *n* to goal node (Future Cost).
	- Neither optimal nor complete but relatively more efficient.
- **Combining UCS & GBFS, A* Search**:
	- *f(n) = g(n) + h(n)*
	- *f(n)*: Estimated total cost of the cheapest path through node *n* from start node to goal.  
- **Objective**: **Shortest path** (optimal with admissible heuristic)

#### Complexity of A*
- Time: *O(b<sup>m</sup>)* (Worst Case)
- Space: *O(b<sup>m</sup>)* (Worst Case)
- With a good heuristic, significant savings are still possible compared to uninformed search methods.
- Variants of A* search exist to deal with complexity issues.  

#### Completeness and Optimality
- Complete: Yes
- Optimal: Yes, if *h* is **admissible**

#### Optimal Efficiency
- Among **all optimal algorithms** that use the **same heuristic h**,
**A* expands the minimal number of Nodes**.

### Branch-and-Bound Search (Depth-First)
- DFS with constraints
- Treat the frontier as a *stack*: expand the most-recently
added path first
- Keep track of a lower bound and upper bound on solution cost at each path
	- **lower bound**: *LB(p) = f(p) = g(p) + h(p)*
		- Total cost for current node.
	- **upper bound**: *UB = f(p&ast;) = g(p&ast;) + h(p&ast;)*
		- Total cost of the best solution found so far.
	- *Total cost* - cost so far + estimate of the cost until goal node.
- If *LB(p) &ge; UB, remove p from frontier without expanding it (pruning).

#### Complexity, Completeness and Optimality
- Time: *O(b<sup>m</sup>)* (Worst Case)
- Space: *O(bm)*
- Complete - same as DFS:
	- Infinite-depth Spaces: No
	- Finite-depth Spaces w/ Loops: No
	- Finite-depth Spaces w/o Loops: Yes
- Optimal: Yes
- For many problems *Branch & Bound* is complete and useful due to *low space complexity*

### Iterative Deepening - IDA*
- *B&B* can still get stuck in infinite (extremely long) paths.
- Analogically to IDS, do Depth-First but to a fixed depth/bound *l*.
	- If no solution is found, increase bound *l*.
- As also for IDS, asymptotic complexity is not changed

### Memory-bounded A* - MBA*
- *Iterative deepening A** and *B&B* use a tiny amount of memory
- What if we've got more memory to use?
- Keep as much of the fringe in memory as we can
- If memory has to be freed, delete the worst paths (highest f(p))
- Back them up to a common ancestor

|      | Complete | Optimal | var Arc Len | Informed | Time | Space |
|:----:|:--------:|:-------:|:-----------:|:--------:|:----:|:-----:|
| BFS     | Y	| Y | N | N | *O(b<sup>d</sup>)* | *O(b<sup>d</sup>)* |
| UCS     | Y	| Y | Y | N | *O(b<sup>d</sup>)* | *O(b<sup>d</sup>)* |
| DFS     | N	| N | N | N | *O(b<sup>m</sup>)* | *O(bm)*            |
| **IDS** | Y	| Y | N | N | *O(b<sup>d</sup>)* | *O(bd)*            |
| GBFS      | N	| N | Y | Y | *O(b<sup>d</sup>)* | *O(bm)* |
| A*      | Y	| Y | Y | Y | *O(b<sup>d</sup>)* | *O(b<sup>d</sup>)* |
| B&B     | N	| Y | Y | Y | *O(b<sup>m</sup>)* | *O(bm)*            |
| **IDA***| Y	| Y | Y | Y | *O(b<sup>d</sup>)* | *O(bd)*            |
| **MBA***| Y	| Y | Y | Y | *O(b<sup>d</sup>)* | *O(bd)*            |

## Constraint Satisfaction Problems
### Consist of
- **Set of variables**
- **Domain for each variable**
- **Set of constraints**

### Definitions
- **Variables** can be of several main kinds depending on their domain:
	- *Boolean*: |dom(V)| = 2
	- *Finite*: the domain contains a finite number of values
	- *Infinite but Discrete*: the domain is countably infinite
	- *Continuous*: e.g., real numbers between 0 and 1
- **State** is defined by an *assignment of values* to some or all of the variables.
	- **Initial State**: all variables unassigned
- **Goal**: Discover some state that satisfies a given set of constraints.
	- **Goal Test**: A **set of constraints** specifying allowable combinations of values for subsets of variables.
- **Constraints** can be of different arity:
	- Unary
	- Binary
	- High-order
- **Consistent (legal) Assignment** - does not violate any constraints.
- **Solution or Model** - an assignment which is:
	- **complete**: *every variable given a value*  
	- **consistent (legal)**

#### Example
- **Sudoku**
	- Variables: empty cells (the preassigned cells are constraints)
	- Domains: 1 to 9
	- Possible worlds: all ways of assigning numbers to cells
		- 9<sup>#empty cells</sup> possible states

### Possible tasks in CSP
1. Determine whether a **Model exists**
	- Prove existence
	- Prove impossibility of existence
2. **Find a Model**
3. **Find all Models**
4. Find the **best Model** given quality measure
5. Determine whether some properties of the variables are persistent

### Search in CSP
- No. of Variables: *n*
- Max. Depth of Space: *n*
- Depth of Solution State: *n* (all variables assigned)
- Branching factor: *b* number of possible values for each of the variables
- Search Algorithm: Depth-First Search
	- All solutions are at the bottom
	- Finite search space without Cycles

#### CSP as a Search Problem
- Nodes: states
- Start Node: initial state
- Successor: state with one additional variable assigned
- Goal Node: Solution
- *Note*: The solution path does not matter for completeness, but the correct
choice of next nodes (which Variables to choose and which values to assign)
can increase efficiency greatly.

#### Backtracking
- Simple DFS wastes time searching when constraints have already been violated.
- Solution: Before generating successors, check if constraints have been violated. If yes, backtrack to the last decision point and continue.

#### Heuristics/Methods for CSP
- Plain backtracking is an uninformed algorithm.
- General-Purpose Heuristics:
	- Which variable to assign next?
	- In which order should the possible values be tried for each variable?

#### Strategies
- **Prune the Domains before Search (for unary constraints)**
- **Most Constraining Variable / Degree Heuristic**
	- The variable to be assigned next should be the variable that is involved in the **largest number of constraints** on unassigned variables.
	- This reduces the branching factor for future choices.
	- Useful to optimise the order of variable assignments.
- **Most Constrained Variable / Minimum Remaining Values Heuristic**
	- The variable to be assigned next should be the variable with the **fewest possible values**.
	- Useful to complement *Most Constraining Variable* in case of a tie.
- **Least Constraining Value**
	- Choose the value for a variable that leaves the **largest choice of values for other constraint-related variables**.
	- Useful to prevent deadlocks, reduce backtracking.
- **Forward Checking**
	- When a variable *X* is assigned, look at each unassigned variable *Y* **connected to** *X* and delete from *Y* any value that is inconsistent with the value chosen for *X*.
- **Constraint Propagation**
	- *Forward Checking* does not look far enough ahead.
	- Constraint propagation involves propagating the implications of an assignment of one variable onto **all** other variables, according to the specified constraints.
	- i.e. eliminate values from domains of variables that can never be part of a consistent solution.
	- Leads to a reduction of the search space.

#### Domain Splitting
- Assume Arc Consistency algorithm finishes with no unique solution i.e.,
for at least 1 var X, |dom(X)|>1
	1. Split X
	2. For all the values, continue Arc Consistency algorithm
	3. Unify solutions
- Pros: Simplifying the problem using Arc Consistency
- Cons: Need to keep all these CSPs around

## Adversarial Search for Game Playing
### Game vs Search
#### Properties of Search
- Deterministic
- Fully observable environment.
- **Solution**: is a method (often uses heuristics) for finding a goal
- **Evaluation function**: estimates the cost of path through current node to the goal

#### Properties of a Game
- Deterministic, but with contingency problem.?
- Fully observable environment with two agents.
- **Solution**: is a strategy in competitive environment
	- Strategy specifies a move for every possible opponent reply.
- **Evaluation function**: evaluates “goodness” of game position

### Game as a Search Problem
- State: *Board configuration* and ***turn***
- Successor Function: Returns a list of (move, state) pairs, each indicating a legal move and the resulting state.
- Terminal Test: Determines whether the game is over. States where the game has ended are the *terminal states*.
- Utility Function: Gives a numeric value to the terminal states.
	- Values at the end of the game are always equal and opposite for opponents (i.e. adversarial).

### Minimax Algorithm
#### MIN & MAX
##### Assumptions
- You are **MAX**. Utility values are with respect to **MAX**.
- Both players play optimally
- No time limit.

##### Results
- MINIMAX basically maximises the worst case outcome for MAX, which is an optimal strategy against infallible opponent.
- If MIN is fallible, MAX will get even better results, than in an optimal game.
- But MAX doesn't plan to exploit MIN's weaknesses, so other algorithms may be better vs bad opponents (take risks or plan for an opponent to take risks).
- Example: MINIMAX never plans to win a game of checkers, because it is not possible against optimal MIN.

#### Steps
1. Generate the entire game tree down to terminal nodes
2. Calculate utility
	a. Assess the utility of each terminal state
	b. Determine the best utility of the parents of the terminals
	c. Repeat the process for their parents until the root
3. Select the best move (i.e. the move with the highest utility)

#### Minimax Properties
- Minimax algorithm performs a depth-first exploration of the game tree.
- Time: ***O(b<sup>m</sup>)***, *b* is the no. of legal moves at each point and *m* is the max. depth of the tree.
- Space: ***O(bm)*** if it generates all the successors at once **OR** *O(m)* if it generates successors one at a time.
- For real games, the time cost is impractical if the whole tree is searched.

### &alpha;-&beta; Pruning
- The Pruning is done on the branches that don't influence the final decision.
- Pruning can decrease time complexity from ***O(b<sup>m</sup>)*** to ***O(b<sup>m/2</sup>)***.
- Returns the same move as the minimax algorithm.

#### &alpha;-&beta; bounds
- **TODO: Insert link to video with a good example**
- &alpha; is the lower bound of optimal utility.
- &beta; is the upper bound of optimal utility.
- The maximiser is always trying to push the value of &alpha; up.
- The minimiser is always trying to push the value of &beta; down.
- If the node's value is between &alpha; & &beta;, then the players might reach it.
- At the beginning (root of the tree), we set &beta; to &infin; and &alpha; to -&infin;.

##### Mechanism
- The lower bound is ***&alpha;*** - something which MAX can guarantee itself at this point.
- MIN finds a branch that guarantees it ***x*** and ***x < &alpha;***.
- MIN will always go for *x* or even lower value *[-inf, x]* in this branch.
- This is worse than *&alpha;*, so MAX will never choose this branch.
- The branch can be pruned.

#### Branch Ordering
- **Best-Case**: The pruning achieves maximum efficiency if the nodes are examined in correct order - **each player’s best move is the left-most alternative**, (i.e., evaluated first).
- **Worst-Case**: branches are ordered so that no pruning takes place. In this case alpha-beta gives no improvement over exhaustive search, *O(b<sup>m</sup>)*.
- With simple ordering heuristics (imperfect), performance is close to best-case.

#### Heuristics for Adversarial Search
- &alpha;-&beta; Pruning increases efficiency and depth of search but it it is not enough to reach the terminal nodes of non-primitive games in reasonable time.
- Instead of searching until the terminal nodes, Cut off (depth limited search) can be applied and the deepest reachable nonterminal node is evaluated with ***heuristic evaluation function*** instead of *utility function*.

#### Evaluation function
- Determine how good it is for the player, and how good it is for the opponent, and subtracts the two.
- Example from Chess:
	1. Value of all white pieces - Value of all black pieces
	2. Weighted sum of different features - both value of pieces as value of positions should be used.
	3. Neural Network using same or even more complex features.

### Games with Elements of Chance
- Non-deterministic games have random elements that can affect the operators.
- This increases the size of the search space.
- The assumption that the opponent minimises utility does not hold.
	- Chance nodes need to be added to the MAX & MIN nodes.
	- Probability needs to be taken into account.
