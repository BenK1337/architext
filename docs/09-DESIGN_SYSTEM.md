# 🎨 Architext AI - Design System & Theme

This document defines the visual language, tokens, and component standards for the Architext AI project. It is inspired by Google Agentspace/AI Studio and is the single source of truth for all UI/UX implementation.

---

## 1. Design Principles
- **Clarity:** Prioritize information hierarchy, whitespace, and clear visual feedback.
- **Delight:** Use subtle, purposeful animations and micro-interactions.
- **Consistency:** Reuse patterns, spacing, and components across the app.
- **Accessibility:** Meet WCAG AA standards. All interactive elements are keyboard/focus accessible.
- **Responsiveness:** Mobile-first, fluid layouts, and adaptive components.

---

## 2. Theme & Design Tokens
All tokens are defined in `/src/lib/styles/theme.css` as CSS custom properties for easy theming and dark mode support.

- **Colors:** Primary, secondary, background, surface, border, error, success, warning, info, overlays, gradients, disabled, on-primary/surface.
- **Typography:** Inter/Roboto, scalable font sizes, weights, heading/body/caption styles.
- **Spacing:** 4px grid, scale from 0–4rem, container max-width.
- **Elevation:** 4 shadow levels for depth and overlays.
- **Radii:** Small/medium/large/full for buttons, cards, modals.
- **Transitions:** Fast/medium/slow cubic-bezier for UI feedback.

---

## 3. Component Library Structure
- **Atoms:** Button, Icon, Input, Checkbox, Radio, Switch, Spinner, Tooltip, Badge, Avatar
- **Molecules:** Card, List, Tab, Modal, Alert/Toast, Collapsible, Progress, Dropdown, Menu
- **Organisms:** Header, Sidebar, Project Card, Task List, Document Section, Auth Form, Dashboard Widgets
- **Templates:** Main layout, Onboarding, Dashboard, Project, Auth, Error/Empty states

---

## 4. Animation & Micro-interactions
- **Navigation:** Slide/fade transitions for route/page changes
- **Modals/Drawers:** Scale+fade in/out, focus trap, overlay dim
- **Tabs/Collapsible:** Smooth expand/collapse, indicator slide
- **Buttons:** Ripple/touch, scale on press, color transitions
- **Feedback:** Loading spinners, skeletons, toast/alert fade/slide
- **Stateful UI:** Hover/focus/active/disabled overlays, subtle shadow/color shifts

---

## 5. Accessibility (a11y)
- Semantic HTML, ARIA roles/labels
- Keyboard navigation, visible focus rings
- Color contrast meets or exceeds AA
- Test with screen readers

---

## 6. File & Folder Structure
- **Tokens:** `/src/lib/styles/theme.css`
- **Global styles:** `/src/lib/styles/global.css`
- **Component styles:** `/src/lib/components/*/*.module.css`
- **Component code:** `/src/lib/components/*/*.svelte`
- **Design system docs:** `/docs/09-DESIGN_SYSTEM.md`

---

## 7. References
- `/docs/design_examples/` (visuals, flows, states, animations)
- `/docs/02-INSTRUCTIONS.md` (coding & style conventions)

---

*Keep this document up to date as the design system evolves!*
