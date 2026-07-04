# Paweł Urbanek -- Philosophy Reference Card

## Core Philosophy
- **Pragmatic, measured optimization** -- high-leverage, low-effort changes with measurable results
- **Evidence over intuition** -- "EXPLAIN ANALYZE allows you confidently make changes based on solid evidence"
- **Caching is a last resort** -- "The best way to implement caching is to avoid it"
- **Own your platform** -- self-hosted content, own your learning
- **No 'just' in software** -- "Lexically there's never a need to include the word 'just'"
- **Infrastructure ownership matters** -- migrate from managed to controllable as projects mature

## 5-Layer Optimization Recipe (in order)
1. **Frontend/HTTP first** -- caching headers, HTTP/2, CDN, compression (best ROI)
2. **Eliminate N+1 queries** -- "top performance killer for Rails applications"
3. **Optimize individual SQL queries** -- using rails-pg-extras
4. **Database configuration** -- `random_page_cost`, `work_mem`, cache hit ratios
5. **Server configuration** -- Puma threading, instance sizing, jemalloc

## Architecture & Code
- **Service objects as transition pattern** -- not final architecture, enum-style result codes
- **View presenters via SimpleDelegator** -- not Draper (memory concerns)
- **Design APIs around primitive values** -- pass IDs not AR instances
- **Rails helpers are anti-pattern** -- global scope, hard to test, naming collisions
- **Adding gems is risk** -- evaluate on memory, maintenance, thread-safety
- **DB constraints complement app validations** -- NOT NULL, foreign keys, partial indexes

## Performance Patterns
- **Brotli over Gzip** -- 13-25% better compression for cache operations
- **`random_page_cost` 1.1 on SSD** -- from default 4
- **`select(:id, :col)` not SELECT *** -- 65% memory reduction on 12-column models
- **Subquery caching** -- extract IDs as primitives, then pass to subsequent queries
- **Jemalloc** -- 15-20% memory reduction, often enables extra Puma worker
- **`load_async`** is powerful but dangerous -- almost doubles DB connections
- **ActiveRecord is double-edged sword** -- "best feature and greatest sin at the same time"

## Key Warnings
- Overusing AR transactions (row-level locks)
- `--sandbox` on production console
- Ruby threads for concurrency (prefer Typhoeus Hydra)
- Raw `Thread.current` (use `ActiveSupport::CurrentAttributes`)
- Smart cache expiry tied to callbacks
- Caching AR::Relation objects (always `.to_a` first)
- Mirrored compound indexes on join tables (one compound + one single-column)
- Nullable boolean fields ("ticking time bomb")
- Third-party script tags without auditing
- `has_and_belongs_to_many`
- Heroku PostgreSQL for mature apps (no superuser access)
- Monitoring Sidekiq from inside the app

## Memorable Quotes
- "There's no 'just' in software development."
- "The best way to implement caching is to avoid it."
- "Learning to spot reusable parts of Active Record queries is an insanely useful technique."
- "Spinning up threads to make code 'run faster because concurrency' is a recipe for disaster."
- "If you want to write fast web apps, use slow internet."
- "Adding a cache layer always increases the complexity and is a potential source of sneaky bugs."

## Primary Sources
- pawelurbanek.com
- rails-pg-extras gem (github.com/pawurb/rails-pg-extras)
- dbg-rb gem
