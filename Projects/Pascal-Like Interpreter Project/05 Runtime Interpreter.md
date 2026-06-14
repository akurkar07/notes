# Runtime Interpreter

## Purpose

The runtime interpreter in `src/interpreter.py` walks the AST and executes the program directly.

This is a tree-walking interpreter: it does not generate bytecode or machine code first.

## Runtime State

The interpreter stores variable values in:

```python
self.GLOBAL_SCOPE = {}
```

This dictionary maps variable names to actual runtime values.

Because identifiers are uppercased by the lexer, the keys in `GLOBAL_SCOPE` are uppercase too.

## Important Visit Methods

`visit_Assign()`:

- evaluates the right-hand side
- stores the value in `GLOBAL_SCOPE`

`visit_Var()`:

- looks up a variable in `GLOBAL_SCOPE`
- raises `InterpreterError` if it is missing

`visit_BinaryOperation()`:

- evaluates both operands
- performs arithmetic or comparison

`visit_UnaryOperation()`:

- evaluates the child node
- applies unary `+` or `-`

`visit_If()`:

- evaluates the condition
- executes the true branch or false branch

`visit_While()`:

- reevaluates the condition on every iteration
- executes the body while the condition is true

`visit_WriteLn()`:

- evaluates the expression
- prints the result

## Example Runtime Behaviour

The sample file `instructions/control_flow_output.pas` exercises declarations, conditionals, loops, arithmetic, comparisons, and output.

Its final runtime scope is:

```python
{'I': 6, 'SUM': 15, 'KEEP_GOING': True}
```

This is separate from the symbol table used during semantic analysis:

- `GLOBAL_SCOPE` stores runtime values
- the symbol table stores declarations and types

That distinction is one of the key architecture ideas in the project.
