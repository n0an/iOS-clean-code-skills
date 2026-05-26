# swift-clean-code

Clean Code skills for Swift / iOS projects based on Robert Martin's *Clean Code* and G. Ann Campbell's *Cognitive Complexity*.

Created by [Lev Bondarenko](https://github.com/levabond). This repository repackages the skills into the [Agent Skills](https://agentskills.io/home) format so they install with a single `npx` command in Claude Code, Codex, Cursor, Gemini, and more.

## Skills

### Slash commands

| Command | What it does |
|---|---|
| `/swift-clean-names` | Review and fix naming: variables, functions, types, protocols |
| `/swift-clean-functions` | Audit function size, single responsibility, argument count, DRY |
| `/swift-clean-types` | Review class/struct/protocol design, SRP, dependency injection |
| `/swift-clean-errors` | Audit `throws`, optionals, `Result`, custom `Error` types |
| `/swift-clean-tests` | Check FIRST principles, AAA pattern, test naming, mocking |
| `/swift-clean-review` | Full Clean Code audit of a file or directory |
| `/swift-cognitive-complexity` | Score and reduce Cognitive Complexity: nesting, closures, control flow |

### Automatic (model-invoked)

`swift-clean-advisor` — activates when writing or editing Swift files. Applies Clean Code guidance without being asked.

## Installation

Install any skill with `npx`:

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

If `npx` is missing, install Node (`brew install node`); if `brew` is missing too, [install Homebrew](https://brew.sh) first.

### Alternative install methods

**Claude Code** (installs the whole bundle):

```bash
/plugin install n0an/iOS-clean-code-skills
```

**Gemini** (installs the whole bundle):

```bash
gemini extensions install https://github.com/n0an/iOS-clean-code-skills.git --consent
```

Or clone this repository and drop the skill folders wherever your agent expects them.

## Usage

```bash
# Review naming in a file
/swift-clean-names Sources/Auth/LoginViewModel.swift

# Audit function design
/swift-clean-functions Sources/Services/NetworkService.swift

# Full audit of a module
/swift-clean-review Sources/Features/Checkout/

# Review test quality
/swift-clean-tests Tests/UserServiceTests.swift

# Score and reduce cognitive complexity
/swift-cognitive-complexity Sources/Features/Checkout/CheckoutViewModel.swift
```

## Requirements

- Claude Code CLI (or another Agent Skills-compatible agent: Codex, Cursor, Gemini, ...)
- Xcode project (any architecture: MVC, MVVM, TCA, etc.)
