# Leader Matrix — Topic-to-Leader Quick Reference

## By Code Pattern

| Pattern/Technology | Primary Leaders | Secondary Leaders |
|-------------------|-----------------|-------------------|
| Controllers (actions, params, redirects) | DHH, Sandi Metz | Xavier Noria, Akshay Khot |
| Models (validations, callbacks, scopes) | DHH, Avdi Grimm | Sandi Metz, Eileen Uchitelle |
| Service Objects | DHH (against), Avdi Grimm, José Valim | Justin Searls, Paweł Urbanek |
| Concerns (ActiveSupport::Concern) | DHH, Xavier Noria | Avdi Grimm |
| POROs / Domain Models | Sandi Metz, Avdi Grimm | José Valim, Justin Searls |
| Background Jobs (Sidekiq) | Chris Oliver, Nate Berkopec | Paweł Urbanek |
| Database Queries / N+1 | Nate Berkopec, Aaron Patterson | Eileen Uchitelle |
| Migrations | Eileen Uchitelle, Xavier Noria | Nate Berkopec |
| Multiple Databases | Eileen Uchitelle | — |
| Caching | Nate Berkopec | Chris Oliver |
| Hotwire / Turbo / Stimulus | DHH, Chris Oliver, Noel Rappin | — |
| Import Maps / No-Build JS | DHH, Chris Oliver | Lee Robinson (counterpoint) |
| React / Next.js Frontend | Lee Robinson | DHH (counterpoint), Noel Rappin |
| API-Only Rails | José Valim | Lee Robinson |
| Testing (general) | Sandi Metz, Avdi Grimm | Noel Rappin, Justin Searls |
| Testing (RSpec vs Minitest) | DHH, Chris Oliver | Justin Searls |
| Test Doubles / Mocks | Justin Searls | Sandi Metz, Avdi Grimm |
| System Tests | Noel Rappin | Chris Oliver |
| Auth (Devise, custom) | Chris Oliver | DHH |
| Authorization (Pundit, CanCanCan) | Chris Oliver | Sandi Metz |
| Billing / Payments | Chris Oliver | — |
| Multitenancy | Chris Oliver | Paweł Urbanek |
| Deployment / Infrastructure | Chris Oliver, Nate Berkopec | DHH |
| Performance / Optimization | Nate Berkopec, Aaron Patterson | Paweł Urbanek |
| Error Handling | Avdi Grimm | Sandi Metz, Justin Searls |
| Code Organization / Naming | Xavier Noria, Matz | Sandi Metz, Akshay Khot |
| Refactoring | Sandi Metz, Avdi Grimm | Justin Searls, Paweł Urbanek |
| Upgrades / Deprecations | Eileen Uchitelle, Xavier Noria | — |
| DSLs / Metaprogramming | Matz, Aaron Patterson | Avdi Grimm, José Valim |

## By File Type

| File/Directory | Primary Leaders | Secondary Leaders |
|---------------|-----------------|-------------------|
| `app/controllers/` | DHH, Sandi Metz | Xavier Noria |
| `app/models/` | DHH, Avdi Grimm, Sandi Metz | Eileen Uchitelle |
| `app/services/` | DHH, Avdi Grimm, José Valim | Justin Searls, Paweł Urbanek |
| `app/jobs/` | Chris Oliver, Nate Berkopec | Paweł Urbanek |
| `app/views/` | DHH, Chris Oliver | Noel Rappin |
| `app/helpers/` | DHH, Avdi Grimm | Sandi Metz |
| `app/forms/` | Avdi Grimm, Sandi Metz | José Valim |
| `app/policies/` | Chris Oliver | Sandi Metz |
| `app/components/` | Chris Oliver, Noel Rappin | DHH |
| `config/routes.rb` | DHH, Xavier Noria | — |
| `config/initializers/` | Xavier Noria | Nate Berkopec |
| `config/database.yml` | Nate Berkopec, Eileen Uchitelle | — |
| `db/migrate/` | Eileen Uchitelle, Xavier Noria | Nate Berkopec |
| `db/schema.rb` | Eileen Uchitelle | Nate Berkopec |
| `spec/` or `test/` | Sandi Metz, Justin Searls, Noel Rappin | Avdi Grimm, Chris Oliver |
| `Gemfile` | DHH, Chris Oliver | Justin Searls |
| `Procfile` / `Dockerfile` | Chris Oliver, Nate Berkopec | — |
| Frontend JS/TS files | Lee Robinson, DHH, Chris Oliver | Noel Rappin |

## Core vs Specialist Thresholds

- **Core 5 always run**: DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria
- **Specialists trigger at 3+ pattern matches** in the table above
- **Minimum 3 specialists** even with few matches — err on inclusion
- **When in doubt, include**: cost of missing a perspective > cost of extra review
