# COMP1008 Overview and Exam Guide

Source slides used:
- `1FAIintro.pptx`
- `2FAIml-intro.pptx`
- `2FAIml-data.pptx`
- `2FAIml-unsupervised.pptx`
- `2FAIml-supervised.pptx`
- `2FAIml-ann.pptx`
- `3FAIbayes.pptx`
- `3FAIkrr.pptx`
- `3FAInlp.pptx`
- `3FAIllm.pptx`
- `4FAIsearch.pptx`
- `4FAIblind-BFS-DFS.pptx`
- `4FAIblind-UCS.pptx`
- `4FAIheuristic.pptx`
- `4FAIgame.pptx`
- `5FAInext.pptx`

Coverage note:
- These notes were expanded against all 16 AI PowerPoint decks from Downloads.
- Total slide count checked: 294 slides.
- The notes aim to preserve examinable details, examples, processes, formulae, and past-exam patterns, not just high-level summaries.

## Assessment Facts

- Module: COMP1008 Fundamentals of AI.
- Exam weighting: 75%.
- Exam marks: 75.
- Exam duration: 2 hours.
- Coursework weighting: 25%.
- Coursework marks: 25.
- Exam is in ExamSys.
- Exam is in-person.
- No coding is required in the exam.
- Exam topics are:
  - AI basics.
  - Intelligent systems.
  - Machine learning.
  - Tree search.
  - Game playing.
- All lecture content is examinable unless the lecturer says otherwise.
- Computing material supports coursework and applied understanding, but the exam does not require coding.

## Revision Priorities

High priority:
- Definitions of AI, weak AI, strong AI, and machine learning.
- Top-down/deductive AI vs bottom-up/inductive AI.
- Turing test and Chinese room experiment.
- Responsible and ethical AI issues.
- Supervised vs unsupervised learning.
- Training set, test set, features, labels, samples, overfitting, ground truth.
- Regression, classification, decision trees, random forests, and ANNs.
- Bayes rule and conditional probability.
- Knowledge representation and reasoning.
- NLP approaches and LLM basics.
- Search spaces, search trees, and combinatorial explosion.
- BFS, DFS, UCS, and A*.
- Completeness, optimality, time complexity, and space complexity.
- Minimax and alpha-beta pruning.

Extra details not to skip:
- Lecture-specific examples: machine translation failure, Monty Hall, TSP route explosion, 8-puzzle, 8-queen, Nim, Titanic, Iris, spam email classification.
- Code-level library names: Pandas, NumPy, Matplotlib, Scikit-learn, `train_test_split`, `cross_val_score`, `KMeans`, `LinearRegression`, `DecisionTreeClassifier`, `MLPClassifier`, `GaussianNB`, `MultinomialNB`, `TfidfVectorizer`.
- KRR logic notation: predicates, quantifiers, implication conversion, CNF, unification, resolution.
- LLM concepts: tokens, context windows, prompt engineering, scaling law, temperature, self-attention, data/model/compute race, limitations, and ethics.
- Search exam discipline: queue/fringe at each step, expanded nodes, path cost, `g`, `h`, `f`, and when to stop.

## How To Answer

- For definitions, give the keyword and one clean explanation.
- For comparisons, explicitly say how the two methods differ.
- For algorithms, write the steps in order.
- For search questions, show the queue/fringe after each expansion.
- For game tree questions, label MAX/MIN levels before propagating values.
- For alpha-beta questions, show which node is pruned and why.
- For machine learning questions, name the data split, the model, and the evaluation method.
- For pros/cons questions, give balanced bullet points rather than one long paragraph.

## Core Course Shape

Part I: AI basics:
- AI definitions.
- History and milestones.
- Turing test.
- Chinese room.
- Ethical AI.

Part II: machine learning:
- ML definition.
- Data, models, computation.
- Data preprocessing.
- Supervised learning.
- Unsupervised learning.
- ANN.

Part III: intelligent systems:
- Bayes rule.
- Knowledge representation and reasoning.
- NLP.
- LLMs.

Part IV: search:
- Search spaces.
- Blind search.
- Heuristic search.
- Game playing.

## Quick Links

- [[01 AI Basics]]
- [[02 Machine Learning]]
- [[03 Intelligent Systems]]
- [[04 Search Techniques]]
- [[05 Game Playing]]
