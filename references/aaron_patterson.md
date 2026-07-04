# Aaron Patterson (tenderlove) — Philosophy Reference Card

## Core Philosophy
- **Build to understand** — learns by building (TenderJIT, Fisk, compacting GC)
- **Do things in public** — gives others a base to build on
- **Incremental progress** — "not that much, but cumulatively"
- **Playfulness is not unserious** — playful names (Adequate Record, TenderJIT), rigorous substance
- **Steal good ideas shamelessly** — credits JRuby/JVM communities for optimization ideas

## Performance Principles
- **Reduce object allocations first** — cut ~1,000 allocations/request in Rails 4.2
- **Separate static from dynamic data** — cache computed invariants (Adequate Record pattern)
- **Use `GC.stat` as lightweight profiler** — count allocations, don't reach for heavy tools
- **Verify with two methods** — confirm memory savings with time tests
- **Algorithm choice matters** — red-black trees over naive binary trees for IV cache (6.65x improvement)
- **JIT is necessary** — believes JIT essential for Ruby's future

## Ruby Internals
- Built Ruby's first compacting GC (2.7, three-year project)
- Machine code = "like ERB for machine code"
- Metaprogramming is pragmatic — for debugging, not production hot paths
- Be precise about references — removing unnecessary mark entries saved ~3% memory

## Rails Patterns
- **Do not fork Rails** — "You are not special"
- **Don't monkey-patch undocumented internals** — "you're only hurting yourself"
- **Contribute upstream** — understand system deeply, fix at source
- **Use cheapest operation** — `bsearch` 30x faster than `include?` on sorted arrays
- **Know concurrency model** — CRuby threads for IO-bound, Ractors for CPU parallelism

## Testing Approach
- Integration tests should replace controller tests entirely (make them fast enough)
- Parallel testing should be automatic and zero-config
- Run only tests relevant to changes
- Randomized test ordering is prerequisite for parallel execution

## Things He Rejects
- Forking Rails
- Monkey-patching undocumented internals
- Weak references used carelessly (slow memory leaks)
- TruffleRuby omitting memory from benchmarks
- Caching without expiry

## Memorable Quotes
- "I am a puts debuggerer."
- "Don't fork Rails. You are not special."
- "When you're debugging, anything goes."
- "I'm a Ruby programmer. I like programming Ruby... Can we do this in Ruby?"

## Primary Sources
- tenderlovemaking.com
- RailsConf keynotes (2014, 2015, 2023, 2024)
- "Some Assembly Required" (RubyConf 2021)
- "Compacting GC for MRI" (Balkan Ruby 2019)
- "Speeding up IVs" (Tropical.rb 2024)
