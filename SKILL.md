---
name: railhawk
description: Use when reviewing or writing Rails code against 14 thought leaders (DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria, and 9 specialists). Triggers on "review with Railhawk" or "build/write with Railhawk".
---

# 🦅 Railhawk

Two modes, one engine. Both use live web searches per leader, not generic rules.

| Mode | Trigger | Does |
|------|---------|------|
| **Review** | "Review X with Railhawk" | Audit existing code |
| **Coach** | "Build/Write X with Railhawk" | Guide code as written |

## Leaders

**Core 5** (always): DHH (conventions, monolith, no-build), Sandi Metz (OOP, class sizing, testing), Avdi Grimm (confident code, errors), Matz (aesthetics, readability), Xavier Noria (organization, naming, autoloading).

**Specialists** (topic-matched, min 3):

| Leader | Lens | Trigger |
|--------|------|---------|
| Aaron Patterson | Perf, internals | Queries, N+1, memory |
| Jose Valim | DDD, explicit | Service objects, domain design |
| Nate Berkopec | Perf, server | Caching, DB, Puma |
| Noel Rappin | Testing, Hotwire | System tests, frontend |
| Justin Searls | Test doubles | Mocking, unit tests |
| Chris Oliver | SaaS, Hotwire, Tailwind | Billing, auth, views |
| Lee Robinson | React/Next.js, UX, CWV | JS, CSS, design |
| Mike Perham | Jobs, deps | Sidekiq, idempotency, gems |
| Katrina Owen | Refactoring, naming | Legacy, naming reviews |

**File mapping**: `controllers`→DHH,Metz,Noria | `models`→DHH,Avdi,Metz | `services`→DHH(against),Avdi,Valim,Searls | `jobs`→Perham,Berko,Oliver | `views/components`→Oliver,DHH,Robinson | `assets/js`→Robinson,DHH,Oliver,Rappin | `migrate`→Noria,Berko | `spec/test`→Metz,Searls,Rappin,Avdi | legacy→Owen,Metz,Avdi | `Gemfile`→Perham,DHH | CSS→Oliver(Tailwind),DHH(vanilla),Robinson(UX,CWV)

---

## Review

For each leader: web search → **Conforms** / **Diverges** / **Advice** (with quote/URL). Report:

```
# Railhawk Review
## Core: [leader] Conforms/Diverges/Advice
## Specialists: [leader] Conforms/Diverges/Advice
## Synthesis: Critical(3+) / Consensus / Single-Leader / Scorecard
```

---

## Coach

1. **Pre-flight**: file type → refs → web search → constraints
2. **Generate**: conflicts: DHH>architecture, Perham>jobs, Metz+Searls+Owen>testing+naming, else simpler
3. **Self-check**: DHH delete half? Metz ≤100L ≤5L? Avdi rescue nil? Noria conventions? Perham idempotent? Owen story-readable?
4. **Flag**: `🦅 RSpec. DHH hates it. Searls/Metz/Rappin fine. Noted.`

### Overrides
DHH: no service objects, no microservices, no-build, hand-roll auth, no RSpec, no Devise
Perham: jobs idempotent, kill dependencies, pass IDs not objects
Metz: ≤100L class, ≤5L method (DHH concerns fit)
Owen: name after understanding, characterization tests for legacy
Tie: fewer files, fewer deps

---

## Reference Cards

Core: `dhh.md` `sandi_metz.md` `avdi_grimm.md` `matz.md` `xavier_noria.md`
Specialists: `aaron_patterson.md` `jose_valim.md` `nate_berkopec.md` `noel_rappin.md` `justin_searls.md` `chris_oliver.md` `lee_robinson.md` `mike_perham.md` `katrina_owen.md`
