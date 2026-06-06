# Compiler Fuzzer and Differential Tester

## Thesis
Build a tool that generates programs, runs them through an interpreter and compiler, compares outputs, and shrinks failing cases.

## Why this is strong
This is very close to the kind of compiler testing and program analysis work that JetBrains appears to value.

## MVP
- generate random but valid programs for the language
- run them through the interpreter and compiler
- compare outputs or final states
- detect crashes, hangs, or semantic mismatches
- shrink failing programs to minimal repro cases
- save a corpus of interesting failures

## Stretch goals
- grammar-guided generation
- mutation-based fuzzing
- coverage-guided prioritization
- dashboard for failures and reductions
- CI integration

## Suggested stack
- Python or Kotlin for the fuzzer harness
- the language core from [[01 Toy Language and IntelliJ Plugin]]
- property-based testing tools if useful

## Why I should like this one
It is algorithmic, technical, and genuinely useful. It also makes the language project feel much more serious because it shows testing discipline, not just implementation.
