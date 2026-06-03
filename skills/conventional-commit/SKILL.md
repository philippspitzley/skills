---
name: conventional-commit
description: Analyzes git diffs and proposes a strict Conventional Commits 1.0.0 message. Use this to generate commit messages before committing code.
---

# Conventional Commit Generator

Your goal is to analyze uncommitted changes and propose a highly accurate commit message following the official Conventional Commits 1.0.0 specification.

## 1. Analyze Changes
Use your `bash` tool to run:
- `git status`
- `git diff` (or `git diff --cached` if files are already staged)
This helps you understand exactly what was changed.

## 2. Determine Type
Select the most appropriate type based on the diff:
- `fix`: Patches a bug in the codebase (correlates with PATCH in SemVer).
- `feat`: Introduces a new feature to the codebase (correlates with MINOR in SemVer).
- `build`: Changes that affect the build system or external dependencies.
- `chore`: Other changes that don't modify `src` or test files.
- `ci`: Changes to CI configuration files and scripts.
- `docs`: Documentation only changes.
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
- `refactor`: A code change that neither fixes a bug nor adds a feature.
- `perf`: A code change that improves performance.
- `test`: Adding missing tests or correcting existing tests.

## 3. Determine Scope (Optional)
Identify the specific section of the codebase affected (e.g., `parser`, `api`, `lang`). It MUST be a noun surrounded by parentheses.

## 4. Check for Breaking Changes (MAJOR)
If the commit introduces a breaking API change, you MUST either:
1. Append a `!` after the type/scope (e.g., `feat(api)!: `).
2. AND/OR include a `BREAKING CHANGE:` footer.

## 5. Draft the Message
Draft the commit message using this exact structure:

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Rules for Drafting:**
- **Description:** MUST immediately follow the colon and space. It is a short summary of the code changes.
- **Body (Optional):** MUST begin one blank line after the description. Use this to provide contextual information about the code changes.
- **Footer (Optional):** MUST be one blank line after the body. Used for things like `BREAKING CHANGE: <description>`, `Refs: #123`, or `Reviewed-by: Z`.
- The units of information MUST NOT be treated as case-sensitive, except for `BREAKING CHANGE` which MUST be uppercase.

## 6. Present the Proposal
Present the drafted commit message to the user inside a code block. 
Ask the user: *"Do you approve this commit message, or would you like to make adjustments before we commit?"*
Do NOT execute `git commit` until the user explicitly approves the message.