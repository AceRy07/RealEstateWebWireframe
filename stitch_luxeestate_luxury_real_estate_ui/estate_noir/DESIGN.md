# Design System Document: The Editorial Estate

## 1. Overview & Creative North Star
**Creative North Star: "The Digital Curator"**

This design system is not a template; it is a high-end editorial experience. We are moving away from the "functional utility" of standard real estate portals and toward the "curated gallery" of a luxury lifestyle magazine. 

To achieve this, the system breaks the rigid, boxed-in nature of traditional web design. We prioritize **intentional asymmetry**, where high-resolution architectural photography is allowed to bleed off-grid or overlap with glass containers. The aesthetic is defined by "breathing room"—expansive white space (or in our case, deep navy space) that signals exclusivity and calm. We do not fill every pixel; we curate every pixel.

---

## 2. Colors & Tonal Depth

Our palette is anchored in the depth of a midnight sky, punctuated by the warmth of polished gold.

### The Palette (Material 3 Logic)
*   **Surface / Background (`#0b1326`):** The foundation. It is deep, immersive, and recedes to let imagery pop.
*   **Primary (`#eec152`):** Our "Signature Gold." Use this for focal points and primary calls to action.
*   **Primary Container (`#cba135`):** A muted, burnished gold for hover states and secondary emphasis.
*   **On-Surface (`#dae2fd`):** An off-white with a hint of coolness to prevent harsh contrast and maintain an elegant "glow."

### The "No-Line" Rule
**Explicit Instruction:** You are prohibited from using 1px solid borders to define sections. 
Boundaries must be created through **Background Shifts**. For example, a section detailing property amenities should use `surface-container-low` to sit subtly atop the main `surface` background. The transition is felt, not seen.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of materials. 
1.  **Level 0 (Base):** `surface` (`#0b1326`).
2.  **Level 1 (Sections):** `surface-container-low` (`#131b2e`).
3.  **Level 2 (Cards/Modules):** `surface-container` (`#171f33`).
4.  **Level 3 (Floating/Glass):** Semi-transparent `surface-bright` with `backdrop-filter: blur(20px)`.

### The "Glass & Gradient" Rule
To evoke a sense of premium "soul," use subtle linear gradients on CTAs: `linear-gradient(135deg, #eec152 0%, #cba135 100%)`. For floating property cards, use **Glassmorphism**: a background of `rgba(49, 57, 77, 0.4)` combined with a heavy background blur to create a "frosted sapphire" effect.

---

## 3. Typography: The Editorial Voice

We pair the timeless authority of a serif with the clinical precision of a modern sans-serif.

*   **Display & Headlines (Noto Serif / Playfair Equivalent):** 
    *   *Role:* Emotional resonance. 
    *   *Usage:* Property titles, hero statements, and section headers. Use `display-lg` (3.5rem) with wide letter-spacing to command attention.
*   **Body & Titles (Inter):** 
    *   *Role:* Functional clarity. 
    *   *Usage:* Descriptions, technical specs, and UI labels. Inter’s tall x-height ensures readability even at `body-sm` (0.75rem) against dark backgrounds.

**Hierarchy Note:** Always maintain a high contrast between your `headline-lg` and `body-md`. This gap creates the "Editorial" feel found in luxury print media.

---

## 4. Elevation & Depth: Tonal Layering

Traditional drop shadows are too "software-like." We use **Ambient Depth**.

*   **The Layering Principle:** Depth is achieved by stacking. A `surface-container-highest` card placed on a `surface` background provides enough "lift" through color alone.
*   **Ambient Shadows:** If a shadow is required for a floating modal, use a 12% opacity shadow using the `primary-fixed-variant` color rather than black. This creates a "gold-tinted" glow that feels like light reflecting off premium finishes. 
    *   *Spec:* `0px 20px 40px rgba(90, 67, 0, 0.12)`.
*   **The "Ghost Border" Fallback:** If a container needs a edge (e.g., in a search input), use `outline-variant` (`#4e4636`) at **15% opacity**. It should be a whisper of a line, barely visible.

---

## 5. Components

### Buttons: The Signature Touchpoints
*   **Primary:** Solid Gold (`primary`). No border. `label-md` uppercase text with 0.1em letter spacing. Radius: `md` (0.375rem).
*   **Secondary (Glass):** `surface-bright` at 20% opacity + backdrop blur. Text is `primary`.
*   **Tertiary:** Text-only. Use `primary` color with a 1px underline that appears only on hover.

### Cards: The Property Showcase
*   **Rule:** Forbid divider lines. 
*   **Construction:** Use `surface-container-low`. Top half is an edge-to-edge image. Bottom half uses `title-lg` for the price and `body-md` for the address. 
*   **Hover State:** The card should subtly scale (1.02x) and the background shift to `surface-container-high`.

### Input Fields: The Concierge Experience
*   Background: `surface-container-lowest`.
*   Active State: The bottom border glows with a 2px `primary` line. Helper text appears in `on-surface-variant`.
*   Focus: Avoid the standard blue ring. Use a soft `primary` outer glow (4px blur).

### Signature Component: The "Glass Navigation"
The top navigation bar should not be a solid block. It is a floating `surface-container` with 60% opacity and 32px backdrop-blur. This allows the property photography to scroll underneath it, creating a sense of continuity and "wet" transparency.

---

## 6. Do’s and Don'ts

### Do:
*   **Do** use asymmetrical layouts (e.g., text block at 4 columns, image at 7 columns with a 1-column gap).
*   **Do** use high-quality photography as a functional UI element.
*   **Do** leverage `surface-variant` for "inactive" or "muted" information like square footage or property ID.

### Don’t:
*   **Don’t** use pure black (`#000000`). It kills the depth of the navy.
*   **Don’t** use standard 1px grey dividers. Use 48px of vertical whitespace instead.
*   **Don’t** use "Select" dropdowns that look like OS defaults. Design them as custom glass overlays.
*   **Don’t** crowd the interface. If a screen feels busy, remove an element; do not shrink it.

---

## 7. Accessibility & Readability
While we aim for "Luxury," we must remain "Legible." 
*   Ensure all `on-surface` text on `surface` backgrounds meets WCAG AA standards. 
*   Interactive elements (Buttons/Chips) must have a minimum height of 44px for touch targets.
*   The `error` token (`#ffb4ab`) should be used sparingly for validation—styled as a soft red glow or text, never as a jarring bright red box.