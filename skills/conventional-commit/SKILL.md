---
name: conventional-commit
description: Analyzes git diffs and proposes a strict Conventional Commits 1.0.0 message. Use this to generate commit messages before committing code.
---

# Conventional Commit Generator

Analyze uncommitted changes and propose a commit message following Conventional Commits 1.0.0.

## 1. Analyze Changes
Run `git status` and `git diff` (or `git diff --cached` if staged).

## 2. Determine Type
Pick the best match:
- `fix`: Bug fix (PATCH)
- `feat`: New feature (MINOR)
- `refactor`: Code change that fixes no bug and adds no feature
- `perf`: Performance improvement
- `test`: Adding/updating tests
- `docs`: Documentation only
- `chore`: Maintenance, non-src/test changes
- `build`, `ci`, `style`: Build system, CI config, or whitespace/formatting

## 3. Scope (Optional)
Noun in parentheses: `feat(parser): add new parser`. Common scopes: `api`, `auth`, `ui`.

## 4. Breaking Changes
If breaking API change:
- Append `!` after type/scope: `feat(api)!: `
- AND/OR include `BREAKING CHANGE:` footer

## 5. Draft Message
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Rules:**
- Header ≤ 72 chars
- Description: imperative mood ("add" not "added"), no period
- Conciseness: "and" → "&", use short verbs (add/fix/rm), drop filler (the/a/an/to)
- Body: explain *what* and *why*, not *how*
- Footer: `Refs: #123` or `Reviewed-by: Name`

## 6. Present
Present the message in a code block.
