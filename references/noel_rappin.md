# Noel Rappin -- Philosophy Reference Card

## Core Philosophy
- **Trust is the goal of process** -- "Process is what we do to make sure that everybody has a shared sense of state and goals"
- **Explicit strategy beats implicit assumptions** -- write down explicit testing strategies with clear goals
- **Perfect is enemy of pragmatic** -- "If you never have a bug in production you've spent too much time on QA"
- **Match complexity to context** -- team-of-thousands practices are overkill on team of ten
- **Extensibility over rigidity** -- "I'm usually more worried about not being able to extend the method"

## Testing (Test Prescriptions)
- **"Why did you hire this test?"** -- every test must have clear purpose among distinct goals
- **Testing uncanny valley** -- large test suite without confidence in your code
- **Three categories by cost**: Capybara system (slowest) → Workflow/service (medium) → Unit (fastest)
- **System tests 12% of count but 75% of runtime** -- fewer large tests, more small ones
- **TDD is not the same as testing** -- testing, automated testing, and TDD are three different things
- **Buggy code clusters** -- add tests where bugs are found, don't aim for 100% coverage upfront
- **Legacy code: draw a line in the sand** -- start testing from now, every bug fix starts with failing test

## Code Organization
- **"Move complex logic out of controllers into workflow objects, complex creation out of models into factory objects, view logic into presenters -- all plain Ruby objects"**
- **Workflow/Service Objects** for business process logic
- **Factory Objects** for complex creation
- **Presenters** for view logic
- **"If you can't tell exactly what a method does at a glance, it's too long"**

## Frontend (Hotwire/Stimulus)
- **Server-side HTML first, minimal JavaScript**
- **Right tool for job**: Turbo for navigation → Stimulus for small interactions → React for complex reactive data → TypeScript for type safety
- Not "one tool for everything" -- layers within same app

## Key Warnings
- Testing uncanny valley (large suite, no confidence)
- Static typing as premature commitment
- Over-engineering for your context
- Cramming business logic into AR models or controllers
- Large-step TDD (write small tests, small code)
- Dogmatic TDD

## Memorable Quotes
- "If you never have a bug in production you have spent too much time and effort on QA."
- "A lot of people test without a theory of why they're testing."
- "TDD reduces the number of things I need to think about at one time."
- "I'm usually more worried about not being able to extend the method."

## Primary Sources
- noelrappin.com
- "Rails Test Prescriptions"
- "Modern Front-End Development for Rails" (2nd ed)
- "Take My Money"
- "Trust-Driven Development" (leanpub)
