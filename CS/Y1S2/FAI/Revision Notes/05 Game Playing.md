# Game Playing

## Why Games Matter In AI

Games are useful for AI because:
- They involve intelligent decision making.
- Rules are usually clear.
- Success or failure is easy to measure.
- They can be represented as search trees.
- They often need planning against an opponent.
- They do not always require large amounts of real-world knowledge.
- Many are solvable in principle by search from the starting state to a winning position.

Examples:
- Chess.
- Go.
- Nim.

Milestones:
- Deep Blue defeated Garry Kasparov in 1997.
- AlphaGo defeated Lee Sedol in 2016.
- AlphaZero learned strong play through self-play.

Chess lecture notes:
- Wolfgang von Kempelen's "The Turk" was an 18th-century chess automaton.
- Hubert Dreyfus claimed in the 1960s that no computer could play even amateur-level chess.
- Newell and Simon predicted in 1957 that a computer would be chess champion in 10 years.
- Deep Blue beat Kasparov on 11 May 1997.
- Match score in slides: 2:1 to Deep Blue with three draws.

Go lecture notes:
- AlphaGo was developed by Google DeepMind.
- October 2015: first computer Go program to beat a professional human Go player.
- March 2016: beat Lee Sedol, a 9-dan player, 4:1.
- December 2016 to January 2017: "Master" won online games 60:0.
- December 2017: AlphaZero.

Why Go is hard:
- Larger board than chess.
- More complex because a new piece appears every move.
- Fast computation alone is less helpful.
- Material advantage can be only short-term.
- Human play involves a high degree of pattern recognition.
- Claude Shannon's estimate for chess was around `10^120` unique states.
- Deep Blue at 200M positions/second would still need around `10^100` years to evaluate all chess games.

## Game Trees

A game tree represents possible moves by both players.

Terms:
- State: a board/game position.
- Move: transition to another state.
- Terminal state: game is over.
- Utility value: numerical value of a terminal or evaluated state.
- MAX: player trying to maximise the utility.
- MIN: opponent trying to minimise MAX's utility.

Key point:
- Unlike ordinary path search, another player is actively trying to stop you winning.
- This is why the search alternates between MAX and MIN layers.

## Minimax

Minimax is a game tree search method for two-player adversarial games.

Idea:
- MAX chooses the move with the highest utility.
- MIN chooses the move with the lowest utility.
- Values are propagated backwards from terminal states to the root.
- The agent maximises its own position while assuming the opponent minimises it.
- It is associated with John von Neumann, 1944.
- It backtracks from terminal/evaluated positions up the game tree.

Steps:
- Generate the game tree, or enough of it.
- Assign utilities to terminal states.
- At MAX levels, choose the maximum child value.
- At MIN levels, choose the minimum child value.
- The root value tells what outcome perfect play can force.

Good exam phrasing:
- Minimax assumes both players play perfectly.
- If the full tree can be generated, minimax tells which player can force a win.

## Utility Functions

A utility function measures how good a position is for a player.

Simple example:
- `1` means MAX wins.
- `0` means MIN wins.
- The slides also use positive values to mean good for the computer/agent and negative values to mean bad for it.

More complex games:
- Utility may estimate how good a non-terminal position is.
- This matters when the full tree is too large to search.

## Nim Example Shape

Nim-style questions often ask you to:
- Draw the search tree.
- Mark terminal states.
- Assign utility values.
- Propagate values with Minimax.
- Decide who wins under perfect play.
- Count winning paths if asked.

Method:
- Label whose turn each level belongs to.
- Work from leaves upward.
- Use max at MAX levels and min at MIN levels.

Nim lecture rule:
- Start with a pile of tokens.
- On each move, divide a pile into two non-empty, non-equal piles.
- The player who cannot move loses.
- The lecture example starts with 7 tokens and asks for the complete search tree.

Past exam Nim variant:
- Starts with a single stack of 6 tokens.
- Each move removes one, two, or three tokens.
- A non-empty stack must remain.
- A player unable to move loses.
- Min plays first.
- Tasks: draw the tree, merge identical child states on each level, assign minimax utility values, decide who wins with perfect play, and count winning paths.

## Alpha-Beta Pruning

Alpha-beta pruning improves minimax by avoiding branches that cannot affect the final decision.

Core idea:
- If a player already has a better option elsewhere, do not explore a branch that cannot improve the outcome.

Alpha:
- Best value MAX can guarantee so far.

Beta:
- Best value MIN can guarantee so far.

Pruning:
- Stop exploring a branch when it cannot change the final minimax decision.

Why it matters:
- It gives the same minimax result.
- It can explore far fewer nodes.
- It is especially useful when the game tree is huge.

Lecture pruning example:
- If `util(D) = 6`, then a parent MIN node `B` may be known to be `<= 6`.
- If another branch already gives MAX a better or equal option, some children no longer matter.
- If `util(J) = 8`, then a parent MAX node `E` may be known to be `>= 8`.
- If best play will not go via `E`, remaining child values such as `K` can be irrelevant and pruned.

## How To Spot Pruning

At a MIN node:
- If the node's value is already less than or equal to an ancestor MAX option, MAX will avoid it.
- Remaining children can be pruned.

At a MAX node:
- If the node's value is already greater than or equal to an ancestor MIN option, MIN will avoid it.
- Remaining children can be pruned.

Exam note:
- Alpha-beta pruning relies on depth-first style evaluation.
- If you tried to evaluate level-by-level like BFS, you would not get the same early pruning.
- The slides explicitly ask whether BFS would allow the same pruning and answer no, because pruning depends on evaluating the tree underneath a node.

## Deep Blue, AlphaGo, AlphaZero

Deep Blue:
- Chess system.
- Used tree search, utility/evaluation functions, alpha-beta pruning, and large chess knowledge/opening/endgame resources.
- The slides describe it as tree search plus utility function plus minimax plus alpha-beta pruning plus large opening/ending boards.

AlphaGo:
- Go system.
- Used search plus deep learning.
- Used supervised learning and reinforcement learning.
- Used minimax/alpha-beta style search ideas plus deep learning.
- Reduced explored nodes using alpha-beta pruning, utility estimates based on human games, and machine learning with CNNs.

AlphaZero:
- Learned from self-play.
- Did not rely on supervised learning from human games.
- Used Monte Carlo tree search and neural networks.
- The slides say it used one CNN on boards from self-playing and Monte Carlo Tree Search for look-ahead by simulations.

Exam comparison:
- Older game AI relied heavily on search and expert knowledge.
- Modern game AI often combines search with machine learning.

## How To Answer Game Tree Questions

- Draw or read the tree carefully.
- Label MAX and MIN levels.
- Assign terminal utilities first.
- Work backwards from the leaves.
- At MAX nodes, write the largest child value.
- At MIN nodes, write the smallest child value.
- State the best move from the root.
- For alpha-beta, mark pruned branches and give the inequality/reason.

Common mistakes:
- Mixing up MAX and MIN levels.
- Propagating values from top down instead of bottom up.
- Pruning before enough information is known.
- Forgetting that minimax assumes perfect play.

## Course Summary For Game Playing

Know:
- How minimax works.
- How to apply minimax to a new small game tree.
- That alpha-beta pruning is built on minimax.
- Where cuts are applied.
- How to assign utility values in the final/pruned tree.
