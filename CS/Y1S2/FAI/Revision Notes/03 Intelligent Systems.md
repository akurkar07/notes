# Intelligent Systems

## Bayes Rule

Bayes rule lets us update a probability when new evidence is observed.

Core idea:
- It reverses conditional probability.
- It helps calculate the probability of a cause or hypothesis given evidence.

Formula:

```text
P(A | B) = P(B | A) P(A) / P(B)
```

Terms:
- `P(A)`: prior probability of A.
- `P(B | A)`: likelihood of seeing B if A is true.
- `P(B)`: probability of the evidence.
- `P(A | B)`: posterior probability after observing B.

Exam use:
- Identify the event/hypothesis.
- Identify the evidence.
- Substitute carefully into Bayes rule.
- Explain what the posterior means.

## Monty Hall

The Monty Hall problem is a useful Bayes/probability example.

Setup:
- Three doors.
- One car and two goats.
- You pick one door.
- The host opens another door with a goat.
- You choose whether to stay or switch.

Key answer:
- Switching gives a 2/3 chance of winning.
- Staying gives a 1/3 chance.

Why:
- Your original door had a 1/3 chance.
- The other unopened door effectively gets the remaining 2/3 once the host reveals a goat.

Bayes-rule conclusion:
- The probability of winning by switching is `2/3`, or about `66.66%`.
- The host's action is not random in the ordinary sense because the host knows where the goat is.
- The evidence changes how probability is distributed across the unopened doors.

Real-world Bayes examples from slides:
- Search and rescue: update the probability of a lost person being in an area when new evidence appears, such as clothing found by a search dog.
- Medical diagnosis: classify the probability of a disease from symptoms and test results.
- Email services: classify emails as spam or legitimate using word/phrase frequencies and feedback over time.

Naive Bayes implementation:
- `GaussianNB` can be imported from `sklearn.naive_bayes`.
- Train with `NB.fit(X_train, y_train)`.
- Predict with `NB.predict(X_test)`.
- Evaluate with `metrics.accuracy_score(y_test, y_predict)`.

Past exam pattern:
- Identify which event is the hypothesis, such as "machine M3 caused the fault".
- Identify the evidence.
- Calculate denominator/evidence probability across all possible causes.
- Substitute into Bayes rule.
- State the final posterior probability and what it means.

## Knowledge Representation and Reasoning

KRR is about representing knowledge so a system can reason with it.

Knowledge includes:
- Facts.
- Concepts.
- Procedures.
- Models.
- Examples.
- Rules about the world.

Why it matters:
- Humans use both methods and domain knowledge in problem solving.
- KRR lets systems use explicit knowledge, not just data patterns.
- KRR dominated AI methods until around the 1990s.
- It is associated with top-down, deductive, symbolic AI.

KRR strengths:
- Uses explicit domain knowledge.
- Can be interpretable.
- Can make decisions quickly within a narrow domain.

KRR limits:
- Not all tasks can be easily formalised.
- Vague or uncertain knowledge is hard to represent.
- Probability and fuzzy logic are ways to handle uncertainty.

## Knowledge-Based Systems

A knowledge-based system is built around a knowledge base.

Knowledge base:
- A stored collection of knowledge taken from human expertise or domain sources.
- Often represented as rules or cases.

Reasoning:
- Applies the stored knowledge to produce decisions or new propositions.

Expert systems:
- Use rules.
- Example form: if condition then conclusion.
- Domain-specific and interpretable.
- Example from slides: if TV spending is 3k, then sales are 3.6k.

Case-based reasoning:
- Uses previous cases.
- Solves new problems by comparing them with stored examples.
- Example: in a stored case, TV spending of 3k led to sales of 3.6k; for a new problem with 4k TV spending, reason from similar cases.

KBS vs machine learning:
- Machine learning input: data with inputs/outputs.
- Machine learning approach: training algorithm.
- Machine learning output: model.
- KBS input: facts or knowledge.
- KBS approach: reasoning.
- KBS output: new knowledge.

## Building a Knowledge-Based System

Main stages:
- Acquire knowledge from experts or sources.
- Represent knowledge symbolically.
- Apply reasoning to draw conclusions.

Possible process:
- Define the task.
- Build the domain vocabulary.
- Develop a model of reasoning.
- Use flowcharts or decision trees as design tools.
- Iterate and refine.

Vocabulary:
- Words, phrases, and formulae used to describe the domain.
- A good vocabulary makes the reasoning model precise enough to use.

## KRR Bottlenecks

Knowledge acquisition is difficult because:
- Human knowledge is complex.
- Human knowledge can be unstructured or vague.
- Experts may disagree.
- Knowledge can become outdated.
- Rules are time-consuming to maintain.
- Missing knowledge can cause wrong decisions.

Exam point:
- KRR is interpretable, but manually building and maintaining knowledge is hard.

## Uncertainty

Not all knowledge is exact.

Ways to handle uncertainty:
- Probability, such as Bayes rule.
- Fuzzy logic for vague concepts.

Useful phrasing:
- Symbolic systems work well when knowledge can be formalised, but real-world knowledge is often vague, incomplete, or uncertain.

## Predicate Logic For KRR

Natural language problem:
- Human language is often ambiguous.
- Sentence structure is not uniform.
- This makes it difficult to reason reliably with raw natural language.

Predicate logic:
- A symbolic formal language for representing knowledge.
- It is expressive enough to derive new knowledge through mathematical deduction.

Terms:
- Constants: named objects, such as `spot` or `Ellie`.
- Variables: placeholders, such as `x`.
- Predicates: properties or relations, such as `dog(x)` or `eats(x, fruit)`.
- Facts: propositions about concrete objects, such as `dog(spot)`.
- Quantifiers: describe scope, such as all objects or at least one object.

Connectives and quantifiers:
- `forall`: for all.
- `exists`: there exists.
- `or`: disjunction.
- `and`: conjunction.
- `not`: negation.
- `->`: implication.

Example:
- "Spot is a dog" becomes `dog(spot)`.
- "Spot has a tail" becomes `hastail(spot)`.
- "All dogs have tails" becomes `forall x dog(x) -> hastail(x)`.

Past exam example:
- "All animals eat fruit or meat" can be represented as:

```text
forall x animal(x) -> eat(x, fruit) or eat(x, meat)
```

Another likely example:
- "Elephants are not carnivores" needs a predicate for elephant/carnivore and negation, e.g. `forall x elephant(x) -> not carnivore(x)`.

## Resolution Rule

Resolution is an inference method for deriving new knowledge.

Main idea:
- Show that the counter-example/negated statement leads to a contradiction in the knowledge base.
- If the negation creates a contradiction, the original statement must be true.

Requirement:
- The knowledge base must be in conjunctive normal form (CNF).
- The slides describe CNF as propositions with clauses connected by `or`.

Implication conversion:

```text
A -> B
not A or B
```

Resolution method:
- Convert the knowledge base into CNF.
- Negate the statement to be proved and add it to the KB.
- Perform unification by replacing variables with concrete constants.
- Resolve contradictions iteratively.
- If an empty clause/contradiction is reached, the negated statement is false and the original is true.
- If no more contradictions exist, the negated statement may be true, so the original is not proven.

Resolution example:
- KB contains `forall x dog(x) -> hastail(x)`.
- KB contains `dog(spot)`.
- Statement to prove: `hastail(spot)`.
- Convert implication: `not dog(x) or hastail(x)`.
- Add negated statement: `not hastail(spot)`.
- Unify `x` with `spot`.
- Resolve to get `not dog(spot)`.
- This contradicts `dog(spot)`.
- Therefore `hastail(spot)` is true.

Past exam style:
- Given facts like `elephant(Ellie)`, `forall x elephant(x) -> animal(x)`, and `forall x animal(x) -> eats(x, fruit) or eats(x, meat)`.
- Convert implications to CNF.
- Add the negated target statement.
- Unify variables with `Ellie`.
- Resolve as far as the rules allow.

## Natural Language Processing

NLP is the branch of AI that allows machines to process, understand, or generate human language.

Natural language forms:
- Text: books, tweets, emails.
- Speech: audio and video.

Why NLP is hard:
- Human language is ambiguous.
- Meaning depends on context.
- Literal translation can fail without world knowledge.
- Words can have different meanings in different settings.

## NLP Approaches

Symbolic approaches:
- Use rules, logic, grammars, and lexical databases.
- Easier to understand and often reliable.
- Limited when language is messy or highly varied.

Statistical approaches:
- Use probabilistic models.
- N-grams predict based on sequences of words.
- Useful for pattern-based language tasks.

ANN/deep learning approaches:
- Use neural networks such as RNNs and transformers.
- Handle sequential data such as text and speech.
- Drove much recent progress in NLP.

## NLP Pipeline Concepts

Common preprocessing:
- Normalisation.
- Tokenisation.
- Stopword removal.
- Stemming.

Pipeline shape:
- Raw text is transformed into a format suitable for analysis.
- Then features are extracted.
- Then advanced processing or applications are performed.

Text preprocessing examples:
- Normalisation: lowercase, remove punctuation, standardise text.
- Tokenisation: break text into words or phrases.
- Stopword removal: remove common words such as "the", "is", and "and".
- Stemming: reduce words to root forms, such as "running" to "run".

Lecture example:
- Raw message: "Hey wanna win a £10k car? Win a Tesla!"
- After normalisation/tokenisation/stopword work, it becomes a cleaner set of tokens/features for classification.

Feature engineering:
- POS tagging assigns word function: noun, verb, adjective, etc.
- NER identifies named entities such as person, number, organisation, location, or object.
- Bag-of-Words turns documents into a matrix where rows are documents, columns are vocabulary words, and cells are word frequencies.
- TF-IDF measures word importance relative to frequency across documents.
- Word embeddings turn words into vectors of continuous values.

Advanced NLP applications:
- Sentiment analysis.
- Auto-correction.
- Machine translation.
- Question answering.
- Text generation.
- Chatbots.
- Plagiarism checking.
- Text classification.

Use in LLMs:
- Large models still rely on data collection, cleaning, and tokenisation before training.

## NLP Milestones and Examples

Eugene Goostman:
- A 2014 chatbot claimed as a Turing-test pass.
- Used rule-based systems, pre-determined responses, large databases of responses/templates, deception techniques, and storytelling.
- Pretending to be a child helped explain weak answers.
- The slides note lack of transparency about the algorithms.

IBM Watson:
- Used NLP such as POS tagging, NER, syntactic analysis, and semantic analysis.
- Used machine learning such as supervised classification/regression, unsupervised topic grouping, and deep learning/RNNs.
- Used reasoning and inference through rule-based systems and probabilistic reasoning.
- The slide frames Watson as a mixed system: NLP plus machine learning plus KRR.

Google Translate:
- Used traditional statistical methods from 2006 to 2016.
- Since 2017, used neural machine translation.
- Encoder analyses/transfers words into useful representations.
- Decoder generates words based on context.
- Attention focuses on specific parts of the sentence.

Spam email classification:
- Preprocess text to obtain vocabulary from the corpus.
- Convert text to a numerical feature matrix using BoW or TF-IDF.
- Use a classifier such as `MultinomialNB`.
- Train/test split is used as in other ML tasks.
- Example libraries: `TfidfVectorizer`, `train_test_split`, and `MultinomialNB`.

## Large Language Models

LLMs are language models built mainly using transformer neural networks.

Key ideas:
- Trained on vast amounts of text/code/data.
- Contain many parameters.
- Predict likely next tokens based on context.
- Use attention mechanisms to focus on relevant parts of input.

OpenAI/ChatGPT timeline from slides:
- December 2015: OpenAI founded as a non-profit research organisation to advance AI benefiting humanity.
- Founders mentioned include Elon Musk and Sam Altman.
- 2018: Elon Musk stepped down.
- 2019-2023: capped-profit structure and major Microsoft funding.
- November 2022: ChatGPT became a major public AI milestone.
- February 2024: Elon Musk sued OpenAI.

LLM/GenAI examples:
- GPT-2 in 2019.
- GPT-3 in 2020.
- GPT-4 in 2023, described as multimodal.
- Gemini, LLaMA, Copilot, Claude, and others.

Transformers:
- Introduced in "Attention is All You Need" in 2017.
- Good at capturing long-range dependencies in text.
- Became the basis of modern LLMs.
- RNNs were successful on text because text is sequential, but they struggle with long-range context.
- CNNs were successful on images because images have hierarchical spatial structure.
- Transformers use attention to weight the importance of different words based on context.

Generative AI:
- Creates new content such as text, code, images, audio, or other media.
- Learns patterns from training data and produces new outputs.

## LLM Training Process

Data collection and preprocessing:
- Collect web pages, books, articles, code, wiki text, and other sources.
- Data may be licensed or "borrowed", raising legal/ethical questions.
- Clean duplicates, irrelevant content, biased content, and harmful content.
- Apply text preprocessing such as normalisation, tokenisation, stopword removal, and stemming.

Model selection:
- Most modern LLMs use transformer architectures.
- Some model sizes are public, such as GPT-3 having about 175B parameters.
- Many companies do not disclose full model sizes or training details.

Training stages:
- Unsupervised pre-training learns general language patterns from huge text corpora.
- Supervised fine-tuning adapts the model to tasks such as classification, sentiment analysis, and translation.
- Reinforcement learning uses rewards to optimise behaviour; the slides mention recent focus around OpenAI o3 and DeepSeek.

## LLM Concepts

Tokens:
- Units/chunks that LLMs read and write.
- They are not exactly words or letters.
- In English, 100 tokens is roughly 75 words.

Token limit/context window:
- A context window is the amount of text the model can consider.
- Once the limit is reached, earlier conversation may be forgotten or truncated.
- Output also consumes tokens.

Prompt engineering:
- Asking the right question in the right way can affect output.
- Good examples in a prompt can steer model behaviour.

Scaling law:
- Relates model performance to model size, data size, and computation.
- If model size increases, training data also needs to increase.
- Raises questions about data walls, exhausted computation, and where tech companies should invest.
- The lecture phrasing was that model size may increase exponentially for only linear gain.

Temperature:
- Controls randomness/creativity at the output layer.
- Higher temperature gives less likely words more chance, useful for creative writing/brainstorming.
- Lower temperature tends to pick the most likely token, useful for maths/coding.

Self-attention:
- RNNs read word by word and can forget the beginning of long text.
- Transformers look at words in parallel and build a map of relationships between words.

LLM race:
- Models, computation, and data are all bottlenecks.
- The slides mention expensive computation, over 20k H100 GPUs, months of training, and multi-billion-dollar costs.
- Model size increases can have diminishing returns.
- Open vs closed AI is a major strategic issue.

Model table examples from slides:
- GPT-3 Small: 125M parameters, 12 layers.
- GPT-3 Large: 760M parameters, 24 layers.
- GPT-3: 175B parameters, 96 layers.
- Gemini/Bard: 137B parameters listed.
- LLaMA 3: 70B / 405B, 80 / 126 layers.
- DeepSeek-v2-Lite: 15.7B, 27 plus MoE.

## LLM Risks and Limits

Important limitations:
- Hallucination: generating plausible but false output.
- Bias or harmful patterns from training data.
- Lack of transparency about training data and model size.
- Unclear understanding: predicting text is not the same as human understanding.
- Ethical and legal questions about data use.
- Limited understanding of the world.
- Difficulty verifying facts and distinguishing facts from opinions.
- Black-box transparency/explainability problems.
- Lack of originality because outputs can be derivative of training data.

Ethical issues from slides:
- Accountability and responsibility.
- Deepfakes and misinformation manipulating public opinion.
- Biased data amplified by trained models.
- Environmental impact and energy consumption.
- Fairness issues in education, digital access, and AI access.
- Safety, including calls to pause advanced AI development.
- IP and copyright ownership.

Responses/challenges:
- Policymakers should mitigate risks and foster responsible development.
- Developers should improve transparency.
- Algorithms should improve fairness and deal with bias.
- Models should better represent the diverse real world.
- Data should be cleaned to remove biases.

Exam phrasing:
- LLMs are powerful because of transformers, scale, data, and computation, but they still raise questions about understanding, reliability, bias, and accountability.
