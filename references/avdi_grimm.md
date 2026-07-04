# Avdi Grimm -- Philosophy Reference Card

## Core Philosophy: Confident Ruby
- **Each method tells a coherent story** -- four parts in order: collect input → perform work → deliver results → handle failure
- **Confident code** tells a straightforward story; **timid code** second-guesses itself with nil checks, conditionals, scattered error handling
- **"Write total functions"** -- methods always return meaningful values for every possible input
- **Zero tolerance for nil** -- use NullObject, `#fetch`, guard clauses

## Key Confident Ruby Patterns
- **`Hash#fetch` over `[]`** -- raises immediately on missing keys, works with `false`/`nil` values
- **Null Object pattern** -- never return `nil`, return objects that respond to same interface (authored Naught gem)
- **Special Case pattern** -- edge cases as proper objects (e.g., `GuestUser` not `nil`)
- **Guard clauses** -- handle edge cases at top, return early, keep happy path prominent
- **Conversion functions** -- `Array()`, `Float()`, `Integer()` (not `.to_a`, `.to_f`) for stricter coercion
- **Pass behavior, not data** -- blocks/procs over configuration hashes
- **Document assumptions** -- validate at system boundaries, raise immediately

## Error Handling (Exceptional Ruby)
- **Failure = breach of contract** (Bertrand Meyer's Design by Contract)
- **Fail fast**: raise immediately when contract can't be met
- **`fail` vs `raise`**: `fail` for new failures, `raise` only for re-raising (from Jim Weirich)
- **Exceptions shouldn't be expected** -- if predictable (invalid input), don't use exceptions
- **Isolate exception handling** -- inline `begin/rescue/end` blocks are "the pink lawn flamingo of Ruby code"
- **Never `rescue nil`** -- masks unexpected exceptions
- **Preserve original exceptions** -- never throw away the cause when raising new
- **Three essential exception classes** per app/library

## Rails/ActiveRecord Patterns (Objects on Rails)
> "What if we stopped treating ActiveRecord as the backbone of our model classes, and instead, programmed as if ActiveRecord were merely a private implementation detail?"

- **Controller actions should not use AR finders or interact with AR directly**
- **Model all concepts as objects** -- workflows, business rules, constraints
- **Tell, don't ask** -- push behavior into objects
- **Persistence should be pluggable** -- business objects shouldn't know about persistence
- **FigLeaf pattern** -- conceal ActiveRecord behind thin wrapper
- **Exhibit pattern** (not Presenter) -- presentational decorators, authored display_case gem

## Things He Explicitly Rejects
- **Service Objects / Interactors** -- "unnecessary complexity without adding meaning"
- **Rails Concerns** -- "haunt your code like ghosts"
- **Fat Models / God Objects** -- "skinny controller, fat model" just moved bloat
- **The MacGyver Method** -- methods written around existing tools rather than the story
- **The Transactional Fallacy** -- "Every time your service workers crash because a web service takes minutes to respond"
- **Inline begin/rescue/end** -- "pink lawn flamingo of Ruby code"
- **Return values as the OOP model** -- "fundamental denial of the messaging model"

## Memorable Quotes
- "Ruby is a language created in love: love for its linguistic heritage; love for the joy of coding; love for the hackers who write the code."
- "Programming is the practice of applied philosophy."
- "There's no such thing as 'plain old data'."
- "A narrative has a direction, not a goal."
- "The key to working productively in an OO language is to make the type system and polymorphic method dispatch do the work for you."

## Primary Sources
- "Confident Ruby" (2013)
- "Exceptional Ruby" (2011)
- "Objects on Rails" (objectsonrails.com)
- Ruby Tapas screencasts
- avdi.codes
