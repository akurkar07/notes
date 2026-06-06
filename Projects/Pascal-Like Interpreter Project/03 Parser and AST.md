# Parser and AST

## Purpose

The parser in `src/Parser.py` consumes tokens from the lexer and builds an abstract syntax tree. The AST is defined in `src/nodes.py`.

This is the point where a flat token stream becomes a structured representation of the program.

## Recursive-Descent Parsing

The parser is a recursive-descent parser. Each method corresponds closely to a grammar rule, for example:

- `program()`
- `block()`
- `declarations()`
- `statement()`
- `expression()`
- `term()`
- `factor()`

The parser uses one-token lookahead through `self.current_token`.

`eat(expected_type)` checks that the current token is the expected kind and then advances to the next token. If not, it raises `ParserError`.

## Expression Precedence

Precedence is encoded by how the parser is split:

- `expression()` handles comparisons
- `arithmetic_expr()` handles `+` and `-`
- `term()` handles `*`, `DIV`, and `/`
- `factor()` handles literals, variables, unary operators, and parenthesised expressions

So multiplication and division bind tighter than addition and subtraction.

## Statement Parsing

`statement()` decides which kind of statement to parse based on the current token.

The parser currently supports:

- compound statements with `BEGIN ... END`
- assignments
- `IF ... THEN ... ELSE`
- `WHILE ... DO`
- `WRITELN(...)`
- empty statements through `NoOp`

## AST Nodes

The AST node classes in `src/nodes.py` represent the meaningful structure of the program.

Important node types:

- `Program`
- `Block`
- `VarDecl`
- `Type`
- `Compound`
- `Assign`
- `Var`
- `If`
- `While`
- `WriteLn`
- `BinaryOperation`
- `UnaryOperation`
- `IntegerNode`
- `RealNode`
- `BooleanNode`
- `NoOp`

## Why the AST Matters

The AST strips away unnecessary grammar detail and keeps the structure the later passes care about.

For example, a `While` node directly stores:

- the loop condition
- the body statement or block

That is much easier for semantic analysis and execution than working directly with raw tokens.
