<h1 align="center">iOS Clean Code Skills</h1>

<p align="center">
    <img src="https://img.shields.io/badge/Swift-5.9+-F05138.svg" alt="Swift 5.9+" />
    <img src="https://img.shields.io/badge/iOS-13+-2980b9.svg" alt="iOS 13+" />
    <a href="https://agentskills.io/home">
        <img src="https://img.shields.io/badge/Agent%20Skills-Compatible-purple.svg" alt="Agent Skills Compatible" />
    </a>
</p>

A bundle of agent skills that help AI coding agents (Claude Code, Codex, Cursor, Gemini, ...) review and write Swift / iOS code that follows **Clean Code** (Robert Martin) and the **Cognitive Complexity** model (G. Ann Campbell, SonarSource).

Originally created by [Lev Bondarenko](https://github.com/levabond/iOS-clean-code-skills). This fork repackages the skills into the [Agent Skills](https://agentskills.io/home) format so they install cleanly with a single `npx` command across all major coding agents.


## Skills in this Bundle

| Skill | Chapter / Topic | What it does |
|---|---|---|
| `swift-clean-names` | Ch. 2 - Meaningful Names | Review and fix naming: variables, functions, types, protocols |
| `swift-clean-functions` | Ch. 3 - Functions | Audit function size, single responsibility, argument count, DRY |
| `swift-clean-types` | Ch. 6, 10 - Classes & Objects | Review class/struct/enum/protocol design, SRP, cohesion, DI |
| `swift-clean-errors` | Ch. 7 - Error Handling | Audit `throws` / optionals / `Result`, custom `Error` types |
| `swift-clean-tests` | Ch. 9 - Unit Tests | Check FIRST principles, AAA pattern, test naming, mocking |
| `swift-clean-review` | All chapters | Full Clean Code audit of a file or directory |
| `swift-cognitive-complexity` | Cognitive Complexity | Score and reduce nesting, closures, control-flow complexity |
| `swift-clean-advisor` | Model-invoked | Activates automatically when writing or editing Swift |


## Installing

Install any skill into Claude Code, Codex, Gemini, Cursor, and more using `npx`:

```bash
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-clean-names
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-clean-functions
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-clean-types
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-clean-errors
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-clean-tests
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-clean-review
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-cognitive-complexity
npx skills add https://github.com/n0an/iOS-clean-code-skills --skill swift-clean-advisor
```

If you get `npx: command not found`, install Node first:

```bash
brew install node
```

(If `brew` is missing too, [install Homebrew](https://brew.sh) first.)

When using `npx`, you can choose which agents to register the skill with, and whether to install it for one project or globally for all your projects.

### Alternative install methods

**Claude Code** (installs the whole bundle):

```bash
/plugin install n0an/iOS-clean-code-skills
```

**Gemini** (installs the whole bundle):

```bash
gemini extensions install https://github.com/n0an/iOS-clean-code-skills.git --consent
```

You can also clone the whole repository and copy the skill folders wherever your agent expects them.


## Using the Skills

### As slash commands

In Claude Code:

```
/swift-clean-names Sources/Auth/LoginViewModel.swift
/swift-clean-functions Sources/Services/NetworkService.swift
/swift-clean-types Sources/Features/Checkout/CheckoutViewModel.swift
/swift-clean-errors Sources/Networking/APIError.swift
/swift-clean-tests Tests/UserServiceTests.swift
/swift-clean-review Sources/Features/Checkout/
/swift-cognitive-complexity Sources/Features/Checkout/CheckoutViewModel.swift
```

In Codex:

```
$swift-clean-names Sources/Auth/LoginViewModel.swift
$swift-clean-functions Sources/Services/NetworkService.swift
...
```

### Natural language

You can also trigger any of these via plain prompts, for example:

> Use the swift-clean-review skill on `Sources/Features/Checkout/`.

> Score the cognitive complexity of `CheckoutViewModel.swift` and suggest reductions.

### Automatic (model-invoked)

`swift-clean-advisor` activates on its own when you write or edit `.swift` files, applying Clean Code guidance without being asked.


## Why a Clean Code Skill for Swift?

LLM training data on Swift skews toward generic OOP examples and older Foundation patterns. As a result, agents routinely produce code that:

- Uses noise names (`UserManager`, `data`, `info`, `helper`) and abbreviated identifiers
- Writes 80-line functions with 5+ arguments and mixed responsibilities
- Reaches for `class` and inheritance when a `struct` + protocol would compose cleaner
- Swallows errors with `try?` or returns `nil` instead of `throws` / `Result`
- Writes tests that share state, hit the network, or assert via side effects
- Nests `if let` / `guard` / `switch` until cognitive complexity explodes

These skills:

- **Catch the anti-patterns** Swift agents default to
- **Provide concrete refactors** mapped to specific Clean Code chapters
- **Stay Swift-idiomatic** - prefer value types, protocol-oriented DI, `guard` for early exits, `async/await`, Swift Testing
- **Cover both reviewing and writing** - use as a linter on existing code or a guide when generating new code


## Clean Code Principles Covered

Based on Robert Martin's *Clean Code* (2008):

1. **Ch. 2 - Meaningful Names**: intention-revealing names, no abbreviations, no noise words, consistent vocabulary
2. **Ch. 3 - Functions**: small, single responsibility, low argument count, no side effects, DRY
3. **Ch. 4 - Comments**: no noise comments, no commented-out code, explain WHY not WHAT
4. **Ch. 5 - Formatting**: vertical/horizontal organization, proximity rule
5. **Ch. 6 - Objects & Data Structures**: encapsulation, data/object anti-symmetry
6. **Ch. 7 - Error Handling**: `throws` over `nil`, meaningful `Error` types, no silent catches
7. **Ch. 9 - Unit Tests**: FIRST principles (Fast, Independent, Repeatable, Self-Validating, Timely)
8. **Ch. 10 - Classes**: SRP, high cohesion, open/closed principle
9. **Ch. 11 - Systems**: dependency injection, separate construction from use

Plus G. Ann Campbell's [Cognitive Complexity - A new way of measuring understandability](https://www.sonarsource.com/resources/cognitive-complexity/) for measuring and reducing how hard a function is to understand.

### Swift-specific additions

- Prefer `struct` (value types) over `class`
- Protocol-oriented programming for dependency inversion
- `guard` for early exits instead of nested `if let`
- `async/await` over callbacks
- `throws` instead of optional returns for errors
- Swift Testing (`@Test`, `#expect`) alongside XCTest


## Contributing

Contributions are welcome - new checks, better examples, typo fixes.

- Keep Markdown concise. Skills carry a token cost - respect the user's context budget.
- Don't repeat what LLMs already know. Focus on edge cases, surprises, and common mistakes.
- New skills should follow the same top-level `<skill-name>/SKILL.md` + `<skill-name>/agents/openai.yaml` layout.


## Credits

- Original repository and skill content: [Lev Bondarenko](https://github.com/levabond/iOS-clean-code-skills)
- Agent Skills repackaging (this fork): [Anton Novoselov](https://github.com/n0an)
