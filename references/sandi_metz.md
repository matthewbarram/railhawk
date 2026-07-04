# Sandi Metz -- Philosophy Reference Card

## Core Philosophy
- **Purpose of design is economic**: reduce cost of change
- **Message-centric OOP**: "You don't send messages because you have objects; you have objects because you send messages"
- **TRUE code**: Transparent, Reasonable, Usable, Exemplary
- **Design for changeability**, not perfection

## The Sandi Metz Rules
1. Classes ≤ 100 lines
2. Methods ≤ 5 lines
3. No more than 4 parameters per method (hash params count)
4. Controllers instantiate only 1 object (views know only 1 instance variable)
5. No more than 2 class names per controller action

**Escape clause**: break rules if your pair agrees. These are forcing functions, not laws.

## Refactoring
- **"Make the change easy, then make the easy change"** -- two-step approach
- **Shameless Green**: simplest code first, tolerate duplication, wait for patterns to emerge
- **Flocking Rules**: systematically turn duplication into abstractions, one line at a time
- **Refactor under green only** -- tests are the safety net

## Duplication vs Wrong Abstraction
- **"Duplication is far cheaper than the wrong abstraction"**
- DRY too early = committing to wrong theory
- Fix wrong abstraction: inline it back, re-duplicate, re-extract correctly
- "Abstractions are found, not created"

## Testing
- **Messages grid**: incoming/outgoing × query/command → what to test
- **Don't test private methods** -- no safety, breaks on refactor
- **Don't test outgoing query messages** -- no public side effects
- **Mock outgoing command messages** -- verify message was sent
- **Stubs for queries, mocks for commands**
- **Contract tests** keep test doubles in sync
- Test interface, not implementation

## Design Heuristics
- **Squint test**: changes in shape (indentation) = complexity; changes in color (syntax) = mixed abstraction levels
- **Depend on things that change less often than you do**
- **Inheritance**: shallow/wide or deep/narrow, never both. For specialization, not code sharing.
- **Composition + DI**: Isolate variable → Name concept → Define role → Inject player
- **Avoid type-checking conditionals** -- use polymorphism instead

## Key Warnings
- Premature DRY/abstraction
- Testing private methods
- Type/category/style variables controlling branches
- Subclasses raising "not implemented"
- Deep AND wide inheritance
- Hiding mess in private methods with poor names
- Big Up Front Design
- Conflating commands and queries

## Primary Sources
- "Practical Object-Oriented Design in Ruby" (POODR)
- "99 Bottles of OOP"
- "All the Little Things" (RailsConf 2014)
- "Nothing is Something" (RailsConf 2015)
- "The Magic Tricks of Testing" (RailsConf 2013)
- sandimetz.com
