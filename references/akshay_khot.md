# Akshay Khot -- Philosophy Reference Card

## Core Philosophy
- **"Audience of One"** -- writes for himself first; if others find value, "that's just icing on the cake"
- **Context over blanket advice** -- "I hate when people give blanket advice on programming techniques"
- **Reality over hype** -- most real-world apps use full-stack frameworks (Rails, Laravel), not React/GraphQL
- **Learn in public with real stakes** -- tests every principle on his own production blog (15-20K monthly visits)
- **"Make the change easy, then make the easy change"** (Kent Beck) -- refactor schema before adding features

## Database & Schema
- **Evolve schemas naturally** -- don't design everything upfront, work just-in-time
- **Defensive column drops** -- add `ignored_columns` first, deploy, then drop migration
- **Surrogate keys over natural keys** -- artificial IDs, natural keys change
- **Model before refactoring** -- wait until you understand domain before replacing JSON with proper tables
- **Build for actual requirements, not speculative** -- no future-proofing
- **One network round-trip** -- use subqueries instead of multiple queries

## Performance
- **Measure before optimizing** -- profile with rack-mini-profiler, optimize surgically
- **Database should do database work** -- compute in DB layer when possible
- **`SELECT *` is a real problem** -- over-fetching consistently causes real memory overhead
- **`includes` is usually safest default** -- but don't blindly use it, `eager_load` when needed
- **Eager loading can make things worse** -- creates memory problems that don't scale

## Controllers & Security
- **Callbacks are useful** -- defend them for offloading non-central concerns
- **Understand callback chain** -- inspect programmatically, especially with deep inheritance
- **Assume unsafe until proven** -- Strong Parameters is real security posture
- **Never `permit_all_parameters` globally**

## Code Organization
- **Model scopes for complex queries** -- easier to read, easier to test
- **Read Rails source code** -- "especially the tests, often leads to discovery of simple and useful patterns"
- **Pragmatic naming** -- don't get stuck on semantic debates

## AI Philosophy
- **"Vibe learning" over "vibe coding"** -- AI as patient mentor, not unsupervised code generator
- **"Not a replacement for thinking"** -- output quality gated by input quality
- **Incremental planning** -- high-level strategy first, step-by-step implementation
- **"Agentic coding with a token efficient language like Ruby on Rails is pure joy!"**

## Key Warnings
- Over-fetching data habitually (SELECT *)
- Blindly using `includes` to fix N+1
- Dropping columns without `ignored_columns` first
- Using `type` as column name (reserved for STI)
- Permitting all parameters globally
- One-shotting large features with AI
- Speculative database design
- Targeting small clients as freelancer ("sell to businesses")

## Memorable Quotes
- "Vibe coding is overrated. Vibe learning, on the other hand, is so underrated."
- "When the schema doesn't properly represent the domain, the damage compounds upward."
- "Reading the Rails codebase, especially the tests, often leads to discovery of simple and useful patterns."
- "Agentic coding with a token efficient language and framework like Ruby on Rails is pure joy!"
- "Never been a better time to be a developer."

## Primary Sources
- writesoftwarewell.com (formerly akshaykhot.com)
- github.com/akshayKhot
- railstack gem (RubyGems)
