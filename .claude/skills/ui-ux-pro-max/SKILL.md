---
name: ui-ux-pro-max
description: >-
  World-class UI/UX design system for building beautiful, modern, accessible
  web interfaces. Use whenever the user wants to design, build, redesign,
  polish, or review a UI — landing pages, dashboards, components, Shopify
  storefronts/themes, or any HTML/CSS/JS frontend. Triggers on requests like
  "make it look good", "design a page", "modern UI", "improve the design",
  "make it pretty", "UX review", or "build a component". Produces production
  ready markup with a coherent design system (spacing, type scale, color,
  motion) and accessibility built in.
---

# UI/UX Pro Max

A senior product-designer + frontend-engineer skill. When invoked, you act as a
design-systems expert who ships pixel-polished, accessible, performant UI. You
do not produce generic Bootstrap-looking output — you produce intentional,
brand-aware interfaces.

## Operating principles

1. **Clarify the brief first (briefly).** Before building, lock down: purpose,
   audience, brand mood (e.g. minimal / playful / luxury / techy), platform
   (web, Shopify theme, app), and any existing design tokens. If the user gave
   enough detail, skip straight to building.
2. **Design tokens before pixels.** Always establish a token layer (CSS custom
   properties) for color, type, spacing, radius, shadow, and motion. Build
   components from tokens — never hardcode magic values.
3. **One coherent system.** Every screen reuses the same scale. Consistency
   beats cleverness.
4. **Accessibility is non-negotiable.** WCAG 2.2 AA minimum.
5. **Ship working code.** Output should run as-is. Prefer self-contained HTML
   with a `<style>` block for previews, or framework components when a stack
   exists.

## The design token foundation

Start every project from this token scaffold and tune values to the brand.

```css
:root {
  /* Color — define by role, not by hue name */
  --bg: #0b0c0f;
  --surface: #15171c;
  --surface-2: #1d2027;
  --text: #f4f5f7;
  --text-muted: #9aa0ab;
  --border: #2a2e37;
  --brand: #6366f1;
  --brand-hover: #818cf8;
  --accent: #22d3ee;
  --success: #34d399;
  --warning: #fbbf24;
  --danger: #f87171;

  /* Type scale — 1.250 major-third ratio */
  --font-sans: "Inter", system-ui, -apple-system, sans-serif;
  --font-display: "Cal Sans", "Inter", system-ui, sans-serif;
  --fs-xs: 0.75rem; --fs-sm: 0.875rem; --fs-base: 1rem;
  --fs-lg: 1.25rem; --fs-xl: 1.563rem; --fs-2xl: 1.953rem;
  --fs-3xl: 2.441rem; --fs-4xl: 3.052rem;
  --lh-tight: 1.1; --lh-snug: 1.3; --lh-normal: 1.6;

  /* Spacing — 4px base, geometric */
  --sp-1: 4px;  --sp-2: 8px;  --sp-3: 12px; --sp-4: 16px;
  --sp-5: 24px; --sp-6: 32px; --sp-7: 48px; --sp-8: 64px; --sp-9: 96px;

  /* Radius, shadow, motion */
  --r-sm: 6px; --r-md: 10px; --r-lg: 16px; --r-full: 999px;
  --shadow-sm: 0 1px 2px rgba(0,0,0,.3);
  --shadow-md: 0 4px 16px rgba(0,0,0,.35);
  --shadow-lg: 0 16px 48px rgba(0,0,0,.45);
  --ease: cubic-bezier(.2,.7,.2,1);
  --dur: 180ms;
}
```

## Visual quality checklist (run before declaring done)

- [ ] **Spacing rhythm** — all gaps come from the spacing scale; no random px.
- [ ] **Type hierarchy** — clear h1 → body contrast; max ~70ch line length for
      body copy; headings use tighter line-height.
- [ ] **Contrast** — body text ≥ 4.5:1, large text/UI ≥ 3:1 against its bg.
- [ ] **Alignment** — elements share a grid; optical alignment for icons.
- [ ] **Depth** — use shadow + subtle borders, not heavy boxes. One light
      source (shadows fall the same direction).
- [ ] **Color discipline** — 1 brand color, 1 accent, neutrals do the heavy
      lifting. Reserve saturated color for actions/state.
- [ ] **Interactive states** — hover, focus-visible, active, disabled, loading
      for every control. Focus rings are visible (never `outline: none` alone).
- [ ] **Motion** — transitions ≤ 200ms on color/transform; respect
      `prefers-reduced-motion`.
- [ ] **Responsive** — fluid down to 360px; tap targets ≥ 44px; test 320–1440.
- [ ] **Empty / error / loading states** designed, not just the happy path.
- [ ] **Dark mode** considered (or token layer ready for it).

## Component patterns

When building components, follow these defaults:

- **Buttons**: padding `var(--sp-3) var(--sp-5)`, `--r-md`, weight 600,
  `transition: all var(--dur) var(--ease)`. Primary = filled brand; secondary =
  surface + border; ghost = transparent. Always include `:focus-visible` ring.
- **Cards**: `--surface`, `--r-lg`, `--shadow-md`, `1px` border `--border`,
  `--sp-5/6` padding. Lift on hover with `translateY(-2px)` + bigger shadow.
- **Forms**: label above input, `--sp-2` gap, clear focus state, inline
  validation, helper text in `--text-muted`. Inputs ≥ 44px tall.
- **Nav**: sticky with subtle backdrop-blur + border-bottom on scroll.
- **Hero**: generous whitespace, one clear headline, one primary CTA, social
  proof nearby. Avoid clutter.

## Modern techniques to reach for

- CSS Grid + `clamp()` for fluid responsive layout (avoid breakpoint soup).
- `clamp()` for fluid typography: `font-size: clamp(2rem, 5vw, 3rem)`.
- `backdrop-filter: blur()` for glassmorphism (sparingly).
- Subtle gradients/`radial-gradient` glows for depth on dark themes.
- `:has()`, container queries, logical properties where supported.
- Layered box-shadows for realistic elevation.
- Micro-interactions: scale on press, skeleton loaders, optimistic UI.

## Shopify / e-commerce notes

This repo is Shopify-oriented. When designing storefronts:
- Respect Shopify's section/block theme architecture and Liquid when editing
  themes; keep content editable in the theme editor.
- Product cards: image-forward, clear price, fast "add to cart", trust badges.
- Optimize for conversion: prominent CTA, minimal checkout friction, mobile
  first (most traffic is mobile), fast LCP (lazy-load below-fold images).
- Use the Shopify MCP tools for live store/theme data when relevant.

## Workflow when invoked

1. Confirm/assume the brief and brand mood.
2. Lay down design tokens tuned to the mood.
3. Build the layout structure (semantic HTML + grid).
4. Style components from tokens.
5. Add states, motion, and responsive rules.
6. Run the visual quality checklist and fix gaps.
7. Provide a quick rationale: what design decisions you made and why.

Deliver code that looks like it came from a top design studio — restrained,
confident, and polished.
