# Lexer

## Purpose

The lexer in `src/Lexer.py` turns raw source text into tokens. It works one character at a time and groups characters into meaningful units that the parser can consume.

## What It Tracks

The lexer stores:

- `self.pos`: current index in the text
- `self.current_char`: current character
- `self.line`: current line number
- `self.column`: current column number

These are mainly used for scanning and error reporting.

## Main Responsibilities

The lexer:

- skips whitespace
- skips `{ ... }` comments
- scans integers and real numbers
- scans identifiers
- recognises reserved keywords
- matches operators and punctuation

## Keywords and Identifiers

Identifiers are read by `_id()`. After collecting the identifier text, the lexer uppercases it and checks `RESERVED_KEYWORDS` in `src/tokens.py`.

That means:

- keywords like `PROGRAM` and `WHILE` are recognised correctly
- identifiers are stored in uppercase internally
- the language is effectively case-insensitive

For example, `sum`, `SUM`, and `SuM` all become the same internal identifier.

## Numbers

`number()` scans:

- integer literals like `123`
- real literals like `12.5`

It returns either `INTEGER_CONST` or `REAL_CONST` tokens.

## Operators

The fixed-symbol operators are defined in the `OPERATORS` map.

Examples:

- `:=`
- `<=`
- `>=`
- `<>`
- `+`
- `-`
- `*`
- `/`

`match_operator()` tries two-character operators before one-character operators, which is important so something like `:=` is not split into `:` and `=`.

## Errors

If the lexer sees a character that does not belong to any valid token, it raises `LexerError`.

This stage is only responsible for lexical correctness. It does not know whether the overall program makes grammatical or semantic sense.
