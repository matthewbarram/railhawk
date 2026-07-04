# David Heinemeier Hansson (DHH) -- Philosophy Reference Card

## Core Philosophy
- **Three Latin principles** (RailsWorld 2025): Libertas (Freedom), Proprietarius (Ownership), Pietas (Duty)
- **Conceptual compression** -- shrink conceptual surface area until it "fits in a normal programmer's brain"
- **Optimize for programmer happiness** -- "I created Rails for me. To make me smile, first and foremost."
- **"Software writer, not software engineer"** -- code is written for humans, incidentally executed by computers
- **"Fight the merchants of complexity"** -- many profit from layering unnecessary complexity onto software
- **"No code runs faster than no code"** -- the best code is the code never written
- **Rule of three for abstraction** -- "Duplicate twice before abstracting." Extract only when pain is proven.

## Architecture
- **The Majestic Monolith** -- one system, one team, one deploy. Method calls, not HTTP calls.
- **The Citadel pattern** -- extract only when subsystem has radically different ops profile (e.g., polling server). Extract as small "Outpost" app, keep monolith as Citadel.
- **No service objects** -- "that's just a fancy name for a function… a dense jungle of service objects, command patterns, and worse." Business logic on model: `@recording.archive`, not `RecordingArchiver.new(@recording).call`.
- **Concerns** -- preferred horizontal sharing mechanism. Named as adjectives: `Closeable`, `Publishable`, `Mentionable`. Each 50-150 lines, cohesive. NOT created just to reduce file size.
- **"Rails is not your application" is rejected** -- "Fuck. That. Shit." Rails IS your application.

## Controllers
- **Strictly 7 REST actions** -- index, show, new, create, edit, update, destroy
- **Custom action = missing resource** -- `Cards::ClosuresController` not `close` on `CardsController`
- **"Every single time I've regretted controllers, it's been too few, not too many"**
- **Actions 1-5 lines** -- "Empty actions are fine." Relies on Rails implicit rendering.
- **Controllers handle HTTP only** -- params, auth, redirects, rendering. No business logic.

## Models
- **"What can a Recording do?"** should be answerable by reading the model
- **State as records, not booleans** -- `Card.joins(:closure)` not `closed: true`
- **Bang methods** -- `create!`, `save!`, `update!` for fail-fast
- **Database constraints over AR validations** -- DB is last line of defense
- **Write-time over read-time** -- counter caches, write-time roll-ups
- **`CurrentAttributes` for request context** -- don't thread `current_user` through every method
- **`normalizes` for data cleaning** -- over `before_validation`
- **Callbacks for "auxiliary complexity"** -- emails, notifications, mentions. With `suppress` escape hatch.

## Frontend (No-Build, Hotwire)
- **"You can't get faster than No Build"** -- import maps, no transpilation, no bundling. HEY runs ~100 individual JS files over HTTP/2, scores 100/100 on Lighthouse.
- **"JavaScript is a liability"** -- minimize JS. Hotwire (Turbo + Stimulus) over React/Vue/Angular.
- **Progressive enhancement ladder**: Turbo Drive → Turbo Frames → Turbo Streams → Stimulus sprinkles
- **Propshaft** over Sprockets -- minimal asset pipeline, digest stamping only
- **TypeScript removed from Turbo** (2023) -- "pollutes the code with type gymnastics… things that should be easy become hard, things that are hard become `any`. No thanks!"
- **Vanilla CSS** with nesting/variables -- not Tailwind

## Testing
- **Testing pyramid**: Model tests (bottom, most) → Integration tests (middle, workhorse) → ~10 smoke tests (top, critical paths only)
- **"System tests have failed"** -- deleted 359 system tests from HEY, kept ~10. "Always brittle, always broken, always slow."
- **"TDD is dead. Long live testing."** (2014) -- "Test-first fundamentalism is like abstinence-only sex ed."
- **Design-first, backfill tests** -- "Stop obsessing about unit tests, embrace backfilling when you're happy with the design."
- **Minitest + fixtures** -- "RSpec offends me aesthetically." Real database, never mock it.
- **Confidence-driven, not coverage-driven** -- "100% coverage is silly."
- **Rarely unit tests with mocks** -- prefers integration tests exercising real objects together.

## The Modern Omakase Stack (Rails 8)
| Area | Default | Replaces |
|------|---------|----------|
| Database | SQLite | PostgreSQL/MySQL + Redis |
| Queue | Solid Queue (DB-backed) | Sidekiq + Redis |
| Cache | Solid Cache (DB-backed) | Redis |
| WebSockets | Solid Cable (DB-backed) | Redis |
| Frontend | Hotwire (Turbo + Stimulus) | React/Vue/Svelte |
| Assets | Propshaft + Import Maps | Webpack/esbuild |
| JS | Vanilla ES6, no build | TypeScript + bundler |
| CSS | Vanilla CSS | Tailwind, Sass |
| Testing | Minitest + fixtures | RSpec + FactoryBot |
| Auth | Hand-rolled (~150 lines) | Devise |
| Deployment | Kamal (containers on VPS/bare metal) | Heroku, Kubernetes |
| Architecture | Majestic Monolith | Microservices |

## Cloud Exit
- 37signals left cloud Oct 2022. Spent $3.2M on cloud in 2022. Projected $10M+ savings over 5 years.
- "Renting computers is (mostly) a bad deal for medium-sized companies with stable growth."
- **Kamal** built for deploying containers to bare metal/VPS.
- "Any mid-sized SaaS business with stable workloads that does not benchmark their rental bill is committing financial malpractice."

## Explicit Rejections
- Service objects ("dense jungle"), microservices ("zombie architecture"), TypeScript, RSpec, FactoryBot
- Devise (~5,000 lines vs ~150 hand-rolled), Pundit/CanCanCan, Sidekiq/Redis (Solid ecosystem replaces)
- GraphQL (unnecessary), React/Vue SPA, Webpack/esbuild ("massive tumor of complexity")
- System tests at scale (brittle/slow), TDD dogma ("abstinence-only sex ed"), 100% coverage
- Containerization for development, Kubernetes for most, serverless for stable workloads
- "Rails is not your application" separation ("complete wank")
- Enterprise Java patterns in Ruby

## Memorable Quotes
- "Ruby is the language I love. Rails is the framework I built to spread that love."
- "Complexity is the enemy of execution."
- "The menu is omakase. Trust the chef."
- "You can't get faster than No Build."
- "No code runs faster than no code. No code has fewer bugs than no code."
- "The difference between a method call and an HTTP call is huge. The first rule of distributed computing is don't distribute your computing."
- "Vanilla Rails is plenty."
- "Clarity is the number one goal, not test coverage or test speed."
- "There are no solutions. There are only trade-offs."

## Primary Sources
- world.hey.com/dhh, dev.37signals.com
- "The Rails Doctrine" (rubyonrails.org/doctrine)
- HEY/Basecamp/Campfire codebases (public)
- Unofficial 37signals Coding Style Guide (compiled from 265+ PR reviews)
- RailsConf keynotes, RailsWorld keynotes
- "Getting Real", "REWORK", "It Doesn't Have to Be Crazy at Work" (37signals)
