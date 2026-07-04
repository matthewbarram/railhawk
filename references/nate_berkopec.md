# Nate Berkopec — Philosophy Reference Card

## Core Performance Philosophy
- **Full-stack and user-first** — optimize at every level, flow from end-user experience
- **Optimization without measurement is premature** — apply scientific, rigorous process
- **Measurement is worthless without context** — relative benchmarks should not replace absolute
- **Simple and fast are complements** — "We cannot optimize what we do not understand"
- **Experimentation over best practice** — "Best-practice-driven development allows lazy decision-making"
- **The Pareto Principle** — 80% of work in 20% of code, do not optimize uniformly
- **It is not Ruby's fault** — "Choosing a web framework based on server costs is clearly a sucker's game"

## ActiveRecord/Database
- **One SQL query per table per controller action** (guideline, not rule)
- **`.count` vs `.size`**: `count` always executes SQL. Most should use `size` (or `load.size`)
- **Never `.where` in AR instance methods** — breaks preloading, causes N+1s when called in collections
- **Predicate differences**: `present?`/`blank?` load all; `any?`/`empty?` use LIMIT 1 if not loaded; `exists?` always executes SQL, never memoized
- **AR audit checklist**: audit predicates, use `exists?` sparingly, avoid where in instance methods, audit count

## Server & Infrastructure (Puma)
```ruby
workers Integer(ENV["WEB_CONCURRENCY"] || 3)
threads 5, 5
preload_app!
```
- **3-8 workers** formula: `TOTAL_RAM / (RAM_PER_PROCESS * 1.2)`, capped at 1.25-1.5x hyperthreads
- **5 threads** — "set it and forget it," >5 has no effect for typical workloads
- **Container sizing**: 70-80% utilization, higher process counts improve routing/latency
- **Scale on queue depth, not response time**
- **jemalloc everywhere**: "If you can switch to jemalloc with Ruby, do it." 4x less memory than glibc.

## Memory & GC
- **glibc malloc is the problem** — per-thread arenas cause 2-4x memory overhead
- **`MALLOC_ARENA_MAX=2`** minimum; **jemalloc** preferred
- **Bloat** (sudden permanent spikes) vs **Fragmentation** (slow logarithmic growth)
- **Daily restarts** as pragmatic defense against fragmentation

## Caching
- **Only cache when failing MAART** (Maximum Acceptable Average Response Time)
- **Key-based expiration** (not manual Sweepers/Observers)
- **Russian doll caching** with `touch: true`
- **Never cache**: pages meeting MAART, POST/PUT, work <10-20ms, remote cache for small work
- **Backend**: Redis (multi-server), MemoryStore (single small), FileStore (low load), never FileStore on Heroku

## Performance Measurement
1. Read production metrics first (New Relic, Skylight, Scout)
2. Profile locally (rack-mini-profiler, Stackprof, rbspy)
3. Create targeted benchmarks (benchmark-ips)
- "Profilers often lie" — cross-validate
- Run with production-like data and `RAILS_ENV=production`

## Key Warnings
- Premature optimization (measure first)
- `.count` when `.size` is appropriate
- `.where` in AR instance methods
- `.exists?` — always executes SQL
- Caching everything blindly
- jemalloc 4.x with Ruby (THP issues)
- FileStore on Heroku
- Scaling on response time rather than queue depth

## Memorable Quotes
- "All performance work without measurement is premature."
- "We cannot optimize what we do not understand. Code that is simple is usually also fast."
- "A Rails controller action should execute one SQL query per table."
- "If you can switch to jemalloc with Ruby, do it."
- "Choosing a web framework based on server costs is clearly a sucker's game."

## Primary Sources
- speedshop.co
- "The Complete Guide to Rails Performance"
- "The Ruby on Rails Performance Apocrypha"
- "Sidekiq in Practice"
- RubyKaigi 2017, 2019 talks
