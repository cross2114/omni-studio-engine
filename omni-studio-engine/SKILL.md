---
name: omni-studio-engine
description: End-to-end AI digital product delivery engine for turning Figma designs into production web apps. Use when the user says "Use Omni Studio Engine" or asks to implement, rebuild, pixel-match, componentize, animate, make responsive, deploy, or maintain a SaaS, dashboard, landing page, Web3 product, AI product, or other digital product from Figma/design assets with exact visual fidelity and production code.
---

# Omni Studio Engine

## Mission

Deliver a complete product from Figma to production with disciplined design analysis, component-system extraction, pixel-level implementation, responsive behavior, animation, deployment, and maintainable code.

Treat this as a delivery engine, not a one-shot Figma-to-code conversion. Iterate until the page matches the design, including spacing, assets, layer relationships, shadows, typography, image crop, responsive layout, animation, and deployment behavior.

## Core Workflow

1. Read the source design.
   - Use Figma MCP when a Figma URL is provided. Prefer `get_design_context`, then `get_metadata` for coordinates/layer hierarchy, then screenshots for visual comparison.
   - Extract file key and node id from the URL. Convert `node-id=154-4` to `154:4`.
   - If Figma access fails, use exported screenshots/assets and state the limitation clearly.

2. Build the design inventory.
   - Record layout bounds, page width, section heights, grid columns, spacing, typography, colors, radii, borders, shadows, opacity, blend effects, image crop, and asset dimensions.
   - Identify reusable components: header, nav, buttons, cards, logo strips, feature rows, forms, pricing cards, footer, empty/loading/error states.
   - Create design tokens before page code: color, type scale, spacing, radius, shadow, z-index, motion, breakpoint, container widths.

3. Establish the implementation system.
   - Prefer Next.js unless the user asks otherwise or an existing project requires another stack.
   - Build a component library first, then pages. Keep components named by product role, not by visual accident.
   - Match existing project conventions when working in an existing repo.
   - Use real design assets. Do not replace detailed imagery with generic gradients or decorative shapes.

4. Implement top-down.
   - Build in page order from first viewport to footer.
   - For every section, set the section box, background/layer stack, content container, typographic hierarchy, assets, then interactions.
   - Preserve layer relationships: background images, masks, overlays, foreground cards, floating UI, shadows, and crop positions must match the design.
   - Use absolute positioning only for design-critical overlays or fixed-format compositions; use layout flow for ordinary sections.

5. Add responsive behavior.
   - Derive breakpoints from where the design naturally breaks, not from arbitrary device names.
   - Preserve hierarchy and spacing ratios on tablet/mobile.
   - Use stable constraints: `aspect-ratio`, `min/max`, container width, grid tracks, and predictable image object positions.
   - Avoid viewport-scaled font sizes. Use tokenized clamp ranges only when needed.

6. Add interaction and motion.
   - Add scroll reveal, marquee, hover, focus, and subtle ambient motion only after static fidelity is close.
   - Keep motion aligned with the product style. Motion should make the page feel smoother, not distract from the design.
   - Respect `prefers-reduced-motion`.

7. Review visually and numerically.
   - Compare against Figma section by section. Measure coordinates, dimensions, gaps, font sizes, radii, shadows, opacity, and asset crop.
   - Do not trust one metric if the visual result still feels wrong. Screenshot review and user-marked comments take priority.
   - Fix from top to bottom so later sections do not drift unpredictably.
   - Read `references/pixel-review.md` before final visual QA.

8. Validate code quality.
   - Run formatting/lint/typecheck/build where available.
   - For CSS-heavy static work, at minimum run syntax checks and `git diff --check`.
   - Confirm assets referenced in HTML/CSS exist and unused assets are removed only when clearly obsolete.

9. Deploy.
   - Use the user’s requested deployment path: GitHub Pages, Netlify, Vercel, or existing CI.
   - Commit intentionally, pull/rebase remote changes before pushing, and never force-push unless the user explicitly approves.
   - Confirm the deployment status and provide the public URL.
   - Read `references/deployment.md` before publishing.

## References

- `references/pixel-review.md`: Use for pixel-level design review and Figma-to-code matching.
- `references/implementation.md`: Use for Next.js structure, components, responsive rules, and animation.
- `references/deployment.md`: Use for GitHub/Netlify/Vercel release flow and delivery checklist.

## User Prompt Pattern

Expected usage:

```text
Use Omni Studio Engine

Figma:
<figma-url>

目标：
将整个项目开发并部署上线

要求：
- 100%还原
- 保持设计系统一致
- 自动生成组件库
- 自动部署
```

When requirements conflict, prioritize: user’s latest instruction, design fidelity, production correctness, maintainability.
