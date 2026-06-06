# Grammar and Current Limits

## Implemented Grammar Shape

The current grammar is documented in `grammar.txt` and implemented in `src/Parser.py`.

Important language features include:

- `PROGRAM name;`
- `VAR` declarations
- `INTEGER`, `REAL`, `BOOLEAN`
- assignments with `:=`
- `BEGIN ... END`
- `IF ... THEN ... ELSE`
- `WHILE ... DO`
- `WRITELN(...)`

## Core Grammar Rules

```text
program : PROGRAM variable SEMI block DOT
block : declarations compound_statement
declarations : VAR (variable_declaration SEMI)+ | empty
variable_declaration : ID (COMMA ID)* COLON type_spec
type_spec : INTEGER | REAL | BOOLEAN
compound_statement : BEGIN statement_list END
statement : compound_statement
          | assignment_statement
          | if_statement
          | while_statement
          | writeln_statement
          | empty
assignment_statement : variable ASSIGN expression
if_statement : IF expression THEN statement (ELSE statement)?
while_statement : WHILE expression DO statement
writeln_statement : WRITELN LPAREN expression RPAREN
```

## Current Limits

The project is intentionally small right now. Current limitations include:

- no procedures or functions
- no nested scopes
- no dedicated `SemanticError` type yet
- comparison operators currently only accept numeric operands
- declarations do not automatically initialise runtime variables

## Good Next Extensions

Natural next steps for the project would be:

1. add nested symbol tables
2. add procedures/functions
3. split semantic errors from interpreter errors
4. add boolean operators like `AND`, `OR`, and `NOT`
5. add clearer handling for uninitialized variables

## Why the Current Scope Is Fine

For a learning interpreter, the current feature set is a good stopping point. It is large enough to show the full structure of a language implementation without yet needing the extra complexity of procedure calls, activation records, or scoped environments.
