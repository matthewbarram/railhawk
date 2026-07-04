# Mike Perham -- Philosophy Reference Card

## Core Philosophy
- **"Kill your dependencies"** -- every dependency is a long-term liability. Sidekiq stripped Celluloid, redis-namespace, Sinatra.
- **"Less is more"** -- minimal APIs, convention over configuration, no knobs you don't need
- **Solo, bootstrapped, sustainable** -- built Sidekiq to $7M ARR alone. VC funding is "a ticking time bomb."
- **"Choose boring, proven technology"** -- what you know will be maintained in 10 years
- **"Developers want to write code"** -- not drag blocks in a workflow GUI

## Background Jobs
- **3 rules** (RubyConf 2012): 1) Small stateless messages 2) Idempotent and transactional 3) Embrace concurrency
- **Idempotency is mandatory** -- Sidekiq guarantees at-least-once, not exactly-once. "All jobs must handle duplication."
- **Pass IDs, not objects** -- queue identifiers, not serialized AR instances (they change between enqueue and execute)
- **Don't enqueue inside transactions** -- job may run before transaction commits
- **Retries are critical** -- "networks fail and bugs happen, job retries are critical to a self-healing production environment"
- **"Background jobs are the best architectural pattern for scaling typical business apps"**

## Architecture & Dependencies
- **Avoid VC-backed dependencies** -- "they either get big or go out of business"
- **Avoid unmaintained OSS** -- maintainers burn out, abandonware becomes liability
- **Self-contained over fragmented** -- Faktory as single binary, no external runtime deps
- **Convention over configuration** -- opinionated defaults, you don't configure every knob
- **Resist feature bloat** -- "just because you can add a feature doesn't mean you should"
- **Memory is the scaling constraint** in Ruby -- multi-process = multi-RAM. 8 threads in 1GB vs 8 process in 4GB.

## Production
- **Idempotent jobs**: check and guard before performing if not naturally idempotent
- **"The contract is: all jobs must be able to handle duplication"**
- **Small messages**: JSON-safe types only in job args (integers, strings, arrays, hashes)
- **Separate fast and slow queues** -- don't let slow jobs block fast ones
- **Monitor queue depth, not just execution time**
- **"If you need workflow orchestration, you need Sidekiq Pro batches or Faktory"**

## Things He Rejects
- Heavyweight gems that pull in 20 transitive dependencies
- Workflow GUIs for developers ("those are marketing tools")
- VC-funded infrastructure dependencies
- Complex configuration ("who cares... let the framework deal with it")
- Building features because you can

## Memorable Quotes
- "Kill your dependencies."
- "Less is more."
- "Choose boring, proven technology."
- "All jobs must be able to handle duplication."
- "Background jobs are the best architectural pattern for scaling."
- "I don't want to hire anybody. I'm going to be solo."
- "Developers don't like moving blocks of code around in a GUI. They want to write code."

## Primary Sources
- mikeperham.com
- Sidekiq wiki: github.com/mperham/sidekiq/wiki/Best-Practices
- RubyConf 2012: "Asynchronous Processing for Fun and Profity"
- Maintainable podcast, alphalist.CTO podcast, SaaS.group podcast
