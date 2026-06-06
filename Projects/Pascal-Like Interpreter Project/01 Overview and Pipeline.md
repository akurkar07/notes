# Overview and Pipeline

## What the Project Is

This is a small Pascal-like interpreter built as a learning project. It does not compile programs to machine code. Instead, it parses source text into an AST and then walks that AST directly to execute the program.

## End-to-End Flow

The main execution path is in `src/main.py`.

When a script runs, the project:

1. Reads the source file into a string.
2. Creates a `Lexer`.
3. Creates a `Parser`.
4. Calls `parse()` to build an AST.
5. Runs `SemanticAnalyser.visit(ast)` to validate declarations and types.
6. Runs `Interpreter.visit(ast)` to execute the AST.
7. Prints the final runtime scope and symbol table.

## Role of `main.py`

`src/main.py` is the orchestration layer. It is responsible for:

- loading files
- wiring together the lexer, parser, semantic analyser, and interpreter
- handling interactive commands like `:run`, `:help`, and `:q`
- catching and displaying errors

## Why the Pipeline Matters

The project is organised like a real language toolchain:

- the lexer understands characters
- the parser understands grammar
- the semantic analyser understands meaning and types
- the interpreter understands runtime behaviour

That separation makes the code much easier to maintain than trying to execute directly from text while parsing.
