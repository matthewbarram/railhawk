# 🦅 Railhawk

> A Claude Code skill that watches your Rails code -- and your views, JS, CSS, and design -- through the sharp eyes of 14 Ruby/Rails thought leaders.

Railhawk reviews and guides Rails code against the philosophies of DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria, Aaron Patterson, Jose Valim, Nate Berkopec, Noel Rappin, Justin Searls, Chris Oliver, Lee Robinson, Mike Perham, and Katrina Owen. See [SKILL.md](SKILL.md) for full leader panel and topic mapping.

## Installation

```bash
git clone https://github.com/matthewbarram/railhawk ~/.claude/skills/railhawk
```

Verify: ask Claude Code "What skills do you have available?" -- look for `railhawk`.

## Usage

**Review** -- audit existing code:
```
Review app/services/user_registration_service.rb with Railhawk
Run a Railhawk review on this PR
What would DHH and Sandi Metz think of this controller design?
```

**Coach** -- write new code guided by leader philosophies:
```
Write a CommentsController with Railhawk
Build payment processing the Railhawk way
```

Review mode runs per-leader web searches, produces structured conforms/diverges/advice report. Coach mode does pre-flight web searches, generates constraint-satisfying code, self-checks against core 5, flags tradeoffs. Both cite leaders' real blog posts and talks, not generic rules.

## Coverage

| Area | Leaders |
|------|---------|
| Ruby/Rails backend | DHH, Sandi Metz, Avdi Grimm, Matz, Xavier Noria |
| Performance, DB, jobs | Aaron Patterson, Nate Berkopec, Mike Perham |
| Testing | Sandi Metz, Justin Searls, Noel Rappin, Avdi Grimm |
| Frontend JS | Lee Robinson (React/Next.js), DHH (Stimulus), Chris Oliver (Hotwire) |
| CSS/design/UX | Chris Oliver (Tailwind), DHH (vanilla CSS), Lee Robinson (Core Web Vitals) |
| Architecture, domain design | Jose Valim, DHH |
| SaaS, billing, auth | Chris Oliver |
| Refactoring, naming, legacy | Katrina Owen, Sandi Metz, Avdi Grimm |
| Dependencies, gems | Mike Perham, DHH |

## License

MIT
