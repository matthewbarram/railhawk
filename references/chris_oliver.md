# Chris Oliver (GoRails) -- Philosophy Reference Card

## Core Philosophy
- **Clarity above all** -- "Programming is a form of expression, like writing a novel"
- **Maintenance is 70% of writing software** -- unclear code costs months later
- **Domain-driven Rails** -- organize by product domain, not just default conventions
- **"As few gems as possible"** -- Jumpstart Pro philosophy
- **Write the code you wish you had** -- start with clearest desired interface

## Rails SaaS Patterns
- **Row-level multitenancy** preferred (`acts_as_tenant` co-author) -- avoid `apartment` gem (memory bloat, unmaintained)
- **Pay gem** (he built it) -- unified Stripe/Braintree/Paddle billing
- **Jumpstart Pro** -- SaaS template: Devise, Pundit, Pay, Administrate, Tailwind, Hotwire, multitenancy
- **Focused API clients over heavyweight gems** -- write minimal clients instead of full-featured gems
- **`ActiveRecord#merge`** -- reuse named scopes across associations

## Frontend (Hotwire/Tailwind)
- **Hotwire is default** -- Turbo Streams, Stimulus controllers, Turbo Frames
- **No-Node, no-bundler stack** -- Tailwind gem + Import Maps + Propshaft
- **Turbo Stream conventions** -- `.turbo_stream.erb` + `render turbo_stream:` in controllers
- **`status: :unprocessable_entity`** for form errors with Turbo
- **Tailwind CSS is standard** -- explicit pivot from Bootstrap

## Auth & Authorization
- **Devise for auth** -- Jumpstart Pro default, Rails 8 generator also appreciated
- **Pundit over CanCanCan always** -- "lock everything down by default," clearer

## Testing
- **Minitest for experienced devs, RSpec for beginners**
- **RSpec DSL "obfuscates a lot"** -- Minitest is plain Ruby
- **Recent shift to Minitest + fixtures** in tutorials

## Code Organization
- **Service objects as POROs** -- pass AR queries inside, pass params explicitly
- **Concerns for feature organization** -- not just code sharing
- **Custom generators for team consistency** -- override scaffolds, add project-specific patterns
- **Expressive class methods over before_actions** -- `admin_access_only` instead of scattered `before_action`

## Key Warnings
- Apartment gem (schema multitenancy)
- Heavyweight API client gems (write focused clients)
- **Premature method extraction** -- "make your code uglier, put code back inline"
- One-method-per-class as mechanical SRP rule -- "naive rule" leading to antipatterns
- CanCanCan for authorization
- RSpec for experienced Rubyists

## Infrastructure
- **Hatchbox** (he built it) -- BYO infrastructure, Caddy, automatic SSL, Sidekiq/Solid Queue
- **Active Storage** patterns -- named variants, representations, ActionMailer attachments
- **Sidekiq** is standard; **Solid Queue** welcomed for Rails 8 batteries-included

## Primary Sources
- gorails.com
- jumpstartrails.com
- hatchbox.io
- Rails World 2025: "Beyond the Basics"
- Brighton Ruby 2024: "Mapping Concepts into Code"
- Remote Ruby podcast
