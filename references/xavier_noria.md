# Xavier Noria (fxn) — Philosophy Reference Card

## Core Philosophy
- **Pragmatic perfectionism** — "rigor, correctness, pragmatism, and simplicity"
- **Against "magic," for "catalyst"** — automation should be transparent, enhancing not hiding
- **The dateless mindset** — estimation regularly off by 2-3x; date-driven = bad incentives
- **Open source as knowledge-sharing** — "principles I strongly believe construct a better society"
- **Measure twice, cut once** — build only what's absolutely essential

## Code Organization & Naming
- **File naming must match constant naming exactly** — `user.rb` defines `User`
- **Directories ARE namespaces** — subdirectories correspond to nested modules
- **Use fully-nested module syntax** — `module A; module B; end` not `module A::B` (constant lookup differences)
- **Rails does not mandate its default structure** — "projects can add service objects, form objects, decorators"
- **On inflection: "You think less"** — what you see is what you get

## Autoloading & Zeitwerk
- **`Module#autoload` is NOT `const_missing`** — fundamental architectural distinction
- **Be as lazy as possible** — nothing loaded until referenced
- **Absolute paths only** — performance: avoid `$LOAD_PATH` search
- **Thread safety is developer responsibility** — Zeitwerk is thread-safe, client coordination required
- **Eager loading is CoW-friendly** — designed for forking servers

## Upgrade & Deprecation
- **Phased deprecation with long migration windows** — classic→Zeitwerk had 2+ year window
- **Clean removal of legacy code** — deleted ~90% of `active_support/dependencies.rb` when migration done
- **No autoloading during initialization** — use `Rails.application.config.to_prepare` blocks
- **Reassuring but realistic** — "Many non-trivial Rails applications reported really smooth switches"

## Things He Warns Against
- Using `const_missing` for autoloading (lacks nesting context)
- Autoloading during initialization (stale constants on reload)
- Caching reloadable constants in non-reloadable places
- Overlapping autoloader root directories
- Defining (rather than reopening) third-party namespaces in gems
- Date-driven workflows
- Treating Rails defaults as mandates
- Calling things "magic"

## Memorable Quotes
- "Rails comes with a default structure that serves well a ton of apps, but does not mandate that you use that structure as is."
- "Your Ruby code has no trace of Zeitwerk."
- "Simply name files and directories after the classes and modules they define."
- "Point is, you think less. What you see is what you get, simple."
- "Reloading does not reboot the application."
- "Open source is all about knowledge sharing and collaboration."

## Primary Sources
- hashref.com
- Zeitwerk README (github.com/fxn/zeitwerk)
- RailsConf 2022 keynote: "The Journey to Zeitwerk"
- Rails World 2023: "Zeitwerk Internals"
- Ruby Rogues Episode 408
- Balkan Ruby 2024: "A Dateless Mindset"
