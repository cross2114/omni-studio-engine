# Pixel Review

## Figma Extraction

- Use `get_design_context` first for visual context, assets, and suggested structure.
- Use `get_metadata` for exact x/y/width/height, layer hierarchy, hidden alternates, masks, and coordinates.
- Use `get_screenshot` for section screenshots when visual comparison is needed.
- Convert design coordinates to CSS deliberately. For a 1920px Figma frame, center a 1200px object with `left: 50%`, `width: min(1200px, calc(100% - gutter))`, and `transform: translateX(-50%)`.
- Preserve asset dimensions and crop. If Figma uses an image at `1152 x 648` inside a `1200 x 695` glass frame, implement both layers, not a single flattened approximation unless the source asset is already flattened.

## Matching Priorities

1. Page order and section heights.
2. Background layers, masks, gradients, and opacity.
3. Primary assets and crop/object-position.
4. Containers, columns, and alignment.
5. Typography: family, weight, size, line-height, color, casing.
6. Spacing between major blocks.
7. Radius, border, shadow, blur, opacity.
8. Icons and small UI details.
9. Motion and interaction.

## Review Method

- Review from top to bottom. Do not fix a lower section before upstream spacing is stable.
- Measure key distances: hero viewport height, header inset, logo/login positions, marquee height, heading-to-mockup gap, mockup-to-next-section gap, card sizes, footer height.
- Compare both numeric values and screenshot feel. If numeric values match but the page still looks wrong, inspect image crop, background layer timing, opacity, or hidden whitespace in assets.
- Keep a short punch list of visible mismatches. Fix one group at a time, then re-check.
- Do not mark complete until the current browser/screenshot view and Figma screenshot agree at the same viewport.

## Common Failure Modes

- Correct asset but wrong crop or object-position.
- Flattened mockup replacing a layered glass frame.
- Background starts too late or ends too early.
- Shadow values approximate but opacity/color wrong.
- Responsive layout keeps desktop spacing on mobile.
- Icon placeholders left where actual brand icons are required.
- Visual gap differs from DOM gap because an image contains internal blank area.
- Header elements drift because they are centered by flex instead of pinned to design coordinates.

## Precision Rules

- Use exact design numbers when the design gives them: width, height, radius, shadow, border, gap.
- Use proportional scaling only when the viewport is smaller than the design frame.
- For critical fixed-format UI, set `aspect-ratio`.
- Avoid decorative substitutes unless the user approves.
- Confirm fonts are loaded and fallback behavior is acceptable.
