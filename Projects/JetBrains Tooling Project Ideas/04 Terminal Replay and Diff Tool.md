# Terminal Replay and Diff Tool

## Thesis
Build a tool that replays terminal sessions, models screen state, and compares two runs visually.

## Why this is strong
It is exactly the kind of developer-tooling work that feels close to editor and terminal integration.

## MVP
- parse ANSI and VT escape sequences
- maintain a terminal screen buffer
- replay recorded sessions frame by frame
- render snapshots
- diff two sessions and highlight where output diverges

## Stretch goals
- record live sessions through a pseudo-terminal
- compare behaviour across emulators
- build a small IntelliJ plugin or Swing viewer
- add a test corpus from tools like git, less, python, and vim

## Suggested stack
- Kotlin or Java
- a terminal parser and custom renderer
- sample shell sessions for testing

## Why I should like this one
It is more unusual than another compiler clone and still very aligned with JetBrains-style tooling work.
