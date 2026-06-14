# Severity Guide

Not all issues are equal. Use this to help the developer prioritise.

## Critical — fix before moving on

- Architecture boundary violations that will break future features
- Missing error handling that causes silent failures
- Functionality that was planned but completely missing
- Security vulnerabilities

## Important — fix soon

- Design system drift that will cause UI inconsistency
- Code standard violations that will compound across the codebase
- Edge cases that a real user will encounter
- Missing input validation

## Minor — fix when convenient

- Naming inconsistencies that do not affect behaviour
- Missing optimisations
- Style issues that do not affect the design system
- Documentation gaps

Label each issue with its severity so the developer can triage quickly.
