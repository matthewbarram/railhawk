# 🦅 Railhawk

> A Claude Code skill that watches your Rails code through the sharp eyes of 15 Ruby/Rails thought leaders.

Railhawk reviews your Rails code against the philosophies of DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria, Aaron Patterson, José Valim, Nate Berkopec, Eileen Uchitelle, Noel Rappin, Justin Searls, Paweł Urbanek, Akshay Khot, Chris Oliver, and Lee Robinson. It performs live web searches to ground its feedback in each leader's actual published opinions.

## Installation

### Method 1: Clone directly into Claude Code skills

```bash
git clone https://github.com/matthewbarram/railhawk ~/.claude/skills/railhawk
```

### Method 2: Copy manually

```bash
cp -r railhawk ~/.claude/skills/
```

### Verify installation

Ask Claude Code: "What skills do you have available?" -- you should see `railhawk` in the list.

## Usage

Invoke Railhawk in Claude Code:

```
Review app/services/user_registration_service.rb with Railhawk
```

```
Run a Railhawk review on this PR
```

```
What would DHH and Sandi Metz think of this controller design?
```

Railhawk will:
1. Identify the code scope and patterns
2. Select the core 5 leaders + topic-matched specialists (Option C: Tiered)
3. Perform live web searches for each leader's actual advice on your specific patterns
4. Produce a structured report: conforms ✓, diverges ✗, and what to do instead

## How It Works

### Tiered Review Model

**Core Panel** (always runs -- 5 leaders):
- **DHH** -- Rails conventions, complexity, no-build, monoliths
- **Sandi Metz** -- OOP design, SOLID, class/method sizing, testing
- **Avdi Grimm** -- Confident code, error handling, method design
- **Matz** -- Ruby aesthetics, readability, programmer happiness
- **Xavier Noria** -- Code organization, naming, autoloading, conventions

**Specialist Panel** (auto-selected by topic -- up to 10 additional leaders):
- Aaron Patterson -- Performance, Ruby internals, memory
- José Valim -- DDD, functional patterns, explicitness
- Nate Berkopec -- Performance, caching, server tuning
- Eileen Uchitelle -- Framework internals, upgrades, multi-DB
- Noel Rappin -- Testing, Hotwire/Stimulus patterns
- Justin Searls -- Test doubles, isolated testing
- Paweł Urbanek -- Architecture, modularization
- Akshay Khot -- Rails design patterns
- Chris Oliver -- SaaS patterns, Hotwire, Jumpstart
- Lee Robinson -- Next.js/React, modern JS, performance

### Active Web Search

Unlike other code review tools, Railhawk does live web searches for each leader's specific advice on the patterns found in your code. This means reviews cite real blog posts, talks, and articles -- not generic rules.

## License

MIT
