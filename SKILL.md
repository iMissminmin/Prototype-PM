---
name: prototype-pm
description: Use this skill when a product manager needs to generate, review, or standardize product prototypes for App, Web SaaS/admin systems, or desktop clients. It applies a consistent prototype layout system extracted from the SalesAgent workspace HTML, including spacing, radii, shadows, hover interactions, responsive behavior, and reference-image independence.
---

# Prototype-PM

## Purpose

Prototype-PM helps product managers generate consistent, high-quality product prototypes across App, Web, and desktop-client scenarios. It must identify the application context first, then apply the matching layout pattern and design tokens.

This skill is based only on `reference/source-default-layout.html`, the SalesAgent intelligent workspace HTML. Do not mix in earlier skills, old MD files, industry-specific business frameworks, or unrelated visual systems.

## Core rule: reference images must not override this method

When the user provides screenshots, reference images, competitor pages, or visual examples, use them only to understand business semantics, information structure, and interaction intent. Do not copy their visual style, color, component appearance, page rhythm, or decorative treatment. Final output must follow this skill's original layout method, spacing, radius, shadow, interaction, and responsive rules.

## Scenario recognition

Before designing, classify the target platform:

- Web SaaS / admin / dashboard / CRM / management system: use the default multi-column workspace.
- Desktop client / desktop software / windowed app: keep the Web workspace density, but add stronger resize, title-bar, status, and collapsible-panel awareness.
- App / mobile / mini program: transform the layout into a mobile structure. Do not directly copy the desktop four-column layout.
- Unclear platform: infer from keywords. When still unclear, default to Web SaaS/admin because this source layout is a Web workspace.

## Default Web and desktop layout

Use a structured workspace shell:

```txt
App Shell
├── Sidebar: global navigation, expandable/collapsible
├── Component Panel: component entries, insight cards, task cards
├── Main Workspace: title/action area, KPI cards, charts, tables, core content
└── Assistant Panel: AI/helper panel, recommendations, command input
```

Default layout tokens:

- Page padding: 22px on large screens, 18px on medium screens, 14px on narrow screens.
- Column gap: 18px to 24px.
- Expanded sidebar width: 240px.
- Collapsed sidebar width: 76px.
- Component panel width: 340px to 390px.
- Main workspace: fluid, minimum 560px to 760px depending on viewport.
- Assistant panel width: 360px to 430px.
- Top action/header spacing: 14px to 20px.
- Card grid gap: 16px to 20px.

## Mobile App transformation

For App/mobile prototypes, convert the layout instead of shrinking it:

```txt
Mobile App
├── Top title/current context
├── Horizontal module switcher
├── KPI card carousel or 2-column card grid
├── Main content card flow
├── AI/helper floating entry or bottom sheet
└── Bottom tab navigation
```

Mobile tokens:

- Page padding: 14px to 16px.
- Card gap: 12px to 14px.
- Card radius: 18px to 22px.
- Main button height: 44px to 48px.
- Bottom tab height: 56px to 64px.
- Tables must become cards, horizontal scroll, or simplified list rows.

## Visual tokens

Use the following defaults unless the user's product brand explicitly requires adjustment:

```css
:root {
  --page: #f6f9ff;
  --surface: #ffffff;
  --surface-soft: #f8fbff;
  --primary: #2f6bff;
  --primary-2: #6aa8ff;
  --text: #132033;
  --muted: #6b7890;
  --line: #edf1f8;
  --shadow: 0 18px 45px rgba(50,72,120,.09);
  --shadow-soft: 0 10px 26px rgba(55,72,110,.06);
  --radius: 26px;
}
```

Color rules:

- Use blue as the primary interaction and selected-state color.
- Use soft green, orange, purple, and cyan only as semantic accents.
- Avoid high-saturation full-page gradients.
- Background may use very light radial gradients, but content surfaces must stay clean and readable.

Typography rules:

- Font stack: `-apple-system, BlinkMacSystemFont, SF Pro Display, PingFang SC, Microsoft YaHei, Arial, sans-serif`.
- Page title: 24px to 28px, strong weight, tight letter spacing.
- Section/card title: 16px to 18px.
- Body/table text: 13px to 14px.
- KPI number: 28px to 31px.
- Helper text: 12px to 13px.

## Radius and shadow rules

- Outer sidebar and assistant panel: 24px to 28px radius.
- Main cards: 22px to 26px radius.
- Small controls: 12px to 18px radius.
- Search and pill controls: 999px or large pill radius when appropriate.
- Use soft SaaS shadows only: avoid hard black shadows and strong glow.
- Primary KPI cards may use a stronger blue shadow, but only subtly.

## Padding rules

- App outer padding is the first rhythm anchor: default 22px.
- Sidebar padding: about 20px vertical, 16px horizontal.
- Main cards: 18px to 22px.
- Assistant panel: 18px to 20px.
- Compact cards: 16px to 18px.
- Header/control clusters: 7px to 14px internal padding.
- Preserve top/bottom/left/right rhythm. Do not let content touch the viewport or panel edges.

## Interaction rules

Default hover behavior:

```css
.card:hover,
.table-card:hover,
.left-card:hover {
  transform: translateY(-3px);
  border-color: rgba(188,210,248,.95);
  box-shadow: 0 18px 42px rgba(50,72,120,.13), 0 2px 8px rgba(47,107,255,.04);
}
```

- Keep hover movement subtle: usually `translateY(-2px)` to `translateY(-3px)`.
- Buttons and pills may lift `-1px` to `-2px`.
- Navigation items can move horizontally by 3px to 4px when expanded.
- Collapsed navigation items should not expose vertical text; use tooltips.
- Respect `prefers-reduced-motion: reduce` and disable animations when needed.

## Responsive and collapsible behavior

- Large desktop: keep all major panels visible.
- Around 1320px: assistant panel may move below the main area or become a drawer.
- Around 1280px: component panel can collapse or become a two-column section.
- Around 980px: collapse sidebar to mobile/overlay behavior.
- Around 720px: switch to single-column mobile flow.
- Collapsed sidebar must keep icons centered, avoid text overflow, and keep bottom actions aligned.
- When resizing, preserve proportional layout and prevent content clipping.

## Output requirements

When generating prototypes:

1. Build a complete first screen; do not leave the central workspace empty.
2. Use CSS Grid for the app shell and Flexbox for component internals.
3. Include realistic simulated data when the user has not provided data.
4. Use semantic HTML and self-contained CSS/JavaScript when outputting HTML.
5. Keep information hierarchy clear: one primary action per area, secondary actions as outline/ghost controls.
6. Avoid cheap-looking gradients, excessive glassmorphism, loud colors, heavy shadows, and PPT-like hero sections.
7. Keep all text readable and avoid overflow, overlap, or clipped shadows.

## Review checklist

Before final output, verify:

- Platform type has been identified: App, Web, or desktop client.
- Page padding follows the 22px / 18px / 14px rhythm.
- Main cards use 22px to 26px radius and soft shadows.
- Hover effects do not change box height or break layout.
- Collapsed panels have recovery entries and tooltips.
- Mobile output is transformed, not merely squeezed.
- Reference images did not override this skill's design method.
