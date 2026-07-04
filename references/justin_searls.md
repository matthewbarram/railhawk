# Justin Searls — Philosophy Reference Card

## Core Testing Philosophy
- **TDD is primarily a design tool**, not a testing tool
- **"Functions should either do or delegate, but never both"**
- **Discovery testing**: write code you wish you had, run (fail), create files (fail differently), implement (now obvious)
- **"Don't mock what you don't own"** — wrap third-party APIs in adapters
- **Level 4 coupling** (isolation tests) demands integration safety net (Level 1 E2E)

## Test Doubles
- **Fake**: simplified working implementation
- **Stub**: returns pre-configured responses
- **Mock**: pre-configures responses + expected interactions
- **Spy**: records interactions for later interrogation
- **Never partial mocks** — mixed real/fake = arbitrary test failures
- **Never mock the subject** — hides root cause (code is too large)
- **50% mock tests fail randomly, tell you nothing**

## Software Design
- **"Clever code is a symptom of poor understanding"**
- **"Obvious is much more impressive than clever"**
- **Small must be meaningfully small** — "Big is bad, but smaller isn't better because it's smaller"
- **"Layering is not abstraction"** — cookie-cutter layers = "large object with extra steps"
- **Verb-before-noun naming**: `FetchesFeed` not `FeedFetcher` (evolves better)
- **Default to returning values** — call verification is last resort
- **Composition over everything** — "My favorite refactoring tool is composition"

## Rails Patterns
- **"Sometimes a controller is just a controller"** — not everything needs refactoring
- **One layer beneath controllers**: `HandlesContactFormSubmission` plain objects
- **Test below the controller, not through it** — don't load webpages
- **"Sticking with omakase pays off"** — trust Rails defaults
- **De-tangle from framework objects** as teams grow

## Key Warnings
- Partial mocks / mocking the subject / half-mocked tests
- Mocking third-party APIs directly (wrap them)
- Mixing logic with delegation
- Cookie-cutter layered architecture
- Clever code (alienates teammates)
- Naive highly-integrated tests
- "Testing after" vs testing first

## Memorable Quotes
- "TDD's primary benefit is to improve the design of our code."
- "Your clever code does not impress me. Your clever code makes me feel stupid."
- "Hard to mock code is hard to use code."
- "Big is bad, but smaller isn't better because it's smaller."
- "Meaningless test data should look meaningless."

## Primary Sources
- testdouble.com/insights
- "Please Don't Mock Me" (JSConf US 2018)
- "Sometimes a Controller Is Just a Controller" (RailsConf 2015)
- "The Failures of Intro to TDD" (2014)
- "The Empowered Programmer" (Rails World 2024)
- Mocktail gem (Ruby) / testdouble.js
