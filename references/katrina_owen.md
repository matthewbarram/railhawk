# Katrina Owen -- Philosophy Reference Card

## Core Philosophy
- **"Therapeutic refactoring"** -- refactoring as calming practice, not just technique. "It made me feel better. Whenever I freak out, I stop thinking well, and refactoring was the one thing that brought me back."
- **Abstractions are discovered, not invented** -- "A good abstraction feels obvious in hindsight -- it was already there; you just needed to clear away noise."
- **"Read lines like a story"** -- high-level methods narrate in domain terms, implementation details in well-named private methods
- **"Don't name the noise"** -- name whole concepts, not fragments and shards of ideas
- **Defer naming until you understand** -- "The easiest time to get the names wrong is at the beginning, when you understand the least."

## Naming Principles (from "One Undo")
1. **Implementation-based naming (BAD)** -- fragments of implementation that go stale. "You end up with a method named 'blue' that returns the hex code for red."
2. **Structural naming (BAD)** -- technically correct but perfectly unhelpful (`recurring_line`, `incremental_sentence`).
3. **Domain-concept naming (RIGHT)** -- name the whole concept in the problem domain. Not "phrases" or "lines" but `motivation`.

## Refactoring Method
- **Characterization tests** -- reverse-engineer tests from error messages: send stub, let errors tell you what inputs are missing, copy-paste expected output as assertion
- **Small safe steps** -- "Safe steps don't break your test suite." Tests must exist before refactoring.
- **Parallel implementations** -- build new code alongside old (unconnected) until understood, then swap
- **Separate template from data first** -- defer naming by using formatting to split static from dynamic
- **"Conditionals are a useful transitory tool"** -- don't rush to eliminate them before understanding the domain
- **"Sameness is a trap"** -- duplicated code that looks similar but isn't conceptually the same leads to wrong abstractions
- **Focus on differences, not similarities** -- "Identify the smallest difference and see if you can make it go away. Then ignore it and look at the remaining differences."
- **Method Object pattern** (Fowler) -- isolate big method into its own class, extract at consistent levels

## Code Review
- **Comments → Methods**: if you write a comment explaining what code does, extract it into a method with the comment as the name. Method names don't go stale; comments do.
- **Two levels of abstraction**: high-level orchestration (reads like story) vs low-level details (formatting, parsing). Never mix them.
- **Invert dependencies**: make data into objects you can send messages to. `critter.qualifier` not `qualifier(critter)`.

## Things She Rejects
- Premature naming (name after understanding, not before)
- Abstracting code that looks similar but represents different concepts
- Rushing to eliminate conditionals before domain is clear
- "Maximum design pattern density" as a goal
- Implementation-fragment names that go stale

## Memorable Quotes
- "Don't name the noise; don't name the fragments and slivers and shards of ideas -- name the whole concepts."
- "It should feel like you're discovering abstractions, not inventing them."
- "The easiest time to get the names wrong is at the beginning of refactoring, when you understand the least."
- "Sameness is a trap; it's a distraction."
- "I just realized that it made me feel better. Refactoring was the one thing that brought me back."
- "Refactoring is not about reaching maximum design pattern density."

## Primary Sources
- "One Undo" -- RubyConf AU 2016, multiple conferences
- "Therapeutic Refactoring" -- Cascadia Ruby 2012, Oredev 2012, ConFoo 2013
- "Here Be Dragons" -- GitHub talk on naming in code
- 99 Bottles of OOP sample chapters (with Sandi Metz)
- Ruby Rogues #69 interview
