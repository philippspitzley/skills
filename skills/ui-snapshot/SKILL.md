---
name: ui-snapshot
description: After building any UI component, extract the visual patterns that matter for consistency and save them to context/ui-registry.md. Use when a new UI component is built, when asked to capture component patterns, or when running an audit on existing UI.
---

# UI Snapshot

Extracts visual patterns from UI components and saves them to `context/ui-registry.md` so every component built after this one matches what came before.

## How to Invoke

```
/ui-snapshot              # capture from recently modified components
/ui-snapshot [filepath]   # capture from a specific file
/ui-snapshot audit        # scan entire codebase for inconsistencies
```

If no filepath is given, the skill identifies recently created or modified component files automatically.

---

## Standard Mode — `/ui-snapshot`

### Step 1 — Find What Was Just Built

If a filepath was provided — read that file directly. Otherwise, identify which component files were most recently created or modified in this session. If unclear, ask: `Which component should I capture patterns from?`

### Step 2 — Read the Registry

Load `context/ui-registry.md`. If it does not exist, create it with a blank `## Entries` section. If an entry for this component type already exists, update it rather than duplicating.

### Step 3 — Extract What Matters for Consistency

Read the component code. Extract only the classes and values that affect visual consistency — not everything, only what makes components look like they belong together.

**Extract:**

- Background — bg- class for containers, cards, panels
- Border — color, width, style
- Border radius — rounded- class
- Text colors — primary, secondary, muted
- Text sizes and weights — headings, body, labels, captions
- Spacing — padding, gap
- Interactive states — hover, focus, active
- Shadow — if used
- Accent or brand color usage

**Skip** (too context-dependent): width/height, flex/grid layout, positioning, animation timing, responsive variants.

**Also capture structure:** wrapper elements, nesting, title/body/layout pattern, icon placement, slot/children pattern.

### Step 4 — Write to ui-registry.md

Append a new entry (or update existing). Use this format:

```markdown
### [Component Name]

File: [filepath]
Last updated: [date]

**Structure:**
[Wrapper elements, nesting, title/body/layout pattern]

| Property         | Class           |
| ---------------- | --------------- |
| Background       | [class]         |
| Border           | [class]         |
| Border radius    | [class]         |
| Text — primary   | [class]         |
| Text — secondary | [class]         |
| Spacing          | [class]         |
| Hover state      | [class]         |
| Shadow           | [class or none] |
| Accent usage     | [class or none] |

**Pattern notes:**
[Why a specific class was chosen, what this component
should always match, what variations are allowed]
```

### Step 5 — Confirm

After writing, confirm to the developer:

```
Saved [Component Name] → ui-registry.md
Captured: [list key classes]
Any future component of this type should match these patterns.
```

If anything looked inconsistent or surprising — flag it with a note.

---

## Audit Mode — `/ui-snapshot audit`

Use when the UI already exists and consistency is uncertain. Scans the entire codebase, finds conflicts, and establishes a clean baseline.

### Step 1 — Scan All UI Components

Find every component file in the project. Read each one. Build a complete picture of what visual patterns are currently in use.

### Step 2 — Identify Conflicts

For each visual property that matters for consistency, list every variation found with a recommendation to standardise. Flag any hardcoded hex values or non-token classes.

### Step 3 — Wait for Developer Confirmation

Present the audit report. Do not fix anything or update ui-registry.md yet. Ask the developer to confirm the recommendations before proceeding.

### Step 4 — Write the Confirmed Baseline

After confirmation, write the agreed baseline to `context/ui-registry.md`:

```markdown
## Baseline — Established [date]

[Note: This baseline was established via /ui-snapshot audit]

| Property         | Correct class |
| ---------------- | ------------- |
| Card background  | [class]       |
| Card border      | [class]       |
| Card radius      | [class]       |
| Button primary   | [class]       |
| Button secondary | [class]       |
| Text primary     | [class]       |
| Text secondary   | [class]       |
| Text muted       | [class]       |
| Input background | [class]       |
| Input border     | [class]       |
```

### Step 5 — List What Needs Fixing

Produce a fix list — every component that deviates from the baseline, with what's wrong and what it should be. The developer can now fix these systematically, or as they encounter each component. Going forward, `/ui-snapshot` keeps new components consistent.
