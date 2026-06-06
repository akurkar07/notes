# AI Basics

## What AI Means

Artificial intelligence is about building computational systems that perform tasks normally associated with human intelligence.

Useful abilities to mention:
- Learning.
- Reasoning.
- Problem solving.
- Perception.
- Decision making.
- Adaptation.

Classic definition:
- John McCarthy described AI as the science and engineering of making intelligent machines.

Other useful definitions from the intro slides:
- AI deals with intelligent behaviour, learning, and adaptation in machines.
- AI can be described as trying to create a computer mind that can think like a human.
- A modern broad definition is the capability of computational systems to perform tasks associated with human intelligence.

Exam answer:
- AI is not just one technique. It is a field containing symbolic reasoning, search, machine learning, NLP, game playing, robotics, and other methods.

## Weak AI vs Strong AI

Weak AI:
- Handles a specific task or narrow domain.
- Does not have self-awareness.
- Exists now.
- Examples: Siri, AlphaZero, spam filters, recommendation systems.

Strong AI / AGI:
- Would have broad, general-purpose intelligence.
- Would learn and reason across many domains like a human.
- Self-awareness is sometimes claimed as part of the idea.
- Still theoretical.

Key point:
- A system can be very good at one intelligent task without being generally intelligent.

## Top-Down vs Bottom-Up AI

Top-down AI:
- Also called deductive or symbolic AI.
- Humans model the problem and write rules or representations.
- The system uses explicit knowledge to reason.
- Examples: expert systems, knowledge representation, search, logic systems.

Bottom-up AI:
- Also called inductive or machine learning based AI.
- The system learns from data.
- The model discovers patterns rather than being fully hand-coded.
- Examples: supervised learning, neural networks, deep learning.

Useful comparison:
- Top-down AI depends on hand-built knowledge.
- Bottom-up AI depends on data, model choice, training, and computation.

## AI Milestones

Useful timeline:
- 1943: early neural network ideas from McCulloch and Pitts.
- 1950: Turing test paper.
- 1956: term "AI" coined at Dartmouth.
- 1950s: early machine translation, including Russian to English experiments.
- 1970s: AI winter after early optimism failed to meet expectations.
- 1997: Deep Blue defeated Garry Kasparov.
- 2011: IBM Watson won Jeopardy.
- 2014: Eugene Goostman chatbot was claimed to have passed a Turing-test-style event.
- 2016: AlphaGo defeated Lee Sedol.
- 2022: ChatGPT became a major public AI milestone.
- Recent LLM examples mentioned: GPT models, Gemini, Claude, LLaMA, and DeepSeek.

Key exam point:
- AI history has cycles of optimism, limits, winter, and renewed progress.

Machine translation example:
- Early literal translation struggled because translation needs context and knowledge.
- The lecture example was that "the spirit is willing but the flesh is weak" could be mistranslated as something like "the vodka is good but the meat is rotten".
- Point: language processing is not just word substitution; it needs understanding, context, and background knowledge.

AI winter point:
- Early neural network work hit limits because simple neurons/perceptrons could not implement important functions.
- The broader lesson is that AI progress is constrained by models, computation, data, and over-optimistic assumptions.

## Turing Test

The Turing test asks whether a machine can imitate human conversation well enough that an interrogator cannot reliably tell which participant is the machine.

Turing background from the slides:
- Turing was a mathematician, philosopher, code breaker, and major figure in computer science.
- His work included the Turing machine in "On Computable Numbers".
- He helped devise the Bombe for Enigma decryption.
- His 1950 paper proposed the imitation-game style test for machine intelligence.
- In the lecture version, if the machine fools the interrogator 30% of the time, it is considered intelligent.
- Example question used: "What is 35,076 divided by 4,567?" A human-like answer might hesitate, while a machine-like answer may give the exact decimal immediately.

Why it matters:
- It gives an operational test of intelligent behaviour.
- It avoids needing a perfect definition of "thinking".
- It focuses on observable behaviour.

Limitations:
- Passing as human is not the same as understanding.
- It rewards imitation, not necessarily intelligence.
- A chatbot can appear convincing in a narrow interaction.
- It may reward deception or human-like errors rather than reliable reasoning.

Real-life Turing-test-like examples:
- Online/AI games.
- Chatrooms.
- Content generators.
- AI art generators, including music, painting, poetry, and composing programs.

Exam phrasing:
- The Turing test tests whether a system acts intelligently, not whether it has a mind.

## Chinese Room Experiment

The Chinese room is a thought experiment by John Searle.

Basic idea:
- A person who does not understand Chinese sits in a room.
- They follow a rule book for manipulating Chinese symbols.
- To outsiders, the room may appear to understand Chinese.
- Internally, there may only be symbol manipulation without understanding.

Why it matters:
- It challenges the idea that correct input-output behaviour proves understanding.
- It argues that syntax is not the same as semantics.

Exam phrasing:
- A system may behave as if it understands language while only following formal rules.

Link to NLP/LLMs:
- The Chinese room is useful when discussing chatbots and LLMs.
- A model can produce appropriate language output without proving that it understands meaning in the human sense.

## Predictions About AI

The intro slides used old predictions to show both ambition and overconfidence.

Examples:
- Herbert Simon predicted in 1957 that a computer would be chess champion within 10 years.
- Newell and Simon made similar optimistic claims about chess.
- Turing suggested that at some stage machines might take control.
- Ray Kurzweil wrote about intelligent machines and later predicted very rapid progress toward superintelligence.

Exam point:
- AI predictions are often useful historically, but they should be treated critically because the field has repeatedly overestimated short-term progress.

## Responsible and Ethical AI

AI creates ethical problems because traditional ethics often assumes human decision makers.

Issues to mention:
- Trolley-dilemma style moral decisions.
- Privacy and security of data.
- Bias and fairness.
- Transparency and explainability.
- Accountability and responsibility.
- Safety.
- Effects on jobs and automation.
- Data degradation, contamination, and loss of diversity.
- Computational cost and efficiency.

Useful exam answer:
- Ethical AI is not just about whether the model works. It is also about who is affected, whether decisions are fair, whether data is used responsibly, and who is accountable when harm occurs.

## Course Content Map

The course is organised around:
- Fundamental issues: AI history, milestones, experiments, and definitions.
- Machine learning: ANN, regression, decision tree, data and process.
- Intelligent systems: Bayes rule, KRR, NLP, and LLMs.
- Search techniques: combinatorial explosion, BFS, DFS, UCS, A*, and game playing.

Reference textbook chapters mentioned:
- Russell and Norvig, Artificial Intelligence: A Modern Approach.
- Chapter 1.1 and 1.2: introduction and philosophy.
- Chapter 3: solving problems by search.
- Chapter 3.5: informed/heuristic search.
- Chapter 5.3: alpha-beta tree search.
- Chapter 7.4: knowledge representation and reasoning.
- Chapter 12.5: Bayes rule.
- Chapter 19.2: supervised learning.
- Chapter 19.3: decision tree.
- Chapter 19.6: regression.
- Chapter 23: natural language processing.

Computing-side reference:
- Python Data Science Handbook by Jake VanderPlas.
- Jupyter Notebook and Anaconda were used for computing sessions.

Course workload facts from slides:
- Lectures: 18 hours.
- Computing sessions: 14 hours including preparation.
- Coursework: about 25 hours.
- Exam revision/self-study: about 38 hours.
- Office hours: about 5 hours.
