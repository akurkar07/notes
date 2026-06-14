# Project Description

## Goal

Turn the current Pascal-like interpreter/compiler into a compiler that can produce a native executable for an ARM64/AArch64 target.

The repository is already in a good position for this because it has a real frontend:

- lexer;
- parser;
- AST nodes;
- semantic analyser;
- tree-walking interpreter;
- stack-based bytecode compiler;
- virtual machine.

The next project is not to rewrite everything. The sensible path is to keep the frontend and add a new native backend.

## Feasibility

This is feasible, but it is a medium-to-large project rather than a small change.

The good news is that the repo already separates source analysis from execution. `src/bytecode.py` walks the AST and emits bytecode, and `src/vm.py` executes that bytecode with a stack, labels, frames, calls, and returns. That means the project has already crossed the hardest conceptual boundary from "interpreter only" to "compiler pipeline".

The hard part is that the VM still handles many things that real machine code will not handle for free:

- variables are currently resolved by name inside VM frames;
- values are Python objects at runtime;
- procedure and function calls use VM-managed call frames;
- `WRITE` and `WRITELN` use Python `print`;
- strings and reals rely on Python behavior;
- bytecode is stack-based, while ARM64 is register-based.

So the native compiler is realistic, but it needs a carefully limited first version.

## Recommended Target

Start by generating ARM64 assembly, then use an assembler/linker to create the executable.

Best first target:

- Linux ARM64 if using an ARM64 Linux machine, VM, or cross-toolchain;
- macOS ARM64 if using Apple Silicon.

On Windows, producing ARM64 executables is still possible, but it adds toolchain complexity. For learning, it is better to generate assembly first and treat linking as a separate milestone.

## Recommended Architecture

Use this pipeline:

```text
source -> lexer -> parser -> semantic analyser -> AST -> native backend -> ARM64 assembly -> object file -> executable
```

Do not compile the full language immediately.

Start with a restricted native subset:

- integer literals;
- integer variables;
- assignment;
- arithmetic;
- comparisons;
- `IF`;
- `WHILE`;
- simple `WRITELN` for integers.

Then expand from there.

## Implementation Plan

### Phase 1: Assembly output only

Add a new backend, probably `src/arm64.py`, that visits the AST and emits `.s` assembly text.

Initial goal:

```pascal
PROGRAM Demo;
VAR
    x : INTEGER;
BEGIN
    x := 2 + 3;
    WRITELN(x);
END.
```

This phase does not need perfect executables yet. It should prove that the compiler can lower basic AST nodes into assembly-shaped output.

Estimated time: 1-2 weeks.

### Phase 2: Integer executable

Add a command such as:

```text
:compile-arm64 examples/demo.pas
```

It should:

1. parse and semantically analyse the source;
2. emit ARM64 assembly;
3. call `clang`, `as`, or another assembler/linker;
4. produce an executable.

This version can support only integer programs at first.

Estimated time: 3-5 weeks.

### Phase 3: Variables and stack slots

Replace VM-style named variables with stack-frame slots.

For example:

```text
x -> [fp, #-8]
y -> [fp, #-16]
```

This needs a layout pass that assigns each local variable a location before code generation.

Estimated time: 1-2 extra weeks.

### Phase 4: Control flow

Map the current bytecode ideas onto ARM64 labels and branches:

- `IF` becomes conditional branches;
- `WHILE` becomes a loop label, condition branch, body, and jump back;
- `FOR` becomes initialization, condition, body, increment/decrement, and jump back.

The existing bytecode backend is a useful guide here because it already emits labels and jumps.

Estimated time: 1-2 extra weeks.

### Phase 5: Procedures, functions, and recursion

This is the point where the project becomes a real native compiler.

You will need:

- function prologues and epilogues;
- ARM64 calling convention basics;
- argument passing;
- return values;
- local stack-frame layout;
- recursion-safe frames.

Estimated time: 2-4 extra weeks.

### Phase 6: Runtime support

Add a tiny runtime layer for features that are currently handled by Python:

- printing integers;
- printing strings;
- string storage;
- string concatenation;
- real number printing;
- division-by-zero checks.

This runtime can be written in C first and linked with the generated assembly.

Estimated time: 3-6 extra weeks depending on how much of the language is supported.

## Main Risks

- ARM64 calling conventions are unforgiving at first.
- Stack-frame layout will matter much more than it does in the VM.
- Strings are significantly harder than integers.
- Reals require floating-point registers and ABI rules.
- Native debugging is slower than debugging Python bytecode.
- Cross-compiling from Windows may create toolchain friction.

## Best First Version

The best first version is not "the whole interpreter, but native".

The best first version is:

- integer-only;
- no strings;
- no reals;
- no procedures or functions;
- simple `WRITELN`;
- produces assembly;
- optionally links to an executable.

That version is small enough to finish and strong enough to prove the compiler is real.

## Final Deliverables

- `src/arm64.py` native backend;
- command-line mode for native compilation;
- generated `.s` files;
- linked executable output;
- tests comparing interpreter, VM, and native compiler behavior;
- small runtime library for printing and later strings/reals;
- README section explaining supported native features and limits.

## Verdict

This is a very good next project.

The current repository is already more than an interpreter: it has a compiler-like pipeline with AST lowering, bytecode, and a VM. That makes an ARM64 backend genuinely achievable. The important choice is scope. Build a small native integer compiler first, then grow it toward the full Pascal-like language.

