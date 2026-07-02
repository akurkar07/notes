# AI Methods Comprehensive Notes

These notes summarise the AI Methods lecture slides into revision-focused explanations. The module is mainly about solving hard optimisation/search problems with heuristic, metaheuristic, evolutionary, and hyper-heuristic methods.

## Big Picture

AI Methods in this module is not mainly about neural networks or symbolic AI. It is about optimisation: how to search a very large set of possible decisions when exact methods are too slow.

Typical example domains:

- Timetabling and exam timetabling
- Vehicle routing and routing variants
- Nurse rostering and personnel scheduling
- Bin packing
- Travelling Salesman Problem
- Knapsack
- Maximum satisfiability
- Wind farm layout and engineering design
- Additive manufacturing process planning

The key theme is that real-world optimisation problems often have search spaces that grow exponentially. Exact methods may guarantee optimality, but can become infeasible. Heuristic methods trade guarantees for practical performance.

## Core Terminology

### Decision Making

Decision making is choosing between alternatives. In optimisation, each alternative is a candidate solution and the goal is to choose the best one according to an objective.

### System

A system is a set of related elements that together perform an activity, function, or task. Optimisation problems often model systems where decisions affect the quality or cost of the whole system.

### Search

Search can mean:

- Finding a path from an initial state to a goal state.
- Finding a high-quality solution inside a large solution space.

Path search is common in AI problems like route planning and game playing. Optimisation search is broader: the goal may not be a path, but a configuration, assignment, ordering, schedule, or set of parameter values.

### Optimisation

Optimisation is the process of minimising or maximising an objective:

- Minimise cost, distance, conflicts, violations, or energy.
- Maximise profit, value, quality, coverage, or satisfaction.

A single-objective optimisation problem has one main objective. Multi-objective problems have more than one objective, often with trade-offs.

### Problem vs Problem Instance

A problem is the general high-level question.

An instance is a concrete input to that problem.

Example:

- Problem: assign tourist groups to buses while minimising the number of buses used.
- Instance: the actual group sizes and bus capacity for one specific day.

### Search Space

The search space is the set of all candidate solutions. It may be:

- Continuous: real-valued parameters, such as angles, coordinates, or weights.
- Discrete: finite combinations, such as permutations, bitstrings, assignments, or schedules.

Combinatorial optimisation problems are discrete optimisation problems where the number of possible solutions grows very quickly.

### Global and Local Optima

A global optimum is better than every other solution in the whole search space.

A local optimum is better than every solution in its neighbourhood, but may still be worse than some distant solution.

This distinction matters because local search methods can become trapped in local optima.

### Search Landscape

A search landscape is a way of thinking about the objective values over the search space. Easy landscapes have smooth paths toward good solutions. Hard landscapes may have:

- Many local optima
- Plateaus
- Ridges
- Deceptive regions
- Large neutral areas

Heuristic methods are designed to navigate these landscapes efficiently.

## Exact vs Inexact Methods

### Exact Methods

Exact methods systematically search for an optimal solution and can prove optimality. Examples include:

- Exhaustive search
- Branch and bound
- Mathematical programming
- Dynamic programming for suitable problems

The weakness is runtime. For many NP-hard combinatorial optimisation problems, exact methods become too slow as instance size grows.

### Inexact or Approximate Methods

Inexact methods aim to find good solutions quickly without guaranteeing optimality.

They are useful when:

- The search space is too large for exhaustive search.
- A good solution is more useful than a perfect solution found too late.
- Real-world constraints make exact modelling difficult.

This module focuses on inexact methods.

## Heuristics

A heuristic is a rule-of-thumb method for solving or improving a solution. It is usually based on domain knowledge or search intuition.

Heuristics can be:

- Constructive: build a solution from scratch or from a partial solution.
- Perturbative: start with a complete solution and modify it.
- Deterministic: same input gives the same output every time.
- Stochastic: includes random choices, so different runs may return different solutions.

### Constructive Heuristics

Constructive heuristics work on partial solutions.

Example: nearest neighbour for TSP.

1. Choose a starting city.
2. Repeatedly visit the nearest unvisited city.
3. Stop when all cities have been visited.
4. Return to the start city if needed.

Nearest neighbour is constructive because it builds the route one city at a time.

### Perturbative Heuristics

Perturbative heuristics work on complete solutions.

Example: 2-opt or pairwise exchange for TSP.

1. Start with a complete tour.
2. Swap or reverse part of the tour.
3. Evaluate the new tour.
4. Keep or reject the modified tour according to an acceptance rule.

Perturbative methods need a complete solution before they can start.

### Limitations of Heuristics

Heuristics often:

- Have no optimality guarantee.
- Need redesigning for new problems.
- Are sensitive to parameter settings.
- Can perform well on one instance type but badly on another.

## Pseudo-Random Numbers and Experiments

Stochastic search uses pseudo-random numbers. These are generated deterministically from a seed, but appear random.

Important experimental points:

- A fixed seed makes a run reproducible.
- Reusing the same seed for every trial can give misleading results.
- Multiple independent runs should use different seeds.
- Results should be reported statistically, not from a single lucky run.

Problems with random generators can include:

- Short periods
- Non-uniform distributions
- Correlations
- Poor seeding

For stochastic algorithms, experimental design matters as much as implementation.

## Combinatorial Optimisation Problems

### Bin Packing

Given:

- A set of items
- Each item has a size
- Bins have fixed capacity

Goal:

- Pack all items into the minimum number of bins without exceeding capacity.

Simple heuristic:

- Largest item first fit: sort items by decreasing size, then place each item into the first bin where it fits.

### Travelling Salesman Problem

Given:

- A set of cities
- Distances between cities

Goal:

- Find a shortest tour visiting each city exactly once and returning to the start.

Representations:

- Usually a permutation of cities.

Common moves:

- Swap two cities.
- Reverse a segment.
- Insert one city elsewhere.

### 0/1 Knapsack

Given:

- A knapsack capacity
- Items with weights and values

Goal:

- Choose a subset of items maximising value without exceeding capacity.

Representation:

- Bitstring where 1 means include the item and 0 means exclude it.

### Boolean Satisfiability and MAX-SAT

SAT asks whether there is a truth assignment that satisfies a Boolean formula.

MAX-SAT asks for an assignment that satisfies as many clauses as possible.

Representation:

- Bitstring of truth values.

Evaluation:

- Number of satisfied clauses, or number of unsatisfied clauses.

SAT is a decision problem. MAX-SAT is an optimisation problem.

## Components of Heuristic Search

Most heuristic, metaheuristic, and hyper-heuristic methods are built from the same core components:

- Search process
- Solution representation
- Initialisation
- Neighbourhood or move operators
- Evaluation/objective function
- Move acceptance rule
- Memory, if used
- Termination condition

### Representation

A representation is the way a candidate solution is encoded.

Good representations should usually be:

- Complete: able to represent all valid solutions.
- Connected or connex: possible to move between candidate solutions through the neighbourhood structure.
- Efficient: easy to evaluate and modify.
- Suitable for the operators used.

Common representations:

- Binary bitstrings: knapsack, MAX-SAT, feature selection.
- Permutations: TSP, sequencing, scheduling orders.
- Integer encodings: assignment and timetabling problems.
- Value encodings: continuous parameters.
- Tree encodings: genetic programming and generated programs.

Representation and operator design must fit together. For example, ordinary one-point crossover on a binary encoding of a TSP permutation can create illegal tours.

### Neighbourhood

The neighbourhood of a solution is the set of solutions reachable by applying one move operator.

Examples:

- Bit flip for binary strings.
- Random reassignment for discrete symbols.
- Adjacent swap for permutations.
- Insertion for permutations.
- Exchange for permutations.
- Inversion for permutations.

Neighbourhood size and structure strongly affect search behaviour. A large neighbourhood may contain better moves but be expensive to scan. A small neighbourhood is cheaper but may trap the search.

### Evaluation Function

An evaluation function measures the quality of a solution.

It may be called:

- Objective function
- Cost function
- Fitness function
- Penalty function

For minimisation, lower is better. For maximisation, higher is better.

The evaluation function gives the search process feedback. Without it, the algorithm cannot distinguish good moves from bad moves.

### Delta Evaluation

Delta evaluation updates only the part of the objective affected by a move.

Example:

- In TSP, swapping two cities changes only nearby edges, so the whole tour length need not be recomputed from scratch.

Delta evaluation can make local search much faster, especially when evaluating many neighbours.

## Hill Climbing

Hill climbing is a local search method that repeatedly moves to a better neighbouring solution.

Generic structure:

1. Choose an initial solution.
2. Generate one or more neighbours.
3. Evaluate them.
4. Move to an improving neighbour.
5. Stop when no move is accepted or a stopping condition is reached.

For minimisation, "improving" means lower cost. For maximisation, it means higher value.

### Random Mutation Hill Climbing

Random Mutation Hill Climbing samples random moves.

1. Start with a current solution.
2. Apply a random mutation.
3. Evaluate the candidate.
4. If it is improving or accepted under the chosen rule, keep it.
5. Repeat.

It is easy to implement but may miss good moves because it samples only part of the neighbourhood.

### First Improvement Hill Climbing

First improvement scans neighbours and accepts the first improving move found.

Strength:

- Often faster than best improvement because it stops scanning early.

Weakness:

- The first improvement may not be the best available improvement.

### Best Improvement Hill Climbing

Best improvement scans the whole neighbourhood and chooses the best improving move.

Strength:

- Makes the best local move according to the neighbourhood.

Weakness:

- More expensive because it evaluates all neighbours.

### Davis's Bit Hill Climbing

Davis's bit hill climbing uses a random permutation of bit positions and tries bit flips in that order. It is a structured way to scan bitstring neighbours while still randomising the order.

### Stopping Conditions

Possible stopping criteria:

- Target objective value reached.
- No improving move exists.
- Maximum number of iterations.
- Maximum runtime.
- Maximum number of evaluations.
- No improvement for a given number of iterations.

### Strengths of Hill Climbing

- Simple to implement.
- Requires only representation, neighbourhood, evaluation, and acceptance.
- Often improves quickly.
- Useful as a component inside larger methods.

### Weaknesses of Hill Climbing

- Gets stuck in local optima.
- Can stall on plateaus.
- Can struggle with ridges and deceptive landscapes.
- Performance depends heavily on the starting solution and neighbourhood.

## Metaheuristics

A metaheuristic is a high-level, problem-independent framework for designing heuristic optimisation algorithms.

It gives a strategy for search, rather than a complete problem-specific algorithm.

Metaheuristics can be:

- Single-point trajectory methods.
- Population-based methods.

Examples:

- Iterated Local Search
- Tabu Search
- Simulated Annealing
- Evolutionary Algorithms
- Genetic Algorithms
- Memetic Algorithms

### Exploration and Exploitation

Exploitation means intensively improving known good regions.

Exploration means searching new regions to avoid premature convergence.

Good metaheuristics balance both.

## Iterated Local Search

Iterated Local Search extends local search by repeatedly perturbing a local optimum and applying local search again.

Typical structure:

1. Generate an initial solution.
2. Apply local search to reach a local optimum.
3. Perturb the solution.
4. Apply local search again.
5. Decide whether to accept the new local optimum.
6. Repeat.

Main components:

- Initialisation
- Local search method
- Perturbation strength
- Acceptance criterion
- Termination condition

Design issue:

- If perturbation is too weak, the method falls back into the same local optimum.
- If perturbation is too strong, the method becomes close to random restart.

## Tabu Search

Tabu Search uses memory to avoid cycling and to escape local optima.

Core idea:

- Keep a tabu list of recently used moves or attributes.
- Forbid moves that would immediately undo recent decisions.
- Allow non-improving moves so the search can leave local optima.

Important components:

- Forbidding strategy: what becomes tabu.
- Freeing strategy: when tabu status expires.
- Tabu tenure: how long something remains tabu.
- Aspiration criterion: when a tabu move can be allowed anyway, usually if it gives a very good solution.

In practice, tabu lists often store move attributes rather than entire solutions.

Strengths:

- Escapes local optima.
- Reduces cycling.
- Can exploit memory of the search path.

Weaknesses:

- Requires parameter choices.
- Tabu tenure is problem-dependent.
- Too much restriction can block useful moves.

## Move Acceptance

Move acceptance decides whether a candidate solution should replace the current solution.

This is separate from move generation. A method can generate many candidate moves, but the acceptance rule controls the trajectory.

### Basic Acceptance Rules

All Moves:

- Accept every candidate.
- Encourages exploration but can behave like random walk.

Improving Only:

- Accept only strictly better candidates.
- Strong exploitation, but can get stuck.

Improving or Equal:

- Accept candidates that are better or equal.
- Can move across plateaus, but may cycle.

### Naive Acceptance

Accept improving or equal moves. Accept worse moves with fixed probability p.

This can improve exploration, but performance is highly sensitive to p.

### Late Acceptance

Late Acceptance compares a candidate against the solution accepted L steps ago.

Basic idea:

- Keep a list of previous accepted costs.
- Accept a candidate if it is not worse than the cost from L steps back.

This lets the search accept some worse moves without requiring a temperature schedule.

Important parameter:

- L, the history length.

### Threshold Acceptance

Threshold methods accept candidates that are worse than the current solution only if they are within a threshold.

For minimisation:

- Accept if candidate_cost <= current_cost + threshold.

The threshold may be static, dynamic, or adaptive.

### Great Deluge

Great Deluge is a dynamic threshold method.

Analogy:

- A water level gradually falls.
- Candidate solutions are accepted if they are below the water level.

Early search accepts more moves. Later search becomes stricter as the water level decreases.

### Extended Great Deluge

Extended Great Deluge adapts the water level and decay rate using feedback from the search. It can include restart-like behaviour when progress stalls.

### Simulated Annealing

Simulated Annealing is inspired by physical annealing.

Idea:

- At high temperature, accept worse moves more often.
- As temperature cools, accept fewer worse moves.

For minimisation:

- Improving moves are accepted.
- Worse moves may be accepted with probability based on the cost increase and temperature.

Common form:

```text
delta = candidate_cost - current_cost
accept if delta < 0
otherwise accept with probability exp(-delta / T)
```

Temperature schedule:

- Initial temperature should be high enough to allow exploration.
- Final temperature should be low enough to reject most worse moves.
- Cooling rate controls how quickly exploration reduces.

If cooling is too fast, the algorithm behaves like hill climbing and may freeze into a poor local optimum.

If cooling is too slow, runtime may be high.

## Parameter Setting

Heuristics and metaheuristics usually contain parameters.

Examples:

- Perturbation strength in ILS
- Tabu tenure in Tabu Search
- Temperature and cooling rate in Simulated Annealing
- Population size in genetic algorithms
- Mutation probability
- Crossover probability
- Depth of search
- Intensity of mutation

### Types of Parameters

Categorical or structural:

- Choice of initialisation method.
- Choice of mutation operator.
- Choice of local search method.

Ordinal:

- Small, medium, large neighbourhood.
- Low, medium, high mutation strength.

Numerical:

- Mutation probability.
- Population size.
- Temperature.
- Tabu tenure.

### Parameter Tuning

Parameter tuning is offline.

You choose settings before the algorithm runs, usually using experiments.

Examples:

- Grid search
- Random search
- Sequential tuning
- Taguchi orthogonal arrays
- Automated methods such as irace, ParamILS, and SPOT

### Parameter Control

Parameter control is online.

The algorithm changes parameter values during the run.

Types:

- Dynamic: follows a predetermined schedule.
- Adaptive: changes based on feedback from search.
- Self-adaptive: parameters are encoded in individuals and evolve with them.

### Design of Experiments

Design of Experiments studies how controllable factors affect performance.

For algorithm tuning:

- Factors are parameters.
- Levels are parameter values.
- Response is performance.

Fractional factorial designs reduce the number of configurations by sampling the parameter space systematically.

### Taguchi Method

The Taguchi method uses orthogonal arrays to test parameter settings efficiently.

Process:

1. Select control parameters.
2. Select possible levels for each parameter.
3. Choose an appropriate orthogonal array.
4. Run experiments for each configuration.
5. Compare performance using a metric.
6. Analyse main effects.
7. Confirm the predicted best setting.

This is useful when many full combinations would be too expensive.

## Evolutionary Algorithms

Evolutionary Algorithms are population-based metaheuristics inspired by natural evolution.

They maintain a population of candidate solutions and repeatedly apply:

- Selection
- Crossover
- Mutation
- Replacement

### Genetic Algorithms

A Genetic Algorithm usually has:

- Representation or chromosome
- Population
- Fitness function
- Parent selection
- Crossover
- Mutation
- Replacement strategy
- Termination condition

Generic loop:

1. Generate an initial population.
2. Evaluate fitness.
3. Select parents.
4. Apply crossover.
5. Apply mutation.
6. Evaluate offspring.
7. Form the next generation.
8. Repeat until termination.

### Selection

Selection chooses parents or survivors.

Common methods:

- Fitness proportionate or roulette wheel selection.
- Tournament selection.
- Rank-based selection.
- Elitism.

Tournament selection:

1. Randomly sample a small group.
2. Choose the best individual from that group.

Larger tournament size increases selection pressure.

### Crossover

Crossover combines information from parents.

For bitstrings:

- One-point crossover
- Two-point crossover
- Uniform crossover

For permutations:

- Ordinary bitstring crossover can create illegal solutions.
- Special permutation crossovers are needed.

### Mutation

Mutation introduces small random changes.

Examples:

- Bit flip for binary strings.
- Value perturbation for real-valued representations.
- Swap, insertion, inversion, or displacement for permutations.

Mutation helps preserve diversity and explore new regions.

### Replacement

Replacement decides which individuals survive.

Transgenerational GA:

- Replaces a large fraction of the population each generation.

Steady-state GA:

- Replaces only a few individuals at a time.

Elitism:

- Preserves the best individuals so they are not lost.

### Termination

Possible criteria:

- Maximum generations.
- Maximum evaluations.
- Target fitness reached.
- Population convergence.
- No improvement for a fixed number of generations.

### Convergence

Convergence means individuals become increasingly similar.

Gene convergence:

- Most individuals share the same value at a chromosome position.

Population convergence:

- The population as a whole becomes genetically similar.

Premature convergence is bad because the population loses diversity before finding high-quality solutions.

## Memetic Algorithms

Memetic Algorithms combine population-based evolutionary search with local search.

They use:

- Genetic exploration from the evolutionary algorithm.
- Local-search exploitation from hill climbing or another improvement method.

A meme is a local improvement strategy or search behaviour. In this context, memes are like local refinements that can be applied to individuals.

Strengths:

- Often faster and more accurate than plain genetic algorithms.
- Good balance between exploration and exploitation.

Weaknesses:

- More computationally expensive per generation.
- Need to choose when and how to apply local search.
- The best meme may depend on the problem landscape.

## Benchmark Functions

Benchmark functions are artificial test functions used to compare optimisation algorithms.

They are useful because:

- The global optimum is known.
- They are easy to compute.
- They have controlled properties.
- They can test behaviour on different landscape types.

Properties:

- Continuous or discontinuous
- Differentiable or non-differentiable
- Scalable or fixed dimensional
- Separable or non-separable
- Unimodal or multimodal
- Noisy, deceptive, or plateau-rich

Separable functions allow delta evaluation because each dimension contributes independently.

### Binary and Gray Encoding

For function optimisation, real or integer values may be encoded as bitstrings.

Gray encoding makes adjacent numeric values differ by Hamming distance 1. This can help mutation move gradually through numeric values.

## Permutation-Based Evolutionary Search

Permutation problems like TSP require operators that preserve valid permutations.

Plain binary crossover can produce:

- Missing cities
- Duplicate cities
- Undefined city codes
- Invalid tours

Permutation crossover operators include:

- Partially Mapped Crossover (PMX)
- Order Crossover (OX)
- Cycle Crossover (CX)

Permutation mutation operators include:

- Exchange mutation
- Insertion mutation
- Inversion mutation
- Displacement mutation

### PMX

Partially Mapped Crossover:

- Selects two cut points.
- Swaps the segment between parents.
- Uses mappings to preserve valid permutations.
- Tries to preserve positions and values.

### OX

Order Crossover:

- Copies a subsequence from one parent.
- Fills remaining positions using the relative order from the other parent.
- Useful when ordering is more important than absolute position.

### CX

Cycle Crossover:

- Preserves absolute positions from parents by identifying cycles.
- Offspring inherit positions from one parent until a cycle closes, then fill from the other.

## Multimeme Memetic Algorithms

Multimeme Memetic Algorithms allow individuals to carry memetic material as well as genetic material.

The memetic material can specify:

- Which local search operator to use.
- How many iterations to apply.
- Where to apply the local search.
- When to apply it.
- How often to apply it.
- Which acceptance criteria to use.

The idea is self-adaptation:

- The algorithm learns useful operator choices during evolution.
- Genetic material and memetic material co-evolve.

Trade-off:

- Learning good memes takes time.
- A hand-tuned single meme can sometimes perform better if the best choice is already known.

## Hyper-Heuristics

Hyper-heuristics search over heuristics rather than directly over solutions.

Instead of asking:

- Which solution should I move to?

A hyper-heuristic asks:

- Which low-level heuristic should I apply next?
- Or what new heuristic should I generate?

Goal:

- Raise the level of generality.
- Reduce the need for problem-specific algorithm design.
- Work across multiple domains.

### Domain Barrier

The domain barrier separates the hyper-heuristic from problem-specific details.

The hyper-heuristic sees:

- A set of low-level heuristics.
- Objective values.
- Feedback from applying heuristics.

The problem domain handles:

- Representation
- Validity
- Evaluation
- Low-level operators

This enables cross-domain search.

### Selection Hyper-Heuristics

Selection hyper-heuristics choose from existing low-level heuristics.

Generic loop:

1. Select a low-level heuristic.
2. Apply it to the current solution.
3. Decide whether to accept the result.
4. Update heuristic scores or memory.
5. Repeat.

Selection methods can be:

- Non-learning
- Learning-based

### Non-Learning Selection

Simple random:

- Choose a heuristic uniformly at random.

Random permutation:

- Apply heuristics in random order.

Greedy:

- Try heuristics and choose the candidate with best objective value.

Tournament greedy:

- Sample a subset of heuristics.
- Choose the best candidate from that subset.

### Reinforcement Learning Selection

Reinforcement learning assigns scores to heuristics.

Good heuristics are rewarded. Bad heuristics are punished.

Selection may use:

- Best score
- Tournament selection over heuristic scores
- Roulette wheel selection based on scores

Scores should adapt because a heuristic that was useful early may be less useful later.

### Choice Function

A choice function combines measures such as:

- Recent improvement from a heuristic.
- Pairwise performance after another heuristic.
- Time since the heuristic was last used.

This gives a more informed selection rule than simple reward/punishment.

### Move Acceptance in Hyper-Heuristics

Selection alone is not enough. A hyper-heuristic still needs move acceptance because:

- Low-level heuristics may be stochastic.
- A chosen heuristic may produce a worse move.
- The search still needs a sensible trajectory.

Move acceptance methods from local search can be reused.

## HyFlex and CHeSC

HyFlex is a framework for cross-domain hyper-heuristic research.

It supplies:

- Multiple problem domains.
- Low-level heuristics.
- A common interface.

CHeSC 2011 was a cross-domain heuristic search competition based on HyFlex.

Important experimental issue:

- Training and test instances must be separated.
- Computational budgets must be fair across machines.
- Hyper-heuristics may still require tuning.

## Multi-Stage Selection Hyper-Heuristic

The multi-stage selection hyper-heuristic uses two stages:

- A simple, fast hyper-heuristic.
- A slower, more sophisticated hyper-heuristic.

The idea is relay hybridisation:

- Use the simple method first.
- Switch to the more expensive method when useful.

This can improve performance, but adds parameters that may need tuning.

## Graph-Based Hyper-Heuristics

Graph-based hyper-heuristics apply constructive low-level heuristics to graph-colouring-style problems.

### Graph Colouring

Given:

- A graph with vertices and edges.

Goal:

- Assign colours to vertices so adjacent vertices do not share a colour.

Variants:

- k-colouring: can the graph be coloured with k colours?
- Minimum colouring: find the fewest colours needed.

Important vertex properties:

- Degree: number of incident edges.
- Saturation degree: number of differently coloured neighbouring vertices.

### Exam Timetabling as Graph Colouring

In exam timetabling:

- Vertices represent exams.
- Edges represent shared students.
- Colours represent time periods.

Hard constraint:

- Exams taken by the same student cannot be in the same time period.

Soft constraints:

- Spread exams out for students.
- Avoid undesirable room/time patterns.

Constructive heuristics:

- Largest degree: schedule highly connected exams first.
- Saturation degree: prioritise exams with the most constrained colour choices.
- Colour degree: based on colour availability.
- Largest weighted degree or related variants.

A constructive hyper-heuristic can learn sequences of such heuristics while building a timetable.

## Genetic Programming

Genetic Programming evolves programs or expression trees.

It uses:

- Function set: internal nodes such as +, -, *, /.
- Terminal set: variables and constants.
- Population of programs.
- Fitness based on program performance.
- Crossover and mutation on trees.

Mutation:

- Select a random node.
- Remove that subtree.
- Insert a randomly generated subtree.

Crossover:

- Swap subtrees between two parent programs.

### Generative Hyper-Heuristics

Generative hyper-heuristics create new heuristics rather than selecting from a fixed set.

Two ideas:

- Disposable heuristics: generate heuristics for one problem instance or run.
- Reusable heuristics: train heuristics that can be reused on unseen instances.

Genetic programming is one way to generate heuristic rules automatically.

## Exam-Style Comparisons

### Hill Climbing vs Simulated Annealing

Hill climbing:

- Accepts only improving or non-worsening moves.
- Fast and simple.
- Easily trapped in local optima.

Simulated Annealing:

- Sometimes accepts worse moves.
- Exploration decreases as temperature cools.
- Needs temperature parameters.

### Tabu Search vs Simulated Annealing

Tabu Search:

- Uses memory to avoid cycling.
- Deterministic or stochastic depending on implementation.
- Key parameter is tabu tenure.

Simulated Annealing:

- Uses probabilistic acceptance.
- Key parameters are temperature and cooling schedule.

### Genetic Algorithm vs Memetic Algorithm

Genetic Algorithm:

- Population-based exploration.
- Uses selection, crossover, mutation.

Memetic Algorithm:

- Adds local search.
- Usually stronger exploitation.
- More expensive per individual.

### Metaheuristic vs Hyper-Heuristic

Metaheuristic:

- Searches the solution space directly.
- Needs problem-specific representation and operators.

Hyper-heuristic:

- Searches over heuristics or heuristic choices.
- Aims for more generality across domains.

## Common Pitfalls

- Confusing a heuristic with a metaheuristic.
- Saying hill climbing always finds the optimum.
- Using binary genetic operators on permutation problems without repair.
- Ignoring parameter sensitivity.
- Reporting one stochastic run as evidence of performance.
- Forgetting that acceptance and selection are separate decisions.
- Assuming hyper-heuristics need no tuning.
- Treating training and test instances as interchangeable.

## Quick Revision Checklist

- Define heuristic, metaheuristic, and hyper-heuristic.
- Explain constructive vs perturbative search.
- Explain representation, neighbourhood, evaluation, and move acceptance.
- Compare random mutation, first improvement, best improvement, and Davis's bit hill climbing.
- Describe Iterated Local Search.
- Describe Tabu Search and tabu tenure.
- Describe Simulated Annealing and cooling schedules.
- Explain parameter tuning vs parameter control.
- Explain GA components and why permutation problems need special operators.
- Explain Memetic Algorithms and multimeme adaptation.
- Explain selection hyper-heuristics and the domain barrier.
- Explain graph colouring and exam timetabling as a graph problem.
- Explain Genetic Programming as a generative hyper-heuristic method.
