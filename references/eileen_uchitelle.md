# Eileen Uchitelle -- Philosophy Reference Card

## Core Philosophy
- **People over architecture** -- "You cannot solve human problems with modularity"
- **Upstream-first development** -- "We tend to look inward for solutions, instead of pushing a patch upstream"
- **Maintenance is foundational work** -- "Organizations promote silver bullets instead of rewarding maintenance"
- **Open source is corporate responsibility** -- "How can Rails be less important than your product if your product relies on Rails?"
- **Overcome self-doubt** -- "The perceived limits we place on ourselves are often untrue"

## Rails Internals & Upgrades
- **Dual-boot during upgrades** -- run app against multiple Rails versions simultaneously
- **Incremental version-by-version** -- never skip major versions
- **Dedicated full-time upgrade team** -- "It will never get done if you have it be a volunteer effort"
- **Deprecation-free operation** -- run clean so future upgrades aren't surprises
- **Tool-assisted issue creation** -- group identical failures, auto-create issues
- **Zero-downtime gradual rollouts** -- deploy across time zones incrementally
- "The cost of not upgrading your application is immeasurable"

## Database & Active Record
- **Multiple databases in Rails 6** (her signature contribution)
- **Horizontal sharding in Rails 7** -- same schema, different data across shards
- **Functional partitioning** -- different schemas per cluster
- **Backward-compatible APIs** -- "change as little of the API as possible"
- **Prevent unnecessary connection teardown** -- reuse connections with identical configs
- **SchemaMigration as independent object** -- decoupled from global AR state

## Testing
- Testing infrastructure should "just work" out of the box (zero-config)
- **System Testing** (Rails 5.1): integrated Capybara, automatic screenshots on failure
- **Parallel Testing** (Rails 6): forked processes or threads, per-worker databases
- **Ship at ~95%** -- let community identify remaining issues
- Flaky tests are **operational cultural problems**, not purely technical

## Culture & Teams
- **Defensive code ownership is unhealthy** -- "Rather than working together, misaligned incentives breed blame"
- **Open source as funnel**: users → contributors → maintainers
- **Constructive feedback only** -- never "this code sucks" or close PRs without explanation
- **"Find something no one else wants to work on"** -- unglamorous work = outsized impact

## Key Warnings
- Don't mutate Minitest classes
- Don't skip Rails upgrades
- Don't rely on volunteer effort for upgrades
- Don't solve human problems with modularity
- Don't over-fragment into tiny packages (packwerk pitfalls)
- Don't ship without quality gatekeeping
- Don't treat open source as a side project
- Don't fall for sunk-cost fallacy on architecture

## Memorable Quotes
- "The myth of the modular monolith is that architecture cannot fix human and cultural problems."
- "You cannot solve human problems with modularity."
- "The cost of not upgrading your application is immeasurable."
- "When you don't upgrade Rails, you lose great talent."
- "If you can't convince leadership that open source is important, consider leaving."

## Primary Sources
- "The Myth of the Modular Monolith" (Rails World 2024)
- "The Magic of Rails" (RailsConf/Rails World 2023)
- "The Success of Ruby on Rails" (RailsConf 2022)
- "All the Things I Thought I Couldn't Do" (RailsConf 2021)
- "The Future of Rails 6: Scalable by Default" (RailsConf 2018)
- eileencodes.com
