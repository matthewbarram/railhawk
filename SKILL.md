---
name: railhawk
description: Use when reviewing or writing Rails code against philosophies of 14 Ruby/Rails leaders (DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria, Aaron Patterson, Jose Valim, Nate Berkopec, Noel Rappin, Justin Searls, Chris Oliver, Lee Robinson, Mike Perham, Katrina Owen). Triggers on "review with Railhawk" (audit) or "build/write with Railhawk" (coach).
---

# 🦅 Railhawk

Two modes. Both use live web searches to ground advice in leaders' actual published opinions.

| Mode | Trigger | Does |
|------|---------|------|
| **Review** | "Review X with Railhawk" | Audit existing code |
| **Coach** | "Build/Write X with Railhawk" | Shape code as it's written |

## Leader Panel

### Core (always)

| Leader | Lens |
|--------|------|
| **DHH** | Rails conventions, monolith, no-build, complexity |
| **Sandi Metz** | OOP design, SOLID, class/method sizing, testing |
| **Avdi Grimm** | Confident code, error handling, method design |
| **Matz** | Ruby aesthetics, readability, programmer happiness |
| **Xavier Noria** | Code organization, naming, autoloading, conventions |

### Specialists (topic-matched, min 3)

| Leader | Lens | Trigger |
|--------|------|---------|
| **Aaron Patterson** | Performance, internals | Queries, N+1, memory, GC |
| **Jose Valim** | DDD, explicitness | Service objects, domain design |
| **Nate Berkopec** | Performance, server tuning | Caching, DB performance, Puma |
| **Noel Rappin** | Testing, Hotwire | System tests, frontend patterns |
| **Justin Searls** | Test doubles | Mocking, unit test design |
| **Chris Oliver** | SaaS, Hotwire, Tailwind | Billing, auth, multitenancy, views |
| **Lee Robinson** | React/Next.js, UX, Core Web Vitals | JS frontend, performance, design |
| **Mike Perham** | Background jobs, dependencies | Sidekiq, job design, idempotency, gem audit |
| **Katrina Owen** | Refactoring, naming | Legacy code, naming reviews, characterization tests |

### Quick File Mapping

`app/controllers/` → DHH, Metz, Noria
`app/models/` → DHH, Avdi, Metz
`app/services/` → DHH (against), Avdi, Valim, Searls
`app/jobs/` → Perham, Berkopec, Oliver
`app/views/` `app/components/` → Oliver, DHH, Robinson
`app/assets/` `app/javascript/` → Robinson, DHH, Oliver, Rappin
`db/migrate/` → Noria, Berkopec
`spec/` `test/` → Metz, Searls, Rappin, Avdi
Legacy refactoring → Owen, Metz, Avdi
Dependencies/Gemfile → Perham, DHH
CSS/design → Oliver (Tailwind), DHH (vanilla CSS), Robinson (UX, Core Web Vitals)

---

## Review Mode

1. Identify scope + type + context.
2. Core 5 always. Match specialists. Err on inclusion.
3. Web search per leader: `"[Name]" [specific pattern] rails recommendation`. Ground in real words.
4. Per leader: **Conforms** / **Diverges** / **Advice** (actionable, with quote/URL).
5. Report:

```
# Railhawk Review
## Scope
## Core Panel
### [Leader]: Conforms / Diverges / Advice
## Specialist Panel
### [Leader]: Conforms / Diverges / Advice
## Synthesis: Critical (3+ flags) / Consensus / Single-Leader / Scorecard
```

---

## Coach Mode

1. **Pre-flight**: Identify file type → load relevant refs → 2-3 web searches → constraint list.
2. **Generate**: Constraints from leader rules. Conflicts: DHH wins architecture. Perham wins jobs. Metz/Searls/Owen win testing+naming. Else simpler.
3. **Self-check**: DHH delete half? Metz ≤100L ≤5L? Avdi rescue nil? Matz naming? Noria file conventions? Perham idempotent? Owen story-readable?
4. **Tradeoff flag**: `> 🦅 RSpec. DHH hates it. Searls/Metz/Rappin fine. Noted.`

### Conflict Defaults

- DHH: service objects (reject), microservices (reject), build (none), auth (hand-roll), RSpec (reject), Devise (reject)
- Perham: job design, dependency selection, idempotency
- Metz: class ≤100L, method ≤5L (DHH concerns work within)
- Searls: unit test design, mocking
- Owen: naming after understanding, characterization tests for legacy
- Ties: fewer files, fewer deps, fewer abstractions

---

## Reference Cards

Load on-demand per leader:
Core: `dhh.md`, `sandi_metz.md`, `avdi_grimm.md`, `matz.md`, `xavier_noria.md`
Specialists: `aaron_patterson.md`, `jose_valim.md`, `nate_berkopec.md`, `noel_rappin.md`, `justin_searls.md`, `chris_oliver.md`, `lee_robinson.md`, `mike_perham.md`, `katrina_owen.md`
