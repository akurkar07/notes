# Semantic Analysis

## Purpose

The semantic analyser in `src/SemanticAnalyser.py` checks whether a parsed program is meaningful before the interpreter executes it.

This stage answers questions like:

- has a variable been declared?
- has it been declared twice?
- does an assignment use compatible types?
- are operator operands valid?
- do `IF` and `WHILE` conditions evaluate to `BOOLEAN`?

## Symbol Table

Semantic analysis uses the `SymbolTable` from `src/tokens.py`.

The symbol table stores:

- built-in types: `INTEGER`, `REAL`, `BOOLEAN`
- declared variables as `VarSymbol` objects

At the moment, this is a single flat scope rather than nested scopes.

## Declaration Checking

`visit_VarDecl()`:

1. resolves the declared type
2. checks whether the variable already exists
3. inserts a `VarSymbol` into the symbol table

This catches duplicate declarations early.

## Type Rules

Arithmetic operators:

- require numeric operands
- `DIV` requires both operands to be `INTEGER`
- `/` always yields `REAL`
- `+`, `-`, `*` yield `INTEGER` only when both operands are `INTEGER`, otherwise `REAL`

Comparison operators:

- currently require numeric operands
- yield `BOOLEAN`

Unary operators:

- require a numeric operand

## Assignment Rules

`visit_Assign()` checks that:

- the target variable exists
- the right-hand side has a compatible type

The current compatibility rule allows:

- exact matches
- widening from `INTEGER` to `REAL`

So assigning an integer expression into a real variable is allowed, but assigning a real expression into an integer variable is not.

## Control Flow Checks

`visit_If()` and `visit_While()` require the condition type to be `BOOLEAN`.

That means conditions must already be proper boolean expressions such as:

```pascal
i <= 5
```

rather than just a numeric expression.
