# Toy Language and IntelliJ Plugin

## Thesis
Build a small typed language and an IntelliJ plugin for it.

## Why this is strong
This is probably the single best JetBrains-style portfolio project I could build because it combines:
- compiler construction
- static analysis
- editor diagnostics
- IntelliJ Platform work

## MVP
- define a small language with variables, functions, control flow, and simple types
- build a lexer, parser, and AST
- implement symbol resolution and semantic checks
- produce source-ranged diagnostics
- create an IntelliJ plugin with syntax highlighting and parser errors
- add go-to-definition and hover info

## Stretch goals
- rename refactoring
- code completion
- formatter
- simple interpreter or bytecode backend
- LSP bridge so the language tools can also run outside IntelliJ

## Suggested stack
- Kotlin
- Gradle
- IntelliJ Platform SDK
- hand-written parser or ANTLR

## Good repo shape
- one repo for the language core
- one repo for the IntelliJ plugin

## Why I should like this one
It feels like a real tools project rather than a toy app. It gives me something concrete to talk about in terms of ASTs, symbol tables, diagnostics, and editor behaviour.
