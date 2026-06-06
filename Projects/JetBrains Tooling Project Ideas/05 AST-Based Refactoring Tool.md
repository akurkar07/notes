# AST-Based Refactoring Tool

## Thesis
Build a refactoring engine over a toy language or a restricted subset of an existing language.

## Why this is strong
This is very IDE-like work. It shows that I can reason about syntax trees, scope, symbol identity, and safe program transformation.

## MVP
- parse source into an AST
- resolve symbols and scopes
- implement safe rename
- preview code changes before applying them
- preserve formatting well enough to be readable

## Stretch goals
- extract variable
- inline constant
- dead code detection
- quick fixes for simple diagnostics
- undo and redo support

## Suggested stack
- ideally Kotlin if I want to stay close to JetBrains-style tooling
- the language core from [[01 Toy Language and IntelliJ Plugin]]

## Why I should like this one
It feels like real editor engineering. If I can explain how I avoid incorrect renames across scopes, that is exactly the kind of technical discussion I would want in an interview.
