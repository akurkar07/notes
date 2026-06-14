# JetBrains Tooling Project Ideas

## Why these notes exist
These project ideas are meant to match the kinds of internship tracks JetBrains seems to like most:
- IDE and language tooling
- developer experience and terminal tooling
- compiler testing and program analysis
- build systems and incremental compilation

## Recommended order
1. [[01 Toy Language and IntelliJ Plugin]]
2. [[02 Compiler Fuzzer and Differential Tester]]
3. [[03 Incremental Compilation Visualiser]]
4. [[04 Terminal Replay and Diff Tool]]
5. [[05 AST-Based Refactoring Tool]]

## Best first project
If I only start one, I should start [[01 Toy Language and IntelliJ Plugin]].

Why:
- strongest JetBrains signal
- forces Kotlin and JVM tooling work
- combines compiler construction with IDE integration
- easy to extend later with fuzzing, refactoring, or an LSP layer

## General note
The configurable-keyword compiler is still useful, but the real selling points are not the configurable keywords themselves. The parts that matter most are:
- parsing and AST design
- semantic analysis and symbol resolution
- diagnostics and editor feedback
- refactoring, testing, and tooling around the language

## Good sequence
- Start with the language core and plugin.
- Add fuzzing once the parser and semantics stabilize.
- Build a second standalone tooling project if I want broader coverage: either the incremental compilation visualiser or the terminal replay tool.
