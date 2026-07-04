---
name: railhawk
description: Use when reviewing Ruby on Rails code, architecture decisions, or design proposals -- Railhawk watches your Rails code with the sharp eyes of 15 Ruby/Rails thought leaders (DHH, Sandi Metz, Avdi Grimm, Matz, and more). Triggers on requests for code review, architecture review, Rails best-practices audit, or when asking "what would [leader] think of this code?"
---

# 🦅 Railhawk

Review Rails code against the philosophies of 15 Ruby/Rails thought leaders. Active web searches ground each leader's feedback in their actual published opinions -- blog posts, talks, interviews -- not generic rules.

## Tiered Review Model

### Core Panel (always consulted)

| Leader | Primary Lens |
|--------|-------------|
| **DHH** | Rails conventions, complexity, no-build, monoliths |
| **Sandi Metz** | OOP design, SOLID, class/method sizing, testing |
| **Avdi Grimm** | Confident code, error handling, method design |
| **Matz** | Ruby aesthetics, readability, programmer happiness |
| **Xavier Noria** | Code organization, naming, autoloading, conventions |

### Topic-Matched Specialists

Auto-select based on code under review. Minimum 3, maximum all 10.

| Leader | Lens | Triggered When |
|--------|------|----------------|
| **Aaron Patterson** | Performance, internals, memory | Query optimization, N+1, memory, GC tuning |
| **José Valim** | DDD, functional patterns, explicitness | Service objects, domain design, concurrency |
| **Nate Berkopec** | Rails performance, server tuning | Caching, server config, database performance |
| **Eileen Uchitelle** | Framework internals, upgrades, multi-DB | Migrations, upgrades, multiple databases |
| **Noel Rappin** | Testing, Hotwire/Stimulus | System tests, Hotwire, frontend patterns |
| **Justin Searls** | Test doubles, isolated testing | Mocking, unit testing, test design |
| **Paweł Urbanek** | Architecture, modularization | Large-scale architecture, service extraction |
| **Akshay Khot** | Rails patterns, code organization | Design patterns, code structure |
| **Chris Oliver** | SaaS patterns, Hotwire, Jumpstart | Billing, auth, multitenancy, deployment |
| **Lee Robinson** | React/Next.js, modern JS, performance | React/Next.js frontend, API mode, SPA |

### Quick File-Type Mapping

| File/Directory | Leaders |
|---------------|---------|
| `app/controllers/` | DHH, Sandi Metz, Xavier Noria |
| `app/models/` | DHH, Avdi Grimm, Sandi Metz, Eileen Uchitelle |
| `app/services/` | DHH (against), Avdi Grimm, José Valim, Justin Searls |
| `app/jobs/` | Chris Oliver, Nate Berkopec, Paweł Urbanek |
| `db/migrate/` | Eileen Uchitelle, Xavier Noria, Nate Berkopec |
| `spec/` or `test/` | Sandi Metz, Justin Searls, Noel Rappin, Avdi Grimm |
| Frontend JS/TS | Lee Robinson, DHH, Chris Oliver, Noel Rappin |

## Execution Flow

### Step 1: Understand What's Being Reviewed

Identify scope (file, diff, PR, design proposal), type (controller, model, service, etc.), and context (what problem is this solving?).

### Step 2: Select Reviewers

Always run core 5. Match specialists using the trigger table above. Err on inclusion -- missing perspective > cost of extra review.

### Step 3: Research Phase (Active Web Search)

For each selected leader, do a **targeted web search** specific to the code patterns. Build search strings from leader name + pattern + rails/ruby. Examples:

- Service object: `"David Heinemeier Hansson" service objects Rails alternative`
- N+1 query: `"Nate Berkopec" N+1 query Rails fix`
- Stimulus controller: `"Chris Oliver" Stimulus controller best practice`
- Error handling: `"Avdi Grimm" rescue nil` or `"Avdi Grimm" exceptional ruby fail vs raise`

Search for the leader's actual words. Ground feedback in real blog posts and talks, not general knowledge. Use `references/` cards as starting framework -- supplement with fresh searches.

### Step 4: Review Against Each Leader

For each leader, evaluate:
1. **Conformance** -- where does the code align with their philosophy?
2. **Divergence** -- where does it deviate?
3. **Advice** -- what would they recommend? Include specific quotes/references from web search.

### Step 5: Produce Report

```markdown
# Railhawk Philosophy Review

## Scope
[What was reviewed]

## Core Panel
### DHH
**Conforms**: [specifics]
**Diverges**: [specifics]
**Advice**: [actionable change, with supporting reference/quote]

### Sandi Metz
[Same structure]
...

## Specialist Panel
### [Leader Name]
[Same structure]

## Synthesis
### Critical Issues
[Flagged by 3+ leaders -- fix first]

### Consensus Recommendations
[Changes recommended by multiple leaders]

### Single-Leader Flags
[Domain-specific issues from individual specialists]

### Scorecard
| Leader | Conformance | Key Issue |
|--------|-------------|-----------|
```

## Reference Cards

Load on-demand from `references/` per selected leader:
- `dhh.md`, `sandi_metz.md`, `avdi_grimm.md`, `matz.md`, `xavier_noria.md`
- `aaron_patterson.md`, `jose_valim.md`, `nate_berkopec.md`, `eileen_uchitelle.md`
- `noel_rappin.md`, `justin_searls.md`, `pawel_urbanek.md`, `akshay_khot.md`
- `chris_oliver.md`, `lee_robinson.md`
