# CLAUDE.md — wonder-coffee-assets

## Repository Overview

This repository contains the CSS stylesheet asset for the **Eden** premium coffee brand landing page. It is a single-file, static CSS project with no build tooling, dependencies, or backend code.

**Primary file:** `wonder-coffee-style.css` (minified, production-ready)

---

## Repository Structure

```
wonder-coffee-assets/
└── wonder-coffee-style.css   # Complete landing page stylesheet (minified)
```

There are no subdirectories, package files, or configuration files. This is intentionally a minimal, standalone asset repository.

---

## CSS Architecture

### Design System

**Color palette** (CSS custom properties defined in `:root`):

| Variable         | Value     | Usage                        |
|------------------|-----------|------------------------------|
| `--green-bright` | `#8DC63F` | Primary brand color, CTAs    |
| `--green-lime`   | `#B5D934` | Accent, hover states         |
| `--green-deep`   | `#3A6B35` | Dark backgrounds             |
| `--green-mid`    | `#5A8A3C` | Secondary elements           |
| `--green-pale`   | `#EEF5E0` | Light section backgrounds    |
| `--white`        | `#FFF`    | Pure white                   |
| `--off-white`    | `#F7FAF0` | Warm white backgrounds       |
| `--dark`         | `#1C2B18` | Near-black for deep sections |
| `--text`         | `#2D4028` | Body text                    |
| `--muted`        | `#6B8060` | Secondary/subdued text       |
| `--yellow`       | `#F0C93A` | Highlight accents            |
| `--red-fruit`    | `#C0392B` | Warning / fruit accent       |

**Typography:**
- Body: `DM Sans` (Google Fonts)
- Headings: `DM Serif Display` (Google Fonts)
- Fluid sizing via `clamp()` throughout

**Spacing:** Based on an 8px grid; gaps/paddings use multiples of 8px.

**Transitions:** Standard duration is `0.3s` on all interactive elements.

---

### Page Sections & Key Classes

| Section       | Key Classes                                    | Description                                         |
|---------------|------------------------------------------------|-----------------------------------------------------|
| Navigation    | `.nav`, `.nav-logo`, `.nav-links`              | Fixed, frosted-glass bar with `backdrop-filter`     |
| Hero          | `.hero`, `.hero-inner`, `.hero-title`          | Full-screen gradient + floating fruit decorations   |
| Product       | `.product-img-wrap`, `.product-img`            | Animated product image with glow effect             |
| Taste Ticker  | `.ticker`, `.ticker-track`                     | Marquee-style scrolling text band                   |
| Tasting       | `.tasting`, `.flavor-card`, `.flavor-tags`     | Two-column layout, flavor profile bars              |
| Story         | `.story`, `.process-steps`                     | Brand heritage narrative                            |
| Specs Band    | `.specs-band`, `.spec-chip`                    | 5-column product specification grid                 |
| Storage       | `.storage`                                     | Care/storage instructions                           |
| Order         | `.order`, `.btn-green`, `.btn-white`           | Call-to-action with dual button styles              |
| Footer        | `.footer`                                      | Branding and origin                                 |

---

### Button Variants

| Class              | Style                                |
|--------------------|--------------------------------------|
| `.btn-green`       | Solid green primary CTA              |
| `.btn-white`       | Solid white secondary                |
| `.btn-outline-white` | Ghost/outline on dark backgrounds  |

---

### Animations (Keyframes)

| Name           | Duration  | Purpose                                    |
|----------------|-----------|--------------------------------------------|
| `fruitFloat`   | 7–10s     | Floating decorative fruit elements in hero |
| `productFloat` | 6s        | Gentle bounce + rotate on product image    |
| `ticker`       | 20s       | Continuous horizontal marquee scroll       |
| `growBar`      | 1.5s      | Flavor profile bar grow-in on load         |
| `fadeUp`       | triggered | Fade + translate-up reveal (`.visible`)    |

The `.visible` class is applied via JavaScript to trigger `fadeUp` on scroll.

---

## Naming Conventions

- **Classes:** BEM-inspired kebab-case (`.section-name`, `.section-element`, `.section-element--modifier`)
- **CSS variables:** `--property-name` kebab-case
- **Keyframes:** camelCase (`fruitFloat`, `growBar`)
- **Responsive breakpoint:** Single mobile breakpoint at `max-width: 900px`

---

## Development Workflow

### Editing the Stylesheet

The CSS is stored minified. When making changes:

1. **Edit in an unminified/expanded form** for readability, then re-minify before committing.
2. Prefer extending existing CSS variables over introducing new color/size literals.
3. Keep new components consistent with the existing section pattern: a wrapper block (`.section-name`) containing an inner container (`.section-name-inner` or `.section-inner`).
4. Maintain the single-breakpoint mobile pattern (`@media (max-width: 900px)`).

### No Build Process

There is no build step, package manager, or preprocessor. The CSS file is used directly as a static asset.

### Testing

There are no automated tests. Visual review in a browser against the Eden landing page HTML is the primary validation method.

---

## Git Conventions

- **Main branch:** `master`
- **Feature/AI branches:** prefix `claude/` (e.g., `claude/claude-md-mmi4omo5s6r37exz-CLEY6`)
- Commits should have short, descriptive messages describing what changed and why.
- Do not commit unminified CSS — the deployed file should always be minified.

---

## Key Constraints for AI Assistants

1. **Do not introduce new files** unless explicitly requested. This repo is intentionally single-file.
2. **Preserve the minified format** of `wonder-coffee-style.css` when committing final changes.
3. **Use existing CSS variables** — do not hardcode color or spacing values that are already defined in `:root`.
4. **Do not add a build system** (npm, webpack, etc.) without explicit instruction.
5. **Maintain the single-breakpoint responsive pattern** at `900px`; do not add additional breakpoints without discussion.
6. **Do not modify the color palette** variables without explicit design direction, as they define the brand identity.
7. When adding new sections, follow the existing section structure and animation patterns.
