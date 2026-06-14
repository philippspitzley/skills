# Review Report Format

Use this exact structure for every review.

```markdown
## Review — [Feature Name]

### Layer 1 — Plan alignment
[PASS / ISSUES FOUND]

[List any gaps between what was planned and what was built]

### Layer 2 — System integrity
[PASS / ISSUES FOUND]

[List any architecture, design, or code standard violations]

### Layer 3 — Production readiness
[PASS / ISSUES FOUND]

[List any error handling gaps, edge cases, or obvious bugs]

### Summary
[X] issues found across [Y] layers.

[If no issues: "No issues found. This feature is ready to ship."]
[If issues: "Resolve the above before moving to the next feature."]

### Issues

| # | Severity | Layer | Description |
|---|----------|-------|-------------|
| 1 | Critical / Important / Minor | 1 / 2 / 3 | [Brief description] |
```

## Rules

- Use PASS only when zero issues exist in that layer
- List every issue — do not group or summarise away details
- Severity must match the guide in `references/severity-guide.md`
- The summary line must have an accurate count
- Do not soften language — "ISSUES FOUND" not "some minor concerns"
