---
name: railhawk
description: Use when reviewing Ruby on Rails code, architecture decisions, or design proposals — Railhawk watches your Rails code with the sharp eyes of 15 Ruby/Rails thought leaders (DHH, Sandi Metz, Avdi Grimm, Matz, and more). Triggers on requests for code review, architecture review, Rails best-practices audit, or when asking "what would [leader] think of this code?"
---

# Rails Philosophy Review

Review Rails code and design proposals against the philosophies of 15 Ruby/Rails thought leaders. The skill does active web searches for each leader's specific advice on the code under review, then produces a structured report showing where code conforms to or diverges from their philosophies.

## Tiered Review Model

### Core Panel (always consulted)
These 5 leaders form the philosophical foundation. Their lenses apply to every review:

| Leader | Primary Lens |
|--------|-------------|
| **DHH** | Rails conventions, complexity, no-build philosophy, monoliths |
| **Sandi Metz** | OOP design, SOLID, class/method sizing, testing |
| **Avdi Grimm** | Confident code, error handling, method design |
| **Matz** | Ruby aesthetics, readability, programmer happiness |
| **Xavier Noria** | Code organization, naming, autoloading, conventions |

### Topic-Matched Specialists
Auto-select from these 10 based on code being reviewed:

| Leader | Primary Lens | Triggered When |
|--------|-------------|----------------|
| **Aaron Patterson** | Performance, internals, memory | Code involves query optimization, N+1, memory, GC tuning |
| **José Valim** | DDD, functional patterns, explicitness | Code involves service objects, domain design, concurrency |
| **Nate Berkopec** | Rails performance, server tuning | Code involves caching, server config, database performance |
| **Eileen Uchitelle** | Framework internals, upgrades, multi-DB | Code involves migrations, upgrades, multiple databases |
| **Noel Rappin** | Testing, Hotwire/Stimulus | Code involves system tests, Hotwire, frontend patterns |
| **Justin Searls** | Test doubles, isolated testing | Code involves mocking, unit testing, test design |
| **Paweł Urbanek** | Architecture, modularization | Code involves large-scale architecture, service extraction |
| **Akshay Khot** | Rails patterns, code organization | Code involves design patterns, code structure |
| **Chris Oliver** | SaaS patterns, Hotwire, Jumpstart | Code involves billing, auth, multitenancy, deployment |
| **Lee Robinson** | React/Next.js, modern JS, performance | Code involves React/Next.js frontend, API mode, SPA |

## Execution Flow

### Step 1: Understand What's Being Reviewed

Identify:
- **Scope**: single file, diff, PR, full app audit, or design proposal?
- **Type**: controller, model, service, view, job, config, migration, frontend?
- **Context**: what problem is this code solving?

### Step 2: Select Reviewers

1. **Always select all 5 core panel members** (DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria)
2. **Match topic specialists** using the trigger table above. Minimum 3, maximum all 10. Err on the side of inclusion — omitted perspectives are missed signals.

### Step 3: Research Phase (Active Web Search)

For each selected leader, do a **targeted web search** specific to the code under review. Use the patterns in `references/search_patterns.md` for each leader.

**Search formula**: `[Leader Name] [specific pattern/technology from code] [rails/ruby] recommendation`

Example searches:
- Code has a service object: `"David Heinemeier Hansson" service objects Rails alternative`
- Code has N+1 query: `"Nate Berkopec" N+1 query Rails fix`
- Code has Hotwire code: `"Chris Oliver" Stimulus controller best practice`

**Critical**: search for the leader's actual words, blog posts, and talks about the specific pattern. Do not rely on general knowledge alone. Web search results ground the review in their real published opinions.

### Step 4: Review Against Each Leader

For each selected leader, evaluate:
1. **Conformance**: where does the code align with their philosophy?
2. **Divergence**: where does it deviate?
3. **Advice**: what would they recommend instead? Include specific quotes or references from your web search.

Use the reference cards in `references/` for each leader's known principles as a starting framework. But always supplement with fresh web searches for the specific patterns in the code.

### Step 5: Produce Report

Output a markdown report with this structure:

```markdown
# Rails Philosophy Review

## Scope
[What was reviewed - file, diff, PR, scope]

## Core Panel

### DHH
**Conforms**: [specific alignment points]
**Diverges**: [specific deviations]
**Advice**: [what to change, with supporting reference/quote]

### Sandi Metz
[Same structure]

### Avdi Grimm
[Same structure]

### Matz
[Same structure]

### Xavier Noria
[Same structure]

## Specialist Panel

### [Leader Name]
[Same structure, only for topic-matched leaders]

## Synthesis

### Critical Issues
[Issues flagged by 3+ leaders — fix these first]

### Consensus Recommendations
[Changes recommended by multiple leaders]

### Single-Leader Flags
[Domain-specific issues from individual specialists]

### Conformance Score
| Leader | Conformance | Key Issue |
|--------|-------------|-----------|
| DHH    | 7/10        | Simplify X |
| ...    |             |           |
```

## Reference Files

- `references/dhh.md` — DHH philosophy reference card
- `references/sandi_metz.md` — Sandi Metz philosophy reference card
- `references/avdi_grimm.md` — Avdi Grimm philosophy reference card
- `references/matz.md` — Matz philosophy reference card
- `references/xavier_noria.md` — Xavier Noria philosophy reference card
- `references/aaron_patterson.md` — Aaron Patterson philosophy reference card
- `references/jose_valim.md` — José Valim philosophy reference card
- `references/nate_berkopec.md` — Nate Berkopec philosophy reference card
- `references/eileen_uchitelle.md` — Eileen Uchitelle philosophy reference card
- `references/noel_rappin.md` — Noel Rappin philosophy reference card
- `references/justin_searls.md` — Justin Searls philosophy reference card
- `references/pawel_urbanek.md` — Paweł Urbanek philosophy reference card
- `references/akshay_khot.md` — Akshay Khot philosophy reference card
- `references/chris_oliver.md` — Chris Oliver philosophy reference card
- `references/lee_robinson.md` — Lee Robinson philosophy reference card
- `references/search_patterns.md` — Web search patterns for each leader
- `references/leader_matrix.md` — Quick-reference topic-to-leader mapping
