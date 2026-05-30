# Implementation Guide

## Next.js Defaults

- Use Next.js with TypeScript when starting a new product.
- Prefer App Router unless the repo already uses Pages Router.
- Suggested structure:
  - `app/` for routes and metadata.
  - `components/` for reusable UI and page sections.
  - `components/sections/` for product sections.
  - `components/ui/` for buttons, cards, badges, marquees, containers.
  - `lib/tokens.ts` or CSS variables for design tokens.
  - `public/assets/` for Figma exports and static media.

## Component System

- Extract design tokens before writing many components.
- Create primitives for button, icon button, card, badge, section heading, marquee, media frame, feature row, pricing card, footer CTA.
- Keep props product-aware and minimal. Avoid premature generic abstractions.
- Use accessible semantic HTML. Buttons are buttons; navigation links are links; decorative images have empty alt text.

## CSS and Layout

- Use the existing styling system if a repo already has one.
- For a fresh project, CSS Modules, Tailwind, or plain CSS are acceptable; choose the simplest path that matches the requested output.
- Use CSS variables for colors, typography, spacing, radius, shadow, and motion.
- Avoid nested cards unless the design explicitly uses nested surfaces.
- Use layout flow for section stacking. Use absolute layers inside a section for backgrounds, masks, and floating UI.
- Avoid one-note palettes and generic gradient backgrounds unless the design itself uses them.

## Responsive Rules

- Define breakpoints from actual design stress points.
- Keep desktop design faithful first; then adapt tablet/mobile.
- Use `clamp()` sparingly for layout sizes and typography. Do not use viewport-only font scaling.
- Use `aspect-ratio` for mockups, cards, media panels, boards, dashboards, and fixed-format compositions.
- Validate that no text overlaps, clips, or spills out of buttons/cards on mobile.

## Assets

- Download or copy Figma assets into the project.
- Keep filenames semantic: `hero-bg.mp4`, `showcase-office.png`, `purple-bg.png`, `logo.svg`.
- Remove obsolete assets only when no current HTML/CSS/JS reference uses them.
- For video hero backgrounds, keep overlay content in place and use `poster`, `autoplay`, `muted`, `loop`, and `playsinline`.

## Motion

- Implement after static layout is close.
- Use scroll reveal classes, IntersectionObserver, CSS keyframes, and hover transitions.
- Add marquees for logo/integration strips when the design calls for continuous movement.
- Keep durations calm: 500-900ms for reveal, 16-30s for marquees, 120-220ms for hover.
- Add `prefers-reduced-motion` fallbacks.

## Verification

- Run lint/typecheck/build when available.
- For static CSS/HTML, run a CSS brace/syntax check and `git diff --check`.
- Use browser screenshots at desktop and mobile when tooling allows.
- Verify public asset paths before deployment.
