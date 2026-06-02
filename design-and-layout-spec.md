# Design and Layout Specification

Source: `source-default-layout.html`.

## Extracted layout

- App shell uses CSS Grid.
- Default page padding: 22px.
- Medium page padding: 18px.
- Narrow page padding: 14px.
- Default columns: sidebar, component panel, main workspace, assistant panel.
- Sidebar expanded width: 240px.
- Sidebar collapsed width: 76px.
- Component panel width: 340px to 390px.
- Assistant panel width: 360px to 430px.
- Main workspace uses fluid minmax sizing.

## Extracted radius

- Outer panels: 24px to 28px.
- Cards: 22px to 26px.
- Header clusters and controls: 16px to 24px.
- Pills/search: 999px or large pill radius.

## Extracted shadow

- Soft surface shadow: `0 10px 26px rgba(55,72,110,.06)`.
- Card hover shadow: `0 18px 42px rgba(50,72,120,.13)`.
- Primary KPI shadow: `0 20px 45px rgba(47,107,255,.28)`.

## Extracted interaction

- Card hover: subtle upward movement, stronger shadow, soft border color.
- KPI hover: preserve height, no layout compression.
- Navigation hover: small horizontal movement when expanded.
- Collapsed sidebar: icon-only with tooltip.
- Reduced motion: disable animation and transitions.

## Extracted responsive behavior

- Large screens: all panels visible.
- Medium screens: assistant panel can drop or compress.
- Tablet: component panel can collapse.
- Mobile: single-column flow with transformed content structure.
