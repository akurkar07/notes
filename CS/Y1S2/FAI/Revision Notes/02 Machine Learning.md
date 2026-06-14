# Machine Learning

## Definition

Tom Mitchell definition:
- A program learns from experience E, with respect to tasks T and performance measure P, if its performance at tasks in T improves with experience E.

Simpler version:
- Machine learning lets a program improve from data or experience instead of being fully hand-programmed for every case.

Key terms:
- Task: what the model is trying to do.
- Experience: the data or interactions it learns from.
- Performance measure: how success is measured.

## Machine Learning vs Traditional Programming

Traditional programming:
- Human writes rules.
- Program combines rules with input data.
- Output is produced directly.

Machine learning:
- Human provides data and chooses a model/algorithm.
- Training learns a model from examples.
- The model is then used to predict outputs for unseen data.

Good exam line:
- ML moves some of the work from manual rule writing into model training.

## Three Pillars of Machine Learning

Models:
- Algorithms and model structures used to learn patterns.
- Examples: regression, decision trees, ANN.
- Models avoid needing knowledge engineers to manually specify every function in an "agent".
- Recent breakthroughs are strongly linked to deep learning models.

Computation:
- Training can require significant processing power.
- Modern ML progress is partly due to cheaper and faster computation.
- The slides mention Moore's Law as a reason computation became less of a bottleneck.

Data:
- Often the key factor in successful ML.
- Quality, quantity, format, bias, and preprocessing all matter.
- Big data sources include social media, business, industry, devices, vehicles, IoT, and IoE.
- Important data dimensions are quantity, format/dimension, and speed.

## Data Mining vs Machine Learning

Data mining:
- Explores large datasets to find valid, novel, useful, and understandable patterns.
- Emphasis is often on discovering and explaining patterns.

Machine learning:
- Builds models that can predict or classify.
- Emphasis is often on predictive performance.

Useful distinction:
- Data mining explains patterns; machine learning predicts using models.

Data mining pattern requirements:
- Valid: holds on new data with some certainty.
- Novel: not obvious to the system.
- Useful: possible to act on.
- Understandable: humans can interpret the pattern/model.

## ML, Deep Learning, AI, and Data Science

AI:
- The broad field of intelligent computational systems.

Machine learning:
- A subset of AI based on learning from data/experience.

Deep learning:
- A subset of ML using multi-layer neural networks.

Data science:
- Broader practical field involving data collection, cleaning, analysis, visualisation, modelling, and interpretation.

Datasets and software mentioned:
- UCI Machine Learning Repository.
- KDnuggets.
- Kaggle.
- Matplotlib and Seaborn for data visualisation.
- NumPy and Pandas for data manipulation.
- Scikit-learn for machine learning.
- TensorFlow, Keras, and PyTorch for deep learning.

## Types of Learning

Supervised learning:
- Learns from labelled training data.
- Each sample has input features and a desired output.
- Goal: learn a function/model that maps inputs to outputs.
- Examples: classification, regression.
- Algorithms: linear regression, decision tree, ANN.

Unsupervised learning:
- Learns from unlabelled data.
- Goal depends on the task, such as finding clusters or associations.
- Examples: customer segmentation, document clustering, anomaly detection.
- Algorithms: k-means, association rule mining.

Reinforcement learning:
- Learns by trial and error over time.
- Uses feedback or rewards from actions.
- Goal: learn a policy that maximises reward.
- Example algorithms mentioned: Q-learning, Deep Q-networks, deep neural networks.
- Example applications: self-driving cars, robotics, and game playing.
- Not a main COMP1008 topic.

## Supervised vs Unsupervised

Supervised:
- Data has labels.
- There is ground truth for evaluation.
- Learns `G(x)` to approximate the true relationship `F(x)`.
- Used for prediction and classification.

Unsupervised:
- Data has no labels.
- No direct ground truth for accuracy.
- Learns hidden structure, clusters, distributions, or associations.
- Evaluation is more task dependent.

Slide notation:
- Supervised: data `D` is labelled, learn `G(x)` to predict labels of new data, goal is to minimise `(F(x)-G(x))^2`.
- Unsupervised: data `D` is unlabelled, often no explicit `y = F(x)`, learn clusters/densities/distributions, goal depends on the task.
- Supervised examples: weather prediction, stock prediction, credit risk, spam detection, image recognition.
- Unsupervised examples: customer behaviour, segmentation, product recommendation.

## Data Preprocessing

Data preprocessing means turning raw data into a suitable format for ML.

Common steps:
- Understand the problem.
- Identify samples/instances.
- Identify features/attributes.
- Identify labels/targets if supervised.
- Collect relevant data.
- Clean missing data.
- Remove duplicates and outliers where appropriate.
- Transform categorical values into numeric representations.
- Normalise numerical data where useful.
- Visualise data to understand patterns and possible problems.
- Split data into training and testing sets.

Missing data handling:
- Drop rows with missing values.
- Replace missing values with mean, mode, or another chosen value.
- Choose the method carefully because imputation can affect bias and performance.

Why preprocessing matters:
- It is often time-consuming.
- It improves model accuracy.
- It reduces noise and bias.
- Pandas DataFrames are used heavily for this kind of work.

Typical code ideas from slides:
- `pd.read_csv("my_csv_file.csv")` reads a CSV file.
- `df["Age"].mean()` calculates a column mean.
- `df.isnull()` checks missing data.
- `df.dropna()` removes rows with missing data.
- `df.replace(to_replace=np.nan, value=m)` replaces missing values.
- `df["SavingAcc"].fillna("little")` fills a categorical missing value.
- Matplotlib scatter plots are used for visualisation.

## Training and Testing

Training set:
- Used to learn model parameters.

Test set:
- Used to estimate how well the model generalises to unseen data.

Typical split:
- 70% training and 30% testing.

Cross-validation:
- Repeats training/testing over multiple partitions.
- Gives a more stable estimate than one random split.
- The supervised slides used `cross_val_score(..., cv=5, scoring="neg_mean_squared_error")`.

Overfitting:
- The model fits the training data too closely.
- It learns noise or accidental patterns.
- It performs badly on unseen test data.

## Regression

Regression predicts continuous values.

Simple linear regression:
- Learns a line of the form `G(x) = b0 + b1*x`.
- Training finds parameters that minimise mean squared error.
- `b0` is the intercept.
- `b1` is the coefficient/slope.

Mean squared error:
- Measures the average squared difference between predicted and actual values.
- Lower MSE usually means better fit.

Pros:
- Short training time.
- Easy to implement.
- Easy to interpret.

Cons:
- Sensitive to noise and outliers.
- Can overfit if extended too far.
- Simple linear regression cannot model complicated relationships.

Polynomial regression:
- Adds extra terms such as `x^2`.
- More flexible, but can overfit.

Sklearn process from slides:
- Split data using `train_test_split(X, y, test_size=0.3)`.
- Create the model with `LinearRegression()`.
- Train with `lr.fit(x_train, y_train)`.
- Predict with `lr.predict(x_test)`.
- Evaluate with `metrics.mean_squared_error(y_test, y_pred)`.
- Inspect the learned function with `lr.coef_` and `lr.intercept_`.

## Classification

Classification predicts categorical labels.

Examples:
- Spam or not spam.
- Credit risk category.
- Image class.
- Survived or not survived.

Key point:
- Classification has labelled categories; regression predicts continuous values.

## Decision Trees

A decision tree is a supervised model that predicts by following feature-based rules.

Parts:
- Internal nodes: decisions/rules on features.
- Branches: outcomes of those decisions.
- Leaf nodes: predicted labels.

Training:
- The algorithm partitions the decision space.
- It chooses which feature to split on.
- It chooses what value to split at.

Pros:
- Reasonable training time.
- Can handle many features.
- Easy to implement.
- Easy to interpret.

Cons:
- Can create simple decision boundaries only.
- Can struggle with missing data.
- Can fail on complicated relationships.
- Over-complex trees can overfit.

Random forest:
- Uses multiple decision trees.
- Each tree is trained on random subsets of data/features.
- Aggregates predictions from all trees.
- Usually more accurate and less prone to overfitting than one tree.
- Less interpretable and slower to train than one tree.

Decision tree implementation details from slides:
- Titanic example features included `Pclass`, `Gender`, `Age`, `SibSp`, and `Fare`.
- Label was `Survived`.
- Missing values can be filled using mode or mean depending on the feature.
- Categorical values can be encoded using `pd.factorize`.
- A model can be created with `DecisionTreeClassifier(max_depth=4, random_state=1)`.
- Training uses `t_model.fit(X_train, y_train)`.
- Testing uses `t_model.predict(X_test)`.
- Accuracy can be calculated with `metrics.accuracy_score(y_test, y_predict)`.
- Tree interpretation can use `tree.plot_tree`.
- The slides show a possible rule path like `Sex <= 0.5`, `pclass <= 2.5`, and fare/age thresholds. The exact learned rule depends on data split, missing-data decisions, and tree depth.

Decision tree tuning:
- Depth is a decision parameter.
- Feature choice and missing-data handling affect the trained tree.
- Deeper trees can look more accurate on training data but overfit.

## Unsupervised Learning Details

Unsupervised learning discovers hidden patterns or structures from unlabelled data.

Advantages:
- No need to label data.
- Useful when labels are expensive or unavailable.

Limitations:
- No ground truth for direct accuracy evaluation.
- Results can be harder to interpret.

Applications mentioned:
- Marketing/customer segmentation.
- Document clustering.
- Fraud detection.
- Clustering genes.
- Clustering medical images.

## Clustering

Clustering groups similar objects.

Given:
- An unlabelled dataset `D`.
- A similarity or distance metric.

Goal:
- Find natural partitions or groups of similar data points.

## K-Means

K-means steps:
- Choose the number of clusters `K`.
- Initialise `K` cluster centroids randomly.
- Repeat until the maximum number of iterations or convergence:
  - Assign each data point to the nearest centroid using a distance metric.
  - Update each centroid by taking the mean of the points assigned to it.
- Output final cluster assignments and centroids.

Implementation details from slides:
- Iris dataset was used as an example.
- Libraries included NumPy, Pandas, Matplotlib, `load_iris`, and `KMeans`.
- `Data = pd.DataFrame(iris.data, columns=iris.feature_names)` creates the feature table.
- Scatter plots were used to inspect sepal/petal measurements.
- `KMeans(n_clusters=3, max_iter=100, random_state=0)` creates the model.
- `fit_predict(x)` trains and returns cluster labels.
- `kmeans.cluster_centers_` shows centroid locations.

## Association Rules

Association rule mining discovers correlations between variables/items.

Given:
- A set of records containing items.

Goal:
- Produce dependency rules that predict the occurrence of variable/item `X` with variable(s)/item(s) `Y`.

Algorithms mentioned:
- Apriori.
- Frequent Pattern Growth.

Examples:
- Market basket analysis.
- `{Bread} -> {Milk}`.
- `{Diaper} -> {Beer}`.

Important warning:
- Correlation is not causation.
- Association rules say items occur together; they do not prove one causes the other.

## Artificial Neural Networks

ANNs are inspired by networks of neurons.

Basic neuron model:
- Inputs are multiplied by weights.
- The weighted inputs are summed.
- If the sum reaches a threshold, the neuron fires.

ANN history:
- McCulloch and Pitts built early neural network models in 1943.
- Hebb proposed an early learning rule in 1949.
- Perceptrons caused excitement in the 1950s and 1960s because they could converge to correct weights for some problems.
- Minsky and Papert showed limits of perceptrons for non-linearly separable functions, contributing to an AI winter for ANN research.
- Multi-layer networks later revived interest because they can handle non-linearly separable problems.

Important terms:
- Input: feature value.
- Weight: strength of a connection.
- Threshold: value needed for firing.
- Output: result produced by the neuron.
- Learning rate: controls how quickly weights change.
- Epoch: one full pass through the training set.
- Loss function: measures error, such as mean squared error.

Weight update idea:
- Error is the desired output minus the actual output.
- If there is error, adjust weights using the input, error, and learning rate.

Training pseudocode:

```text
While an epoch produces an error:
    Check the next input pattern.
    Err = Y - O.
    If Err != 0:
        wi = wi + LR * Xi * Err.
```

Learning rate:
- Usually set by experimentation.
- The slides gave `0.1` as a typical example.
- Too high can overshoot good weights or fail to settle.
- Too low can make training very slow.

Linearly separable:
- Classes can be separated by a straight line, plane, or hyperplane.
- A single-layer perceptron can only represent linearly separable functions.
- XOR is the classic example that requires a hidden layer.

Logic functions:
- McCulloch-Pitts style networks can model logic functions.
- OR can be modelled with positive weights and a threshold.
- AND NOT can be modelled using one positive and one inhibitory/negative weight.
- XOR can be represented as `(X1 AND NOT X2) OR (X2 AND NOT X1)`.
- XOR needs a hidden layer because a single perceptron cannot separate it linearly.

Past exam pattern:
- Given a truth table, decide whether a perceptron can learn it.
- Answer by checking whether the output classes are linearly separable.

ANN pros:
- Can learn more complicated class boundaries.
- Can handle many features.
- Can be more accurate than simpler models.

ANN cons:
- Hard to implement well.
- Choosing structure and parameters involves trial and error.
- Training can be slow.
- Can overfit.
- Hard to interpret.

Deep learning:
- Uses multiple layers of connected neurons.
- Learns progressively higher-level features.
- Examples mentioned: CNNs, RNNs, transformers.
- CNNs and transformers were marked as not assessed in COMP1008 ANN detail.

Deep learning milestones mentioned:
- 2018 Turing Award: Yann LeCun, Yoshua Bengio, and Geoffrey Hinton.
- 2024 Nobel Physics: John Hopfield and Geoffrey Hinton for work connected to foundations of machine learning.
- 2024 Nobel Chemistry: David Baker, Demis Hassabis, and John Jumper for AlphaFold/protein-structure work.

CNN:
- Learns feature engineering by itself using filters.

Transformer:
- Transforms an input sequence to an output sequence.
- ChatGPT, Gemini, and other LLMs build on transformers.

## Confusion Matrix

A confusion matrix breaks classification results into:
- True positives.
- True negatives.
- False positives.
- False negatives.

Why it matters:
- Accuracy alone can hide what kinds of errors the model is making.
- It is useful when false positives and false negatives have different costs.

## ANN Implementation Notes

ANN classifier:
- `MLPClassifier(hidden_layer_sizes=(3,6), max_iter=3000)`.
- Train with `mlp.fit(X_train, y_train)`.
- Predict with `mlp.predict(x_test)`.
- Accuracy can be checked with `metrics.accuracy_score`.
- Cross-validation can use `cross_val_score(..., cv=5, scoring="accuracy")`.

ANN interpretation:
- Trained neural networks are difficult to understand.
- Weights can be inspected using `mlp.coefs_`.
- ANN weights do not directly reflect feature importance in the easy way a decision tree can.

ANN regression:
- Use `MLPRegressor`.
- ANNs can solve both classification and regression tasks.

## Supervised Learning Applications

Applications mentioned in the supervised learning summary:
- Healthcare: disease diagnosis and drug discovery.
- Retail: product recommendation and demand prediction.
- Transportation: traffic prediction and object recognition.
- Security: facial recognition and cyberattack detection.
- NLP: translation and sentiment analysis.
- Finance: credit scoring for loan approvals.

Key data point:
- Supervised learning needs high-quality labelled data, which can be expensive.
- Known ground truth allows more accurate evaluation metrics than unsupervised learning.
