# Search Techniques

## Search Space

A search space is the set of all possible states or solutions to a problem.

Search algorithms:
- Take a problem as input.
- Explore the search space.
- Return a solution or failure.
- Search is important because many science and engineering problems can be seen as searching for the right answer.

Examples:
- Path finding.
- Puzzle solving.
- Game playing.
- Travelling Salesman Problem.

## Combinatorial Explosion

Combinatorial explosion means the number of possible solutions grows extremely quickly as the problem size increases.

Why it matters:
- Exhaustive search becomes impossible for large problems.
- Even fast computers cannot check all possibilities in huge search spaces.

TSP example:
- A salesperson must visit each city once and return to the start.
- The number of possible routes grows explosively with the number of cities.
- Goal: find the minimum distance/cost route.

Numbers from the slides:
- 10-city TSP: about 181,000 possible solutions.
- 20-city TSP: about 10,000,000,000,000,000 possible solutions.
- 50-city TSP: about `1.52 * 10^64` possible solutions.
- A 10GHz computer doing `10^9` tours per second since the start of the universe would still only have done about `10^26` tours.

Paper-folding example:
- Thin paper of thickness `0.1mm = 10^-4m`.
- Earth to Moon distance about `3.8 * 10^8m`.
- The point is exponential growth: repeated doubling can become huge surprisingly quickly.

Exam line:
- Search methods are needed because brute force over the full search space is often impractical.

## Search Trees

A search tree represents possible choices.

Terms:
- Root: initial state.
- Node: a state in the search.
- Edge/branch: an action or transition.
- Leaf: node with no expanded children.
- Goal state: desired state.
- Path: sequence of states/actions from root to a node.
- Branching factor `b`: average number of children per node.
- Solution depth `d`: depth of the first/optimal solution.
- Maximum depth `m`: deepest possible search level.
- Parent/child nodes: nodes connected by an operator/action.
- Depth of a node: distance from the root.
- Depth of a tree: maximum node depth.
- Branches: actions/operators between states.

## General Search Algorithm

General idea:

```text
Create a queue containing the initial state.
Loop:
    if the queue is empty, return failure.
    remove the front node from the queue.
    if it is a goal, return it.
    expand it and add children using the queuing function.
```

Key point:
- Different search algorithms mainly differ in how the queue/fringe is ordered.

General search vocabulary from slides:
- `nodes`: the queue/fringe.
- `node`: current state removed from the queue.
- `Make-Queue`: creates a queue.
- `Make-Node`: creates a node from a state.
- `Initial-State[p]`: initial state of problem `p`.
- `Goal-Test[p]`: checks whether the current state solves the problem.
- `Operators[p]`: actions available in the problem.
- `Expand`: produces child nodes.
- `QUEUING-FN`: controls search strategy.

## Defining A Search Problem

States:
- Possible states of the problem.
- In a tree, states are represented as nodes.

Search space:
- All nodes/states reachable from the initial state.

Operators:
- Actions that move from one state to another.
- In a tree, operators correspond to branches.

Neighbourhood:
- All possible states reachable from a given state.

Goal test:
- A test applied to a state to decide whether it solves the problem.

Path cost:
- Cost of taking a particular path.

## 8-Puzzle Example

States:
- A board of eight tiles at their locations.
- It is useful to include the blank tile as part of the state.

Operators:
- A tile moves left, right, up, or down.
- Equivalently, the blank moves left, right, up, or down.

Goal test:
- Current board matches the goal board.

Path cost:
- Each tile/blank move costs 1.

## 8-Queen Exam Pattern

Problem:
- Place 8 chess queens on a chess board so that no two queens attack each other.

Possible definition:
- Initial state: empty board.
- Operator: add a queen into a cell.
- States: any arrangement of 0 to 8 queens on the board.
- Goal state: valid arrangement of 8 queens.

Combinatorial explosion point:
- Level 1 has the empty-board root.
- Level 2 can have 64 choices.
- Level 3 can have 63 choices for each previous node.
- The search tree grows very quickly.

Improving search:
- Define/model the problem to make the tree smaller.
- Use better search techniques to move through the tree efficiently.

## Evaluation Criteria

Completeness:
- Will the algorithm find a solution if one exists?

Optimality:
- Will the algorithm find the best/lowest-cost solution?

Time complexity:
- How many nodes may be expanded?

Space complexity:
- How many nodes must be stored?

## Breadth-First Search

BFS expands the shallowest nodes first.

Method:
- Expand the root node first.
- Expand all nodes at level 1 before level 2.
- More generally, expand all nodes at depth `d` before nodes at depth `d + 1`.

Queue behaviour:
- First-in, first-out.
- New nodes are added to the back.
- Queuing function: `ENQUEUE-AT-END`.

Properties:
- Complete if the branching factor is finite.
- Optimal when every step has the same cost.
- Time complexity is usually written around `b^d`.
- Space complexity is high because it stores many frontier nodes.
- The actual time/space can be lower if a solution is found before level `d`.

Three node types in tree search:
- Fringe/open/leaf nodes: discovered and in the queue, but not yet processed or goal-tested.
- Visited/closed nodes: already processed and tested.
- Undiscovered nodes: not yet discovered.

Good for:
- Finding the shallowest solution.
- Problems where all actions have equal cost.

Bad for:
- Deep search spaces.
- Large branching factors.

## Depth-First Search

DFS expands the deepest node first.

Method:
- Expand the root node first.
- Explore one branch before another branch.

Queue/stack behaviour:
- Last-in, first-out.
- Follows one path down before backtracking.
- Queuing function: `ENQUEUE-AT-FRONT`.

Properties:
- Not complete in infinite-depth spaces or spaces with loops.
- Not optimal.
- Time complexity can be high, around `b^m`.
- Space complexity is lower than BFS because it stores mainly the current path and alternatives.
- The slides describe DFS storage as the path from root to leaf plus unexpanded neighbour nodes, around `bm`.
- DFS is neither complete nor optimal in the general case.

Good for:
- Low memory search.
- Deep exploration when a solution may be far down.

Bad for:
- Finding shortest paths.
- Infinite or cyclic spaces without checking.

## Uniform Cost Search

UCS expands the node with the lowest path cost `g(n)` from the root.

Queue behaviour:
- Ordered by total path cost so far.
- Cheapest path is expanded first.
- Queuing function: enqueue by cost.
- Cost is usually written as `g(n)`.

Properties:
- Complete if path costs do not decrease and are positive enough.
- Optimal because it always expands the cheapest path first.
- BFS is a special case of UCS when all step costs are equal.
- Time and space can still be expensive.
- Worst-case time complexity is often written around `b^d`, though it can be much better depending on costs.
- Space complexity stores expanded/fringe nodes of the cheapest costs, also expensive.

Important exam detail:
- A goal is only accepted when it is removed from the front of the queue, not merely when it first appears in the fringe.

Example idea from slides:
- BFS may find path `S-A-G` of cost 11.
- UCS can find a cheaper path such as `S-B-G` of cost 10.
- UCS may discover a goal earlier but delay expanding it because another fringe node has lower path cost.

UCS applicability:
- BFS should only be used for optimal path finding when all branch costs are the same.
- UCS can be used with varied path costs as long as costs never decrease along depth.

## Blind Search Summary

BFS:
- Uses depth/level.
- Complete: yes, with finite branching.
- Optimal: yes, if all costs are equal.
- Memory: high.

DFS:
- Uses depth.
- Complete: not always.
- Optimal: no.
- Memory: lower.

UCS:
- Uses path cost `g(n)`.
- Complete: yes under suitable cost assumptions.
- Optimal: yes.
- Memory: high.

## Heuristic Search

Heuristic search uses domain knowledge to choose promising nodes.

Heuristic:
- An estimate of how close a node is to the goal.
- Often written as `h(n)`.
- It is an educated guess or intuitive judgement using domain knowledge.

Why it helps:
- Blind search may waste effort in unpromising parts of the tree.
- A heuristic can guide the search toward likely solutions.

## A* Search

A* combines:
- `g(n)`: path cost from the initial state to node `n`.
- `h(n)`: estimated cost from `n` to the goal.
- `f(n) = g(n) + h(n)`: estimated total cost through `n`.

Algorithm idea:
- Expand the node with the smallest `f(n)`.
- Function form: `A*-SEARCH(problem)` returns `GENERAL-SEARCH(problem, g + h)`.

Special cases:
- If `h(n) = 0`, A* becomes UCS.
- If `h(n)` dominates too much, search becomes greedier and may lose optimality.

## Admissible Heuristics

A heuristic is admissible if it never overestimates the true cost to the goal.

Why it matters:
- A* is complete and optimal when the heuristic is admissible and other normal assumptions hold.

Examples:
- Straight-line distance between cities is admissible for road distance because it cannot overestimate the shortest possible road path.
- In an 8-puzzle, number of misplaced tiles can be admissible.
- Manhattan distance can also be admissible and often more informative.

Romania map example:
- Straight-line distance to Bucharest is used as `h`.
- It is admissible because no road route can be shorter than the straight-line distance.
- A* compares `g + h` for fringe nodes.
- In the lecture example, A* reached the same optimal route as UCS but expanded fewer nodes.
- UCS expanded: Sibiu, Rimnicu, Fagaras, Arad, Pitesti, Zerind, Craiova, Timisoara, Bucharest.
- A* expanded: Sibiu, Rimnicu, Pitesti, Fagaras, Bucharest.
- Both found route cost 278 in the lecture example, but A* reached it with fewer expansions.

Straight-line distance examples from the slide table:
- Arad: 366.
- Bucharest: 0.
- Craiova: 160.
- Dobreta: 242.
- Eforie: 161.
- Fagaras: 178.
- Giurgiu: 77.
- Hirsova: 151.
- Iasi: 226.
- Mehadia/Mehadai: 241.
- Neamt: 234.
- Oradea: 380.
- Pitesti: 98.
- Rimnicu: 193.
- Sibiu: 253.
- Timisoara: 329.
- Urziceni: 80.
- Vaslui: 199.
- Zerind: 374.

8-puzzle heuristics:
- `h1`: number of tiles in the wrong position.
- `h2`: sum of Manhattan distances of tiles from their goal positions.
- Both can be admissible.
- `h2` is usually better because it is closer to the true remaining cost and explores fewer nodes.
- The lecture example gives `h1 = 4` and `h2 = 5` for one state.
- Typical 8-puzzle solution length in the slides: about 20 steps.
- Approximate branching factor: about 3.
- Search-space size: about `9! = 362,880` states.

Heuristic comparison from the slides:
- Depth 2: A* with `h1` explored 6 nodes; A* with `h2` explored 6.
- Depth 4: `h1` explored 13; `h2` explored 12.
- Depth 6: `h1` explored 20; `h2` explored 18.
- Depth 8: `h1` explored 39; `h2` explored 25.
- Depth 10: `h1` explored 93; `h2` explored 39.
- Depth 12: `h1` explored 227; `h2` explored 73.
- Depth 14: `h1` explored 539; `h2` explored 113.
- Lesson: the closer an admissible heuristic is to the actual cost, the fewer nodes A* tends to explore.

Better heuristic:
- Still admissible.
- Closer to the true cost.
- Explores fewer nodes.

## How To Do Search Exam Questions

For BFS/DFS/UCS/A*:
- Write the initial queue/fringe.
- Expand exactly one node at a time.
- Add children in the order required by the question.
- For UCS, sort by `g`.
- For A*, calculate `g + h = f`.
- Mark expanded nodes separately from fringe nodes.
- Stop only when the goal is selected for expansion/removal according to the algorithm.
- State the final route and cost.

Common trap:
- Do not stop UCS or A* just because the goal appears in the queue. Stop when it is the next node chosen.

## Search Technique Types

Tree search examples:
- BFS.
- DFS.
- UCS.
- A*.
- Minimax.

Evolutionary/meta-heuristic examples mentioned:
- Genetic algorithms.
- Tabu search.

The course focuses mainly on tree search.
