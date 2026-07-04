# David Heinemeier Hansson (DHH) — Philosophy Reference Card

## Core Philosophy
- **"The Rails Doctrine"** — 9 pillars: Optimize for programmer happiness, Convention over Configuration, The menu is omakase, No one paradigm, Exalt beautiful code, Value integrated systems, Progress over stability, Push up a big tent, Present company excepted
- **Monoliths over microservices** — "The majestic monolith" — one system, one team, one deploy
- **Complexity is the enemy** — less code, fewer dependencies, fewer services
- **"Conceptual compression"** — reduce cognitive overhead by compressing ideas into simpler abstractions
- **Real-world problems over theoretical purity** — build what solves actual problems today

## Architecture
- **Majestic monolith** — single application, not microservices. Extract only when proven necessary.
- **No service objects** — "Service objects are just objects that have a single method. In Ruby, that's just a function. You can define a function, what you need is a lambda, a Proc, a block."
- **Active Record with concerns** — share code horizontally via concerns, not vertically via inheritance
- **"Skinny controllers, fat models" then "skinny models too"** — use concerns to break up large models
- **Domain events over service objects** — use `ActiveSupport::Notifications` for cross-cutting concerns
- **"On the verge" extraction** — extract only when the alternative is clearly worse

## Frontend (No-Build)
- **"No build" JS** — import maps over Webpack/esbuild, no transpilation, no bundling
- **Hotwire (Turbo + Stimulus)** over React/Vue/Angular
- **HTML over the wire** — send HTML, not JSON. Server-rendered by default.
- **"JavaScript is a liability"** — minimize JS in your app
- **Propshaft** over Sprockets — simpler asset pipeline, no compilation
- **Tailwind CSS** as utility-first approach for styling
- **"The Time When Rails Eats the Frontend"** — Rails should handle the entire stack with Hotwire

## Code Design
- **Convention over Configuration** — follow Rails defaults, don't customize unless truly needed
- **Naming things well** — "There are only two hard things in Computer Science: cache invalidation and naming things"
- **"Don't Repeat Yourself"** (DRY) — but know when DRY is appropriate. Don't DRY prematurely.
- **"You Ain't Gonna Need It"** (YAGNI) — don't build for hypothetical futures
- **Explicit over implicit** (when it matters) — but implicit conventions over boilerplate
- **"Code is like humor. When you have to explain it, it's bad."**

## Testing
- **"Test what's valuable, not what's testable"** — don't test the framework
- **Minitest over RSpec** — simpler, less DSL magic, pure Ruby
- **Fixtures over factories** — faster, simpler, deterministic
- **System tests over unit tests** — test the full stack, what the user actually experiences
- **"TDD is dead"** debate participant — believes strict TDD can lead to over-testing and design damage
- **Don't test private methods or implementation details**
- **"Write tests for confidence, not coverage"**

## Things He Explicitly Rejects
- **Service objects** — "that's just a fancy name for a function"
- **Microservices** — extract only when absolutely necessary
- **GraphQL** — unnecessary complexity over REST
- **TypeScript/static typing** — adds ceremony without proportional benefit for most apps
- **React/Vue SPA** — unnecessary complexity for most web apps, Hotwire solves the same problems
- **Webpack/esbuild complexity** — import maps and no-build are the future
- **Docker for development** — unnecessary complexity
- **Kubernetes for most apps** — overkill
- **TDD purism** — test-first does not guarantee better design
- **"Best practices" without context** — every practice has tradeoffs
- **Enterprise Java patterns in Ruby** — don't import complexity from other ecosystems

## Memorable Quotes
- "Ruby is the language I love. Rails is the framework I built to spread that love."
- "Optimize for programmer happiness."
- "The menu is omakase. Trust the chef."
- "Convention over Configuration."
- "Rails is omakase. A team of chefs picked the ingredients. Trust them."
- "JavaScript is a liability. The less you write, the better."
- "Complexity is the enemy of execution."
- "The majestic monolith."
- "You can't rollback a bad culture decision with `git revert`."
- "There are no solutions. There are only trade-offs."
- "Progress over stability."

## Primary Sources
- dhh.dk (personal blog)
- HEY and Basecamp codebases (public)
- RailsConf keynotes
- "The Rails Doctrine" (rubyonrails.org/doctrine)
- "Getting Real" and "REWORK" (37signals)
- "It Doesn't Have to Be Crazy at Work"
- @dhh on Twitter/X
