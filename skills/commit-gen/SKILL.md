---
name: commit-gen
description: Analyzes git diffs and proposes a strict Conventional Commits 1.0.0 message. Use this to generate commit messages before committing code.
---

# Conventional Commit Generator

Analyze uncommitted changes and propose a commit message following Conventional Commits 1.0.0.

## 1. Analyze Changes
Run `git status` and `git diff` (or `git diff --cached` if staged).

## 2. Style Analysis
Run `git log --oneline -20`. Extract:
- Verb preferences (add/create, fix/resolve, rm/remove)
- Scope naming (short/long, separator style)
- Capitalization convention
- Abbreviation patterns

Apply these patterns for project consistency.

## 3. Determine Type
Pick the best match:
- `fix`: Bug fix (PATCH) — signals defect resolution
- `feat`: New feature (MINOR) — signals user-facing capability
- `refactor`: Code restructure — no bug or feature, just clarity/maintainability
- `perf`: Performance improvement — speed or resource gains
- `test`: Test additions or corrections — coverage or assertion fixes
- `docs`: Documentation only — no code changes
- `chore`: Maintenance — deps, config, non-src/test changes
- `build`, `ci`, `style`: Build system, CI config, or formatting

## 4. Scope (Optional)
Noun in parentheses: `feat(parser): add new parser`. Common scopes: `api`, `auth`, `ui`.

## 5. Breaking Changes
If breaking API change:
- Append `!` after type/scope: `feat(api)!: `
- AND/OR include `BREAKING CHANGE:` footer

## 6. Draft Message
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Rules:**
- Header ≤ 72 chars — fits git log, email subjects, PR titles
- Description: imperative mood ("add" not "added"), no period — git generates revert messages from this
- Conciseness: "and" → "&", short verbs (add/fix/rm), drop filler (the/a/an/to) — scanability in terminal
- Body: concise `-` bullets of *what* changed and *why* — reviewers need rationale, not just diffs
- Footer: `Refs: #123` or `Reviewed-by: Name` — traceability to issues and reviewers

## 7. Present
Present the message in a code block.
