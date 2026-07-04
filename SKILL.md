---
name: railhawk
description: Use when reviewing or writing Rails code -- Railhawk audits against or guides toward philosophies of 15 Ruby/Rails leaders (DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria, Aaron Patterson, Jose Valim, Nate Berkopec, Eileen Uchitelle, Noel Rappin, Justin Searls, Pawel Urbanek, Akshay Khot, Chris Oliver, Lee Robinson). Triggers on "review with Railhawk" (audit mode) or "build/write with Railhawk" (coach mode).
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
| **Eileen Uchitelle** | Framework, upgrades | Migrations, multi-DB, upgrades |
| **Noel Rappin** | Testing, Hotwire | System tests, frontend patterns |
| **Justin Searls** | Test doubles | Mocking, unit test design |
| **Pawel Urbanek** | Architecture | Large-scale, service extraction |
| **Akshay Khot** | Rails patterns | Code structure, schema design |
| **Chris Oliver** | SaaS, Hotwire | Billing, auth, multitenancy |
| **Lee Robinson** | React/Next.js | JS frontend, API mode, SPA |

### Quick File Mapping

`app/controllers/` → DHH, Metz, Noria
`app/models/` → DHH, Avdi, Metz, Uchitelle
`app/services/` → DHH (against), Avdi, Valim, Searls
`app/jobs/` → Oliver, Berkopec, Urbanek
`db/migrate/` → Uchitelle, Noria, Berkopec
`spec/` `test/` → Metz, Searls, Rappin, Avdi
Frontend JS/TS → Robinson, DHH, Oliver, Rappin

---

## Review Mode

**Step 1**: Identify scope + type + context.

**Step 2**: Core 5 always. Match specialists. Err on inclusion.

**Step 3**: Web search per leader: `"[Name]" [specific pattern] rails recommendation`. Ground in real words, not general knowledge.

**Step 4**: Per leader: **Conforms** / **Diverges** / **Advice** (actionable, with quote/URL).

**Step 5**: Produce report:

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

### Protocol

1. **Pre-flight**: Identify file type → load relevant refs → 2-3 web searches → build constraint list (rules attributed to leaders).
2. **Generate**: Write code satisfying constraints. Conflicts resolved by: DHH wins architecture (no service objects, monolith, no-build). Metz/Searls win testing. Else simpler option wins.
3. **Self-check**: DHH delete half? Metz squint? Avdi rescue nil? Matz naming? Noria file conventions?
4. **Tradeoff flag**: If user demands something a leader rejects, flag it:
   `> 🦅 RSpec. DHH hates it ("offends me aesthetically"). Searls/Metz/Rappin fine. Noted.`

### Conflict Defaults

- DHH beats everyone on: service objects (reject), microservices (reject), monolith (keep), build tools (none), auth (hand-roll), RSpec (reject), Devise (reject)
- Metz beats DHH on: class ≤100L, method ≤5L -- DHH concerns work within this
- Searls beats DHH on: unit test design, mocking rules
- Ties: simpler (fewer files, fewer deps, fewer abstractions)

---

## Reference Cards

Load on-demand from `references/` per selected leader:
Core: `dhh.md`, `sandi_metz.md`, `avdi_grimm.md`, `matz.md`, `xavier_noria.md`
Specialists: `aaron_patterson.md`, `jose_valim.md`, `nate_berkopec.md`, `eileen_uchitelle.md`, `noel_rappin.md`, `justin_searls.md`, `pawel_urbanek.md`, `akshay_khot.md`, `chris_oliver.md`, `lee_robinson.md`
