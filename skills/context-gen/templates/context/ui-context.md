# UI Context

## Theme

[Describe the overall visual language — e.g. Dark only.
No light mode. The design language is a dark technical
workspace — near-black backgrounds, layered surfaces,
and vivid accent colors for interactive elements.]

## Colors

[Define your color tokens as CSS custom properties.
All components must use these tokens — no hardcoded
hex values.]

| Role            | CSS Variable       |  Value (olkch) |
| --------------- | ------------------ |  ------------- |
| Page background | `--bg-base`        |  oklch(x y z)  |
| Surface         | `--bg-surface`     |  oklch(x y z)  |
| Primary text    | `--text-primary`   |  oklch(x y z)  |
| Muted text      | `--text-muted`     |  oklch(x y z)  |
| Primary accent  | `--accent-primary` |  oklch(x y z)  |
| Border          | `--border-default` |  oklch(x y z)  |
| Error           | `--state-error`    |  oklch(x y z)  |
| Success         | `--state-success`  |  oklch(x y z)  |

## Typography

| Role      | Font              | Variable      |
| --------- | ----------------- | ------------- |
| UI text   | [e.g. Geist Sans] | `--font-sans` |
| Code/mono | [e.g. Geist Mono] | `--font-mono` |

## Border Radius

| Context           | Class            |
| ----------------- | ---------------- |
| Inline / small UI | `rounded-[size]` |
| Cards / panels    | `rounded-[size]` |
| Modals / overlays | `rounded-[size]` |

## Component Library

[e.g. shadcn/ui on top of Tailwind. Components live
in components/ui/. Use the CLI to add new components
rather than writing from scratch.]

## Layout Patterns

- [Pattern — e.g. Editor: full-viewport split with
  left sidebar, center canvas, right sidebar]
- [Pattern — e.g. Sidebars: fixed width with border separator]
- [Pattern — e.g. Modals: centered overlay with backdrop blur]
- [Pattern — e.g. Navbar: top bar with bottom border]

## Icons

[e.g. Lucide React. Stroke-based icons only. Sizes:
h-4 w-4 for inline, h-5 w-5 for buttons.]

## Component Patterns

See `ui-registry.md` for the living record of every
component built in this project. It tracks the concrete
classes and structure used for each component type so
every new component matches what came before.
