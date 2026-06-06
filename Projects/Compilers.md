---
notion-id: 28c982ca-e761-80e0-8088-e351ef92a555
---
# Top down

Start at the root of the parse tree then visit nonterminals

# Bottom up parse trees

Starts with input streams and recursively shifts one character forward until the symbols read in match a non terminal, reducing them, building up the tree from the bottom

A wider range of texts can be parsed with this method compared to top down.

# LL(1) Parsers

Top-Down that requires one character of lookahead

Parses in O(n) time relative to the derivation length with no backtracking

To build an LL(1) parser:

1. Compute first and follow sets for each symbol
2. compute start set for each rule
3. use sets to build a table to show which rule to apply for each nonterminal + input symbol combination

## First and follow sets 

If A→betaC

If beta derives the empty string then add first(C)

# Bottom Up Parsing

Intermediate steps when parsing from the start symbol to the final sentence are called sentential forms

Works in reverse to top down parsing by starting at a given character and working out what the one before it must have been. 

A handle is a pair of a rule and an index into a sentential form, A→B,k means the last k tokens of Yi form B.

Apply as many reductions when parsing input in one pass as possible

# LR(1)

Left-to-right scan, Reverse rightmost derivation, 1 token of lookahead

Completes a bottom up parse in O(n) time

Repeatedly pushes symbols onto a stack until the top of the stack forms a handle

Table based - Action table and goto table

closure function is for terminals, goto is for nonterminals

create a different set for each grammar symbol, im guessing so the grammar cannot be parsed ambiguously 

jsmachines.sourceforge.et/machines/r1.html

# IR

-

# Translation

## Syntax-Directed Translation

From Parse tree to AST

Translates one representation of a program into another by converting source code into a suitable IR to work with

Called syntax-directed bc it is a method guided by the source code’s syntax

AST can be built at the same time as the parse tree

Representing loops and conditionals with linear IR is harder, but AST is easier

## Defining translations

Nearly all translation schemes are recursive

The representation of a given grammar nonterminal depends on the representations of other symvols that go into it

SExpr → List → ( ListContent )

In the above production, the representation of the top-level SExpr depends on the list, which depends on the list content

## Embedded Actions

yacc LALR(1) parser generator. Grammar writer defines snippets of code that the parser generator insets into its code for parsing different rules

Define the value of a node in terms of its arguments

## Visitor pattern

 is a design patter thant allos defining custom actions to take for different parts of a data striucture without having to modify the data structure itself

Eg, define a method to execute for each element of a list

Eg, define a method to execute for each node of a parse tree

Create a Visitor class and define methods for visiting each distinct node

You can extend a generic visitor class to define your own behaviour

## Auxiliary Data Structures

Translation often needs extra info, eg, the symbol table

Depending on the paradigm, this is done with global variables or class members

## Memory Layout

Compiler must workout where to store all the data and for how long

Generally three types of lifetime:

Static data stored in a global area below the first stack frame

Automatic data stored within the stack fram of its function/scope

Irregular data ends up on the heap

## Storage layout

Amount of memory needed for a value depends on its type

Individual values are simple to store

Arrs are stored as seqs of adjacent values contiguously

Each namespace gets its own separate memory area

Entities can be loaded with a base address and an offset, basically uses offset addressing

Once acc location of base is determined, compiler can assign absolute value for each address

# Code Shape

Code gen done in multiple stages

A naive first pass to get things roughly right and one/more optimisation passes for improvement

Code shape is the general set of rules and heuristics for carrying out the initial pass

Same techniques apply whether lowering to a linear IR or producing the final binary

Code shape is a template for general concepts in program structure, eg, accessing memory

## Addresses

Addresses should generally be kept abstract until the last moment as sections of code may be rearranged or optimised out

Where possible, all symbols should have relative addresses based on a known location like the base of the current stack frame

Code for accessing memory requires generating code to calculate the address and generating code to load data from the address

Symbol table should record storage location and size of variables

Since arrays are stored contiguously, accessing arrays is the same but relative to the base address and index as an offset.

Row-major order assumes we iterate through rows when accessing arrays

Column-major order assumes we iterate through columns

## Binary Operations

To generate a binary operation

Optimisations may later let us skip some steps

With logical operations, you can implement short-circuiting, where the evaluation of an expression stops early when the entire expression’s truth value is known

This is not an optimisation because the short-circuited values arent evaluated

## Control Flow

In linear code, we jump over the code that isn’t used in conditionals

To do this, label first instruction of the true block, first instruction of the false block and next instruction after the false block

Loops are simpler, the label points back to the start of the loop and evaluate whether the loop should be executed again by comparing some value, if not jump to end label.

Switch statements requires code to test the input and branch to the appropriate section. Larger statements may generate a lookup table or a binary search to find the correct destination per case

## Procedures

Linkage (aka calling) convention is the agreed upon standard for generating procedure call

Four basic components:
