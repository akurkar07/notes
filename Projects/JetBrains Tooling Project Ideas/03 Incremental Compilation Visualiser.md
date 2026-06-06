# Incremental Compilation Visualiser

## Thesis
Build a tool that explains what changed in a build, what got invalidated, what recompiled, and why.

## Why this is strong
This is a great developer-tooling project because it sits between compilers, build systems, and user experience.

## MVP
- ingest Gradle or Kotlin build logs
- identify changed files and affected tasks
- reconstruct a simple task and dependency graph
- show cache hits and misses
- display a timeline of what recompiled and why

## Stretch goals
- compare two builds side by side
- highlight expensive invalidations
- suggest likely causes of full rebuilds
- add a small local web UI or desktop UI
- integrate with build scans if possible

## Suggested stack
- Kotlin or Java for parsing and analysis
- a minimal frontend or desktop UI
- Gradle sample projects for test data

## Why I should like this one
It is practical, different from typical student projects, and very obviously about developer productivity rather than generic app building.
