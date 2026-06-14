# Project Description

## Goal

Build your own simplified version of C's dynamic memory allocator. The project should teach:

- how heap allocation works;
- how `malloc` finds and returns blocks of memory;
- how `free` tracks reusable memory;
- why fragmentation happens;
- how alignment, metadata, splitting, and coalescing work.

The finished project does not need to replace the real system allocator. It should be a learning allocator with clear tests, diagrams, and explanations.

## Recommended Language

Use **C**.

C is the best language for this project because `malloc` is part of C's standard library, and the allocator model is naturally expressed with:

- raw pointers;
- byte-level memory layout;
- structs for block metadata;
- manual alignment;
- direct interaction with `sbrk`, `mmap`, or a fixed-size simulated heap.

For a first version, use a **fixed-size simulated heap** instead of calling the operating system directly. For example, allocate a large static byte array and manage memory inside it:

```c
static unsigned char heap[1024 * 1024];
```

That keeps the project safer and easier to debug. Once the allocator works, add an optional version using `sbrk` or `mmap`.

## Why Not Another Language?

Rust would be interesting, but it adds ownership and unsafe-code complexity before the allocator concepts are clear.

C++ would work, but it brings extra abstraction and `new`/`delete` concerns.

Python is useful for writing a visualiser or test generator, but not for implementing the allocator itself.

## Rough Timeline

### Minimum version: 1-2 weeks

This version should include:

- simulated heap;
- `my_malloc`;
- simple block metadata;
- basic `my_free`;
- tests for allocating and freeing memory.

### Good version: 3-4 weeks

This version should include:

- free list;
- block splitting;
- block coalescing;
- alignment;
- `calloc`;
- `realloc`;
- unit tests;
- debugging output that prints the heap layout.

### Strong portfolio version: 5-6 weeks

This version should include:

- benchmarks against simple allocation patterns;
- fragmentation measurements;
- diagrams or a small visualiser;
- clear README;
- edge-case tests;
- optional `mmap` or `sbrk` backend.

## Suggested Implementation Plan

1. Create a static heap array and a pointer to the first free byte.
2. Implement a bump allocator that only moves forward.
3. Add block headers storing size, free/used state, and next block.
4. Implement `free` by marking blocks reusable.
5. Use a free list to reuse freed blocks.
6. Split large free blocks when serving smaller requests.
7. Coalesce adjacent free blocks to reduce fragmentation.
8. Add alignment so returned pointers are valid for common C types.
9. Implement `calloc` by allocating and zeroing memory.
10. Implement `realloc` by resizing in place where possible, otherwise allocating a new block and copying data.

## Final Deliverables

- `my_malloc.c` and `my_malloc.h`
- tests for allocator behavior
- heap layout debug printer
- README explaining the allocator design
- short writeup comparing bump allocation, free lists, splitting, and coalescing

