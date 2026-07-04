# José Valim -- Philosophy Reference Card

## Core Philosophy
- **FP is means to end** -- "not a goal in the Erlang VM. It is a means to an end."
- **Fault-tolerance, concurrency, maintainability** are the real objectives
- **Immutability eliminates root causes** -- "if I can disappear with the root cause of the problem altogether -- I'll take that"
- **Extensibility over constant change** -- small language core, ecosystem grows via macros/protocols
- **Language design patience** -- "The important thing about the prototype is the lessons you learn from it"

## Domain-Driven Design
- **Phoenix is not your app** -- business logic functions independently of web framework
- **Contexts are simple** -- "A context is a module and functions, that's it. Don't bring more to it than it is."
- **Microservices = operational, not architectural** -- BEAM processes are already isolated "nanoservices"
- **Ecto's explicit Repo pattern** -- direct rejection of ActiveRecord's implicit data access

## Explicit Contracts & Testing
- **"Mock is a noun, never a verb"** -- create new entities implementing contracts
- **Golden Rule**: every test with mock must have integration test covering that mock
- **Explicit contracts via behaviours** -- `@behaviour` + `@callback`, complexity visible in one place
- **Pass dependencies as arguments** -- with defaults, not config files
- **Testing as code design** -- "A test is a consumer of your API like any other code"
- **Unit tests = behaviour, integration tests = stack works, not all outcomes**

## What He Left Behind from Rails
- Mutable state → immutability by default
- Thread-safety bolted on → lightweight actor processes
- Web-framework-first → general-purpose extensible language
- "Magic" → explicit contracts, behaviours, data access
- ActiveRecord (behavior+state) → Ecto (plain structs + Repo + changesets)
- Controllers/Models/Views → Contexts as domain boundaries
- Global mocking → mocks as nouns with explicit @behaviours
- Fat models → schemas are plain data, changesets separate validation

## Things He Rejects
- Thread-safety as bolt-on (Rails' mutex around everything)
- "Magic" as substitute for understanding (blames Rails community for spreading it)
- Fat models / ActiveRecord as god objects
- Implicit data access (nothing touches DB without explicit `Repo`)
- Web-framework-first language design
- Implicit global mocking (breaks concurrent test execution)

## Memorable Quotes
- "I can fix problems, but if I can disappear with the root cause of the problem altogether -- I'll take that."
- "A test is a consumer of your API like any other code you write."
- "Your application will always have complexity, so always make it as explicit as you can."
- "If the language is extensible... the language doesn't need to change."

## Primary Sources
- dashbit.co/blog
- plataformatec.com.br blog
- "Mocks and Explicit Contracts" (2015)
- "Elixir in Times of Microservices" (2015)
- ElixirConf EU 2024: "Gang of None"
- Semaphore interview
