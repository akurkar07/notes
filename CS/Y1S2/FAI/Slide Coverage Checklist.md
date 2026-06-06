# FAI Slide Coverage Checklist

This file is a checklist for the AI PowerPoints used to make the notes. It is not a replacement for the revision notes; it is here to make sure the slide decks have been accounted for.

## Decks Checked

- `01 Course Introduction.pdf` / `1FAIintro`: 25 slides.
- `02 Machine Learning Introduction.pdf` / `2FAIml-intro`: 11 slides.
- `03 Machine Learning Process and Data.pdf` / `2FAIml-data`: 16 slides.
- `04 Machine Learning Unsupervised Learning.pdf` / `2FAIml-unsupervised`: 15 slides.
- `05 Machine Learning Supervised Learning.pdf` / `2FAIml-supervised`: 35 slides.
- `06 Artificial Neural Networks.pdf` / `2FAIml-ann`: 39 slides.
- `07 Bayes Rule.pdf` / `3FAIbayes`: 25 slides.
- `08 Knowledge Representation and Reasoning.pdf` / `3FAIkrr`: 12 slides.
- `09 Natural Language Processing.pdf` / `3FAInlp`: 16 slides.
- `10 Large Language Models.pdf` / `3FAIllm`: 15 slides.
- `11 Search Tree.pdf` / `4FAIsearch`: 19 slides.
- `12 Blind Search BFS and DFS.pdf` / `4FAIblind-BFS-DFS`: 15 slides.
- `13 Blind Search UCS.pdf` / `4FAIblind-UCS`: 10 slides.
- `14 Heuristic Search.pdf` / `4FAIheuristic`: 19 slides.
- `15 Game Playing.pdf` / `4FAIgame`: 25 slides.
- `16 What Next.pdf` / `5FAInext`: 7 slides.

Total checked: 294 slides.

## 1FAIintro

Covered in [[01 AI Basics]]:
- AI definitions from McCarthy and broader modern definitions.
- Weak AI vs strong AI / AGI.
- Top-down/deductive vs bottom-up/inductive approaches.
- AI milestones: Turing, Dartmouth, AI winter, Deep Blue, Watson, Eugene Goostman, AlphaGo, ChatGPT, current LLMs.
- Machine translation example and why language needs context/knowledge.
- Turing test definition, examples, and limitations.
- Chinese room experiment and the behaviour-vs-understanding issue.
- AI predictions by Simon, Turing, and Kurzweil.
- Responsible/ethical AI: privacy, security, bias, fairness, transparency, accountability, responsibility, safety.
- Course structure, assessment shape, textbooks, and computing setup.

## 2FAIml-intro

Covered in [[02 Machine Learning]]:
- Tom Mitchell definition using experience `E`, tasks `T`, and performance `P`.
- Traditional programming vs machine learning.
- Top-down/classic AI vs bottom-up/machine learning.
- Three pillars: models, computation, data.
- Big data sources and dimensions.
- Data mining vs machine learning.
- ML vs deep learning vs AI vs data science.
- Datasets/software: UCI, KDnuggets, Kaggle, Matplotlib, Seaborn, NumPy, Pandas, Scikit-learn, TensorFlow, Keras, PyTorch.

## 2FAIml-data

Covered in [[02 Machine Learning]]:
- Supervised, unsupervised, and reinforcement learning.
- Features, labels/targets, samples/instances/observations.
- Training/test split and generalisation.
- Overfitting.
- Data preprocessing: collection, cleaning, transformation, encoding, normalisation, splitting, visualisation.
- Missing data handling and Pandas examples.

## 2FAIml-unsupervised

Covered in [[02 Machine Learning]]:
- Unlabelled data and lack of ground truth.
- Applications: segmentation, clustering documents, fraud detection, genes, medical images.
- Clustering definition.
- K-means algorithm steps.
- Iris/k-means implementation outline.
- Association rules, Apriori, Frequent Pattern Growth, market basket examples.
- Correlation vs causation.

## 2FAIml-supervised

Covered in [[02 Machine Learning]]:
- Supervised process: prepare `X` and `y`, split, train, test.
- `train_test_split`, `fit`, `predict`, metrics, and cross-validation.
- Regression, MSE, coefficient/slope, intercept, polynomial regression, overfitting.
- Classification and categorical labels.
- Decision tree structure: internal nodes, branches, leaves.
- Decision tree training, interpretation, pros/cons.
- Random forest comparison.
- Titanic decision tree example, missing-data handling, factorisation, accuracy, confusion matrix, tree plotting.

## 2FAIml-ann

Covered in [[02 Machine Learning]]:
- McCulloch-Pitts, Hebb, perceptrons, AI winter, multi-layer revival.
- Neuron model: inputs, weights, threshold, output.
- Excitatory/inhibitory weights.
- Logic modelling: OR, AND NOT, XOR.
- Hidden layer, input layer, output layer.
- Epoch, training value, error, learning rate, weight update, MSE.
- Linearly separable functions and perceptron limits.
- Past-exam truth-table pattern.
- ANN pros/cons and applications.
- Deep learning, CNN, RNN, transformers.
- Turing Award and Nobel examples mentioned in slides.
- ANN Titanic/sklearn process, `MLPClassifier`, `MLPRegressor`, cross-validation, confusion matrix, interpretability limits.

## 3FAIbayes

Covered in [[03 Intelligent Systems]]:
- Bayes rule formula and meaning.
- Monty Hall problem and 66.66% switching result.
- Past-exam probability style.
- Real-world examples: search and rescue, medical diagnosis, spam classification.
- `GaussianNB` example process.

## 3FAIkrr

Covered in [[03 Intelligent Systems]]:
- Knowledge, domain knowledge, and symbolic/top-down AI.
- Knowledge-based systems, expert systems, case-based reasoning.
- KBS vs ML input/approach/output comparison.
- Knowledge acquisition/engineering bottleneck.
- KBS building process.
- Predicate logic representation, variables, constants, predicates, objects, facts, quantifiers, connectives.
- Past-exam proposition translation.
- Resolution rule, CNF, implication conversion, negation, unification, contradiction/empty clause.
- Dog/Spot tail example and Ellie/elephant past-exam pattern.

## 3FAInlp

Covered in [[03 Intelligent Systems]]:
- NLP definition.
- Symbolic, statistical, and ANN/deep learning approaches.
- NLP pipeline: normalisation, tokenisation, stopword removal, stemming, POS, NER, feature engineering, advanced applications.
- Eugene Goostman, Watson, Google Translate.
- Spam email classification with vocabulary, BoW, TF-IDF, word embeddings, `TfidfVectorizer`, `MultinomialNB`.

## 3FAIllm

Covered in [[03 Intelligent Systems]]:
- OpenAI/ChatGPT timeline from slides.
- GPT-2, GPT-3, GPT-4, Gemini, LLaMA, Copilot, Claude.
- Deep learning, RNNs, CNNs, transformers.
- Attention mechanisms and next-token probability.
- LLM process: data collection, cleaning, preprocessing, model selection, pre-training, fine-tuning, reinforcement learning.
- Tokens, context windows, prompt engineering, scaling law, temperature, self-attention.
- Models/data/computation race and model-size examples.
- Ethical issues, limitations, policy/developer/model/data challenges.

## 4FAIsearch

Covered in [[04 Search Techniques]]:
- Paper folding and exponential growth.
- TSP definition and route-count examples.
- Combinatorial explosion.
- Search space, search algorithms, search tree terminology.
- States, operators, neighbourhood, goal test, path cost.
- 8-puzzle definition.
- 8-queen past-exam pattern.
- Branching factor and exponential tree growth.

## 4FAIblind-BFS-DFS

Covered in [[04 Search Techniques]]:
- General search algorithm.
- Queue/fringe, node, goal test, operators, expand, queuing function.
- BFS method, enqueue-at-end, fringe/visited/undiscovered node types, evaluation criteria.
- BFS completeness, optimality, time complexity, and space complexity.
- DFS method, enqueue-at-front, completeness problem, optimality problem, time/space complexity.

## 4FAIblind-UCS

Covered in [[04 Search Techniques]]:
- UCS as general search ordered by path cost `g`.
- Cheapest node first.
- BFS as special case when all step costs are equal.
- Goal-test caution: accept goal when removed/chosen, not just discovered.
- Completeness, optimality, time complexity, space complexity.
- Past-exam style: show fringe queue, expanded nodes, shortest route and cost, optimality explanation.

## 4FAIheuristic

Covered in [[04 Search Techniques]]:
- Blind vs heuristic search.
- Heuristic function as domain knowledge/educated estimate.
- A* with `f(n)=g(n)+h(n)`.
- `h=0` makes A* behave like UCS.
- Overlarge `h` can behave greedily and lose optimality.
- Admissible heuristics.
- Romania/Bucharest straight-line distance example.
- 8-puzzle heuristics: misplaced tiles and Manhattan distance.
- Tree search vs evolutionary/meta-heuristic search examples.

## 4FAIgame

Covered in [[05 Game Playing]]:
- Why games matter in AI.
- Chess, Go, Deep Blue, AlphaGo, AlphaZero.
- Go/chess search-space difficulty.
- Game trees, terminal positions, agent/opponent, MAX/MIN.
- Minimax, utility values, perfect play.
- Nim lecture and past-exam variants.
- Alpha-beta pruning, alpha/beta cutoffs, DFS dependence.
- Deep Blue/AlphaGo/AlphaZero method comparisons.

## 5FAInext

Covered in [[COMP1008 Exam Guide]]:
- Final course summary.
- School AI course context.
- AI in the wild discussion points.
- Exam structure: 75%, ExamSys, no coding, five parts, all lecture content unless specified.
