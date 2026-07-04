---
name: railhawk
description: Use when reviewing Ruby on Rails code, architecture decisions, or design proposals -- or when writing Rails code with philosophical guidance. Railhawk watches your Rails code with the sharp eyes of 15 Ruby/Rails thought leaders (DHH, Sandi Metz, Avdi Grimm, Matz, and more). Two modes: Review (audit existing code) and Coach (guide code generation in real time).
---

# 🦅 Railhawk

Two modes, one philosophy engine:

| Mode | Trigger | Purpose |
|------|---------|---------|
| **Review** | "Review X with Railhawk" | Audit existing code against leader philosophies |
| **Coach** | "Build X with Railhawk" / "Write X the Railhawk way" | Guide code generation to match leader philosophies |

Both modes use live web searches to ground everything in leaders' actual published opinions -- blog posts, talks, interviews -- not generic rules.

## The 15 Leaders

### Core Panel (always consulted)

| Leader | Primary Lens |
|--------|-------------|
| **DHH** | Rails conventions, complexity, no-build, monoliths |
| **Sandi Metz** | OOP design, SOLID, class/method sizing, testing |
| **Avdi Grimm** | Confident code, error handling, method design |
| **Matz** | Ruby aesthetics, readability, programmer happiness |
| **Xavier Noria** | Code organization, naming, autoloading, conventions |

### Topic-Matched Specialists

Auto-select based on code patterns. Minimum 3, maximum all 10.

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

---

## Mode 1: Review (Audit Existing Code)

### Step 1: Understand Scope
Identify scope (file, diff, PR, design proposal), type (controller, model, service, etc.), and context (what problem is this solving?).

### Step 2: Select Reviewers
Always run core 5. Match specialists using trigger table above. Err on inclusion.

### Step 3: Research (Active Web Search)
For each selected leader, do targeted web search for specific code patterns. Examples:

- Service object: `"David Heinemeier Hansson" service objects Rails alternative`
- N+1 query: `"Nate Berkopec" N+1 query Rails fix`
- Stimulus controller: `"Chris Oliver" Stimulus controller best practice`
- Error handling: `"Avdi Grimm" rescue nil exceptional ruby`

Search for leaders' actual words. Ground feedback in real blog posts and talks.

### Step 4: Evaluate Per Leader
For each leader: **Conforms** (alignment), **Diverges** (deviation), **Advice** (actionable change with reference/quote).

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

---

## Mode 2: Coach (Guide Code Generation)

Coach mode runs Railhawk's philosophy engine **during** code generation, not after. It shapes the code as it's written.

### When Coach Mode Activates
Triggers include: "Build X with Railhawk", "Write X the Railhawk way", "Implement X following DHH/Sandi Metz/etc", "Generate this controller the Railhawk way".

### Coach Protocol

#### Phase 1: Pre-Flight (before writing code)
1. Identify what's being built (controller, model, service, migration, test, etc.)
2. Identify relevant leaders from the file-type mapping + trigger table
3. Load their reference cards from `references/`
4. Do 2-3 quick web searches for specific patterns the code will use
5. Synthesize a **constraint list** -- specific rules the code must follow, attributed to specific leaders

#### Phase 2: Generate (write the code)
Write code that satisfies the constraint list. For each design decision, apply the highest-priority leader's rule. When leaders conflict:

| Conflict | Resolution |
|----------|-----------|
| DHH vs Sandi Metz on class size | Sandi Metz: ≤100 lines, ≤5 line methods. DHH's concern pattern works within this. |
| DHH vs Avdi Grimm on service objects | DHH wins: no service objects. Put logic on model with concerns. |
| DHH vs Justin Searls on mocking | Context-dependent: Searls for unit test design, DHH for integration preference. |
| DHH vs Chris Oliver on Devise | DHH wins: hand-rolled auth unless user specifically requests Devise. |
| Sandi Metz vs Justin Searls on testing | Metz for what to test, Searls for how to mock. Complementary, not conflicting. |

Default tiebreaker: **simpler option wins** (ponytail principle -- fewer files, fewer dependencies, fewer abstractions).

#### Phase 3: Self-Check (after writing code)
After generating, run a quick internal checklist:
1. Would DHH delete half of this? (If yes, what?)
2. Does each method pass the Sandi Metz squint test?
3. Are there any `rescue nil` or timid code patterns Avdi Grimm would flag?
4. Is naming Matz-readable? (File names match constants, methods tell intent.)
5. Does file structure match Xavier Noria's conventions?

#### Phase 4: Flag Tradeoffs
If any generated code deliberately violates a leader's advice (e.g., user demands RSpec but DHH hates it), flag it explicitly:

```markdown
> 🦅 **Railhawk note**: This uses RSpec. DHH would use Minitest here ("RSpec offends me aesthetically").
> Justin Searls and Sandi Metz are fine with it. Tradeoff noted.
```

### Coach Mode Example

User: "Write a CommentsController the Railhawk way"

Pre-flight:
- File: `app/controllers/comments_controller.rb` → Leaders: DHH, Sandi Metz, Xavier Noria
- Quick search: DHH REST controller conventions + DHH concern patterns
- Constraint list: 7 REST actions only, 1-5 lines each, empty actions fine, no service objects, use concerns on model for shared behavior

Generate:
```ruby
class CommentsController < ApplicationController
  before_action :set_commentable
  before_action :set_comment, only: %i[ show edit update destroy ]

  def index
  end

  def show
  end

  def new
    @comment = @commentable.comments.new
  end

  def edit
  end

  def create
    @comment = @commentable.comments.create!(comment_params)
    redirect_to @comment, notice: "Comment created."
  end

  def update
    @comment.update!(comment_params)
    redirect_to @comment, notice: "Comment updated."
  end

  def destroy
    @comment.destroy!
    redirect_to @commentable, notice: "Comment deleted."
  end

  private
    def set_commentable
      @commentable = params[:commentable_type].constantize.find(params[:commentable_id])
    end

    def set_comment
      @comment = @commentable.comments.find(params[:id])
    end

    def comment_params
      params.require(:comment).permit(:body)
    end
end
```

Self-check:
> 🦅 **Railhawk self-check**: DHH approves (REST, 1-line actions, `create!`/`update!`/`destroy!`, no service objects). Sandi Metz: controller instantiates 2 objects (`@commentable`, `@comment`) -- consider extracting one to a before_action-only lookup that doesn't set an instance variable. Xavier Noria: file naming matches constant (`CommentsController` → `comments_controller.rb`). Matz: readable, intention-revealing method names.

---

## Reference Cards

Load on-demand from `references/` per selected leader:
- `dhh.md`, `sandi_metz.md`, `avdi_grimm.md`, `matz.md`, `xavier_noria.md`
- `aaron_patterson.md`, `jose_valim.md`, `nate_berkopec.md`, `eileen_uchitelle.md`
- `noel_rappin.md`, `justin_searls.md`, `pawel_urbanek.md`, `akshay_khot.md`
- `chris_oliver.md`, `lee_robinson.md`
