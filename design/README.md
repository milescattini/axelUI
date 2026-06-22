# Axel Design System — Seed Prompt

You are building a landing page using the Axel design system. Read this file before writing a single line of HTML or copy. Everything you need is here.

---

## What this is

A reusable design system for marketing landing pages targeting SMB founders and operators. Two layers:

- **Layer 1 — Visual tokens** (`global.json`, `semantic.json`): colours, type, spacing, and motion values. `global.json` holds raw values; `semantic.json` maps them to intent. Never use a raw value from `global.json` directly in a component — always go through a semantic token.
- **Layer 2 — Voice & tone** (`voice-tone.md`): how copy is written. Read it before writing any content.

---

## How to build a page

### 1. Compile the tokens to CSS

```bash
npx style-dictionary build --config design/style-dictionary.config.json
```

This outputs `public/tokens.css`. Link it in the `<head>` of every page:

```html
<link rel="stylesheet" href="tokens.css">
```

Then use semantic token names as CSS custom properties:

```css
body {
  background: var(--sd-color-surface-page);
  color: var(--sd-color-text-primary);
  font-family: var(--sd-font-family-body);
}
```

Never write a raw hex value or pixel value in component CSS. Every value traces back to a token.

### 2. Load the fonts

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600&family=DM+Mono&display=swap" rel="stylesheet">
```

`Plus Jakarta Sans` is the only body and heading font. `DM Mono` is for code blocks only — not labels, not eyebrows, not decorative use.

### 3. Write copy before writing HTML

Read `voice-tone.md`. Then write the headline and subheadline before scaffolding any markup. If the copy sounds like a SaaS landing page, it's wrong.

---

## Token quick reference

Compiled CSS variables follow the pattern `--sd-[category]-[subcategory]-[name]`.

### Colour

| Semantic token | CSS variable | Value | Use |
|---|---|---|---|
| `color.surface.page` | `--sd-color-surface-page` | `#F9F8F6` | Body background |
| `color.surface.raised` | `--sd-color-surface-raised` | `#FFFFFF` | Cards, panels |
| `color.surface.subtle` | `--sd-color-surface-subtle` | `#F1EEE9` | Alternating section tint |
| `color.surface.inverse` | `--sd-color-surface-inverse` | `#1A1816` | Dark hero / CTA sections |
| `color.text.primary` | `--sd-color-text-primary` | `#1A1816` | Body copy |
| `color.text.secondary` | `--sd-color-text-secondary` | `#635D58` | Supporting / muted text |
| `color.text.tertiary` | `--sd-color-text-tertiary` | `#9E9690` | Placeholder, fine print |
| `color.text.inverse` | `--sd-color-text-inverse` | `#F9F8F6` | Text on dark sections |
| `color.accent.default` | `--sd-color-accent-default` | `#2C5FD4` | CTAs, links, highlights |
| `color.accent.hover` | `--sd-color-accent-hover` | `#1E4DB0` | Hover state |
| `color.accent.subtle` | `--sd-color-accent-subtle` | `#EDF3FF` | Tags, selected state |
| `color.border.default` | `--sd-color-border-default` | `#E3DEDA` | Hairlines, dividers |
| `color.border.focus` | `--sd-color-border-focus` | `#2C5FD4` | Focus rings |

### Typography

| Semantic token | CSS variable | Value |
|---|---|---|
| `font.family.body` | `--sd-font-family-body` | Plus Jakarta Sans |
| `font.family.code` | `--sd-font-family-code` | DM Mono — code blocks only |
| `font.size.display` | `--sd-font-size-display` | 3.5rem — hero headline |
| `font.size.h1` | `--sd-font-size-h1` | 2rem |
| `font.size.h2` | `--sd-font-size-h2` | 1.5rem |
| `font.size.h3` | `--sd-font-size-h3` | 1.25rem |
| `font.size.lead` | `--sd-font-size-lead` | 1.125rem — intro paragraphs |
| `font.size.body` | `--sd-font-size-body` | 1rem |
| `font.size.caption` | `--sd-font-size-caption` | 0.875rem |
| `font.size.label` | `--sd-font-size-label` | 0.75rem — eyebrows, metadata |
| `font.weight.heading` | `--sd-font-weight-heading` | 600 |
| `font.weight.emphasis` | `--sd-font-weight-emphasis` | 500 |
| `font.weight.body` | `--sd-font-weight-body` | 400 |
| `font.leading.heading` | `--sd-font-leading-heading` | 1.1 |
| `font.leading.body` | `--sd-font-leading-body` | 1.6 |
| `font.tracking.heading` | `--sd-font-tracking-heading` | -0.03em |
| `font.tracking.label` | `--sd-font-tracking-label` | 0.06em — uppercase labels only |

### Spacing

| Semantic token | CSS variable | Value | Use |
|---|---|---|---|
| `space.component.xs` | `--sd-space-component-xs` | 8px | Badge / tag padding |
| `space.component.sm` | `--sd-space-component-sm` | 12px | Button vertical padding |
| `space.component.md` | `--sd-space-component-md` | 16px | Button horizontal, input padding |
| `space.component.lg` | `--sd-space-component-lg` | 24px | Card internal padding |
| `space.layout.section-y` | `--sd-space-layout-section-y` | 96px | Section vertical padding |
| `space.layout.stack` | `--sd-space-layout-stack` | 24px | Gap between content blocks |
| `space.layout.gutter` | `--sd-space-layout-gutter` | 24px | Grid column gap |
| `space.layout.max-width` | `--sd-space-layout-max-width` | 1160px | Container max width |

### Radius, shadow, motion

| Semantic token | CSS variable | Value |
|---|---|---|
| `radius.button` | `--sd-radius-button` | 8px |
| `radius.input` | `--sd-radius-input` | 4px |
| `radius.card` | `--sd-radius-card` | 8px |
| `radius.panel` | `--sd-radius-panel` | 12px |
| `radius.badge` | `--sd-radius-badge` | 999px |
| `shadow.card-hover` | `--sd-shadow-card-hover` | Subtle — hover state only |
| `shadow.dropdown` | `--sd-shadow-dropdown` | Floating elements |
| `motion.interactive` | `--sd-motion-interactive` | 200ms |
| `motion.reveal` | `--sd-motion-reveal` | 400ms |
| `motion.easing` | `--sd-motion-easing` | cubic-bezier(0.4, 0, 0.2, 1) |

---

## Layout conventions

- Max content width: `1160px`, centred, `24px` horizontal padding on mobile.
- Sections alternate: `surface.page` → `surface.subtle` → `surface.page`. Not arbitrary colours.
- `surface.inverse` (dark) is used once per page maximum — hero or a final CTA block, not both.
- Grid: 12-column at desktop, single column on mobile. Use CSS Grid, no framework.

---

## Visual rules (non-negotiable)

- **One accent.** `accent.default` only. No second accent, no gradients, no colour washes on multiple sections.
- **Two weights in body content.** `weight.body` (400) and `weight.emphasis` (500). `weight.heading` (600) for headlines only.
- **Mono for code only.** Never use `font.family.code` for labels, tags, system names, eyebrows, or metadata. It reads as AI-generated decoration.
- **Shadows on hover only.** No resting card shadows. `shadow.card-hover` applies on `:hover` / `:focus-visible` only.
- **No emoji. No decorative icon grids.** Diagrams only when they show something prose cannot.
- **Sentence case everywhere.** Uppercase + `tracking.label` only for short eyebrow labels above a heading.

---

## Copy rules (non-negotiable)

Full guide in `voice-tone.md`. The short version:

1. **Lead with consequence.** What goes wrong if they skip this? What gets easier if they don't?
2. **Name the real thing.** ABN, ASIC, shareholders agreement, vesting cliff — not "your business setup."
3. **No vague claims.** Every sentence earns its place with a tool, a number, a step, or a named scenario.
4. **Peer voice.** No "we're here to help you on your journey."
5. **Banned:** empower, seamless, unlock, navigate (metaphorical), journey, leverage, robust, solution/s, streamline, game-changer, holistic, ecosystem.
6. **Australian English.** AUD, GST, BAS, ABN, ACN, Pty Ltd, ASIC, Corporations Act.
7. **No fabricated social proof.** No invented testimonials, client names, or metrics.

---

## What not to build

- Three identical centred icon cards in a row.
- Hero with a gradient background.
- Glassmorphism, resting box shadows, layered blur effects.
- Full-page dark mode as the default surface.
- Stock illustration of a person at a laptop.
- "Trusted by X companies" badge row for a product with no customers.

---

## Adapting this system for a new project

Only `global.json` changes between projects. Edit the `color` and `font.family` blocks to match the brand, recompile, done. `semantic.json` and `voice-tone.md` stay the same. See the per-client swap guide in the previous `README.md` (now superseded by this file) for the step-by-step.
