# Project guidelines

## Responsive design is mandatory
Every design, prototype, page, or component produced in this project MUST be fully responsive and verified to work on:

- **Mobile** (320px – 480px wide, incl. small phones like iPhone SE)
- **Tablet** (481px – 1024px, both portrait and landscape)
- **Desktop** (1025px and up, through 1920px+)

### Hard requirements
1. **No horizontal scroll** at any viewport width. Use `overflow-x: hidden` on `body` as a safety net when large absolutely-positioned decorative elements are used.
2. **Use Tailwind's responsive prefixes** (`sm:`, `md:`, `lg:`, `xl:`) on every multi-column grid, flex row, font size, and padding/margin that meaningfully changes between devices.
3. **Stack grids on mobile**: `grid-cols-1` → `sm:grid-cols-2` → `lg:grid-cols-3` (or similar). Never leave a 3+ column grid without a stacking breakpoint.
4. **Wrap flex rows** that contain 3+ siblings: add `flex-wrap` plus `gap-y-*` so they reflow on narrow screens.
5. **Scale typography**: large display headlines must shrink on mobile (e.g. `text-4xl sm:text-6xl lg:text-7xl`). No headline should overflow at 320px.
6. **Touch targets** ≥ 44px on mobile. Buttons, links, and form inputs must remain tappable.
7. **Nav patterns**: hide secondary nav links behind a hamburger on mobile (`hidden md:flex`). Ensure logo + primary CTA + menu icon all fit at 320px wide.
8. **Form fields**: full-width on mobile, comfortable inner padding, no zoom on focus (input font-size ≥ 16px on iOS).
9. **Absolutely-positioned decorative elements** (blur orbs, glow effects) must not push content or cause overflow — clip them with `overflow-hidden` on their parent.
10. **Images and media** should use `max-w-full h-auto` or aspect-ratio utilities so they never break their container.

### Verification
After building, always ask the verifier subagent (via `fork_verifier_agent`) to specifically check responsive behavior at 375px, 768px, and 1280px before ending the turn. Report any layout breaks and fix them.

### When in doubt
Prefer fluid layouts (flex/grid with `gap`), relative units, and `min`/`max`/`clamp()` for sizing. Avoid fixed pixel widths on top-level containers.
