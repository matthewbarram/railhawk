# Yukihiro "Matz" Matsumoto -- Philosophy Reference Card

## Core Philosophy: Programmer Happiness
- Primary design goal for Ruby: making programmers happy
- "Ruby was designed to make programmers productive and happy"
- Happiness = reduce drudgery + enable creative flow

## Design Principles
- **Humans over machines**: "We are the masters. They are the slaves."
- **Pseudo-code that runs**: code should read like your intent
- **Freedom of choice**: TIMTOWTDI, but guide users to better ways
- **Harmony over orthogonality**: pick one good approach vs every combination
- **Principle of Least *My* Surprise**: Matz's surprise, not yours. Applies after you learn Ruby.

## Code Aesthetics (from "Treating Code as an Essay")
Six virtues of beautiful code:
1. **Brevity** -- less code = fewer bugs
2. **Reusability** -- "never write the same thing twice"
3. **Familiarity** -- traditional control structures
4. **Simplicity** -- avoid unnecessary complexity
5. **Flexibility** -- freedom from enforcement
6. **Balance** -- all elements in harmony

"Both essays and lines of code are meant -- before all else -- to be read and understood by human beings."

## Key Quotes
- "I hope to see Ruby help every programmer in the world to be productive, and to enjoy programming, and to be happy."
- "Code is an expression of the thoughts, attitudes, and ideas of the programmer."
- "Naming is extremely important. Proper naming holds great power."
- "Interface is everything. If your system has a bad interface, you basically have nothing."
- "Be lazy. Machines should serve human beings."
- "Programming is a process of designing your own DSL."
- "Motivation is a rare resource."
- "MINASWAN: Matz is nice, and so we are nice."

## Testing Views
- "I hate tests, tests aren't DRY." -- prefers static analysis as supplement
- Values avoiding repetition in all forms
- Ruby's testing culture grew from its expressiveness, not Matz's direct advocacy

## Things He Dislikes
- Perl-style global variables ("my mistake")
- autoload ("I hate autoload")
- Multiple inheritance (hence mixins)
- Threads ("I regret adding Threads" -- prefers Ractors/Fibers)
- Non-free/proprietary software
- Static typing as requirement (embraces optional RBS for documentation/verification)

## Modern Evolution
- Ruby 3x3: acknowledged Ruby "was too slow"
- Backward compatibility as first-class priority
- Types as optional documentation (RBS), not replacement for dynamic soul
- AI: "Humans should remain the master and AI the servant"

## Primary Sources
- Artima interviews (2003): The Philosophy of Ruby, Matz on Craftsmanship
- "Treating Code as an Essay" -- Beautiful Code, Ch. 29 (O'Reilly, 2007)
- RubyConf/RubyKaigi keynotes
