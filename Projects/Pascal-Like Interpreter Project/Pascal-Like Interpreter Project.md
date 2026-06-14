# Pascal-Like Interpreter Project

This project is a small Pascal-like interpreter written in Python. It is split into a classic language-tooling pipeline:

`source text -> Lexer -> Parser -> AST -> SemanticAnalyser -> Interpreter`

## Notes

- [[01 Overview and Pipeline]]
- [[02 Lexer]]
- [[03 Parser and AST]]
- [[04 Semantic Analysis]]
- [[05 Runtime Interpreter]]
- [[06 Grammar and Current Limits]]

## Project Structure

- `src/main.py`: entry point and orchestration
- `src/Lexer.py`: tokenization
- `src/Parser.py`: recursive-descent parsing
- `src/nodes.py`: AST node definitions
- `src/visitor.py`: shared visitor dispatch
- `src/SemanticAnalyser.py`: declaration and type checks
- `src/interpreter.py`: runtime execution
- `src/tokens.py`: token definitions, symbol table classes, errors

## Why This Structure Works

The main strength of the project is separation of concerns. Each stage produces a cleaner representation for the next stage to work on, which makes the interpreter easier to understand and extend.
