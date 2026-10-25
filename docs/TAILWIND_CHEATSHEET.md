# BuildBoard — Tailwind CSS Cheatsheet & Architecture Reference

A comprehensive guide to all Tailwind CSS classes, custom design tokens, responsive breakpoints, and styling patterns used across the **BuildBoard** project.

---

## 1. Custom Theme Tokens (`@theme` in `index.css`)

BuildBoard uses **Tailwind CSS v4** with a custom design system mapped to light/dark CSS custom properties (`index.css`):

| Tailwind Utility | Underlying CSS Token | Light Mode Value | Dark Mode Value | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| `bg-[var(--bg-page)]` | `--bg-page` | `#fbfaf7` (Warm Paper) | `#0b100c` (Obsidian) | Main canvas / body background |
| `bg-[var(--bg-surface)]` | `--bg-surface` | `#ffffff` (Pure White) | `#131914` (Deep Forest) | Card and modal surface background |
| `bg-[var(--bg-surface-subtle)]` | `--bg-surface-subtle` | `#f4f1ea` (Soft Beige) | `#19221b` (Subtle Ink) | Muted badges, secondary button backgrounds |
| `text-[var(--text-main)]` | `--text-main` | `#141a15` (Deep Ink) | `#f3f4f0` (Warm Linen) | High-contrast headings and primary labels |
| `text-[var(--text-muted)]` | `--text-muted` | `#434f45` (Slate Forest) | `#b0baa9` (Muted Celadon) | Descriptions, subtitles, and body text |
| `text-[var(--text-subtle)]` | `--text-subtle` | `#68766a` (Soft Gray) | `#828e7d` (Muted Sage) | Timestamp captions, keyboard hints, icons |
| `border-[var(--border-main)]` | `--border-main` | `#e2ded4` (Warm Craft) | `#242f26` (Deep Tactile) | Card outlines, dividers, input borders |
| `border-[var(--border-strong)]` | `--border-strong` | `#cfc9bd` | `#324235` | Hovered borders and focused borders |
| `bg-[#d96b43]` / `text-[#d96b43]` | `--accent-coral` | `#d96b43` (Terracotta) | `#e07a5f` (Soft Terracotta) | Brand primary action color (CTAs, active pills) |
| `font-display` | `--font-display` | `DM Sans` | `DM Sans` | Brand headings (`h1`, `h2`, `h3`) |
| `font-sans` | `--font-sans` | `DM Sans` | `DM Sans` | Default interface body text |
| `font-mono` | `--font-mono` | `JetBrains Mono` | `JetBrains Mono` | Code snippets, stats, hashes, and URLs |

---

## 2. Layout, Structure & Positioning

| Utility | CSS Equivalent | BuildBoard Use Case |
| :--- | :--- | :--- |
| `sticky top-0 z-40` | `position: sticky; top: 0; z-index: 40;` | Pinned sticky Navbar that stays visible during scrolling |
| `fixed inset-0 z-50` | `position: fixed; top: 0; right: 0; bottom: 0; left: 0; z-index: 50;` | Full-screen modal overlay for listing deletion |
| `relative` | `position: relative;` | Anchor parent for absolute icons, badges, and layout IDs |
| `absolute inset-y-0 left-0` | `position: absolute; top: 0; bottom: 0; left: 0;` | Search bar magnifying glass icon position |
| `absolute inset-y-0 right-0` | `position: absolute; top: 0; bottom: 0; right: 0;` | Clear search button and keyboard shortcut hint (`/`) |
| `w-full max-w-7xl mx-auto` | `width: 100%; max-width: 80rem; margin: auto;` | Central responsive content container |
| `min-h-screen` | `min-height: 100vh;` | Ensures page containers stretch full viewport height |
| `overflow-x-auto` | `overflow-x: auto;` | Horizontal scrolling container for category pills on mobile |

---

## 3. Flexbox & Grid Layouts

| Utility | CSS Property | BuildBoard Use Case |
| :--- | :--- | :--- |
| `flex items-center justify-between` | `display: flex; align-items: center; justify-content: space-between;` | Header rows, card footer stats, navbar brand + actions |
| `flex flex-col gap-4` | `display: flex; flex-direction: column; gap: 1rem;` | Form fields stack, comment lists, vertical card layouts |
| `flex flex-wrap gap-2` | `display: flex; flex-wrap: wrap; gap: 0.5rem;` | Category tags, technology badges, targeting options |
| `inline-flex items-center gap-1.5` | `display: inline-flex; align-items: center; gap: 0.375rem;` | Pill tags with icon + text (e.g. `★ 142`) |
| `shrink-0` | `flex-shrink: 0;` | Prevents SVGs, avatars, or tags from being squeezed |
| `grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-3 gap-8` | CSS Grid with responsive column counts | Explore catalog cards layout |
| `grid lg:grid-cols-[1.1fr_0.9fr] gap-10` | Two-column asymmetric editorial layout | Product Details (1.1fr Info / 0.9fr Action Studio) |
| `grid lg:grid-cols-2` | Two equal columns | Sign In / Sign Up split layout (Editorial left / Form right) |

---

## 4. Typography & Text Hierarchy

| Utility | Font Size / Weight | BuildBoard Use Case |
| :--- | :--- | :--- |
| `text-xs font-semibold` | `12px / 600` | Tag badges, status indicators, meta captions |
| `text-sm leading-relaxed` | `14px / line-height: 1.625` | Form labels, helper text, and feedback copy |
| `text-base` | `16px` | Standard body paragraphs and search bar text |
| `text-xl sm:text-2xl font-bold` | `20px / 24px (700)` | Section headings, dialog titles |
| `text-3xl sm:text-5xl font-extrabold` | `30px / 48px (800)` | Product name title on Product Details page |
| `text-4xl sm:text-5xl lg:text-6xl font-display` | `36px to 60px` | Hero headings on Landing & Auth pages |
| `tracking-tight` | `letter-spacing: -0.025em;` | Tight editorial headings |
| `uppercase tracking-wider` | `text-transform: uppercase; letter-spacing: 0.05em;` | Kicker tags (e.g. `DIRECTORY`, `SECURITY`) |
| `truncate` | `overflow: hidden; text-overflow: ellipsis; white-space: nowrap;` | Maker emails, long URLs, single-line links |
| `break-words` | `overflow-wrap: break-word;` | Prevents custom user titles from overflowing cards |

---

## 5. Borders, Surfaces & Elevation

| Utility | Value | BuildBoard Use Case |
| :--- | :--- | :--- |
| `rounded-full` | `border-radius: 9999px;` | Category pills, CTA buttons, search inputs, avatar rings |
| `rounded-xl` | `border-radius: 0.75rem;` | Media thumbnails, code blocks, smaller cards |
| `rounded-2xl` | `border-radius: 1rem;` | Standard cards, status notices, feedback items |
| `rounded-3xl` | `border-radius: 1.5rem;` | Auth boxes, hero cards, confirmation modals |
| `border border-[var(--border-main)]` | 1px border with token color | General component borders |
| `border-t border-[var(--border-main)] pt-6` | Top divider line with spacing | Separates sections inside a card or footer |
| `border-l-2 border-[#d96b43]/30 pl-4` | 2px left colored border | Visual guide line for threaded nested comments |
| `shadow-warm-xs` | `0 1px 2px rgba(20,26,21,0.03)` | Buttons and inputs |
| `shadow-warm-md` | `0 4px 12px rgba(20,26,21,0.06)` | Floating dropdowns, hover cards |
| `shadow-warm-xl` | `0 20px 36px rgba(20,26,21,0.09)` | High-elevation modals and auth boxes |

---

## 6. Glassmorphism & Translucency

| Utility | CSS Value | BuildBoard Use Case |
| :--- | :--- | :--- |
| `backdrop-blur-md` | `backdrop-filter: blur(12px);` | Frosted-glass sticky Navbar scrolling over content |
| `backdrop-blur-xs` | `backdrop-filter: blur(4px);` | Subtle backdrop blur behind the delete modal overlay |
| `bg-[var(--bg-surface)]/90` | `opacity: 0.9` | Semi-translucent surface tint for sticky header |
| `bg-black/60` | `rgba(0, 0, 0, 0.6)` | Dimmed background overlay behind modal dialogues |
| `bg-[#d96b43]/10` | `rgba(217, 107, 67, 0.1)` | Subtle terracotta tinted pill badges |
| `border-[#d96b43]/30` | `rgba(217, 107, 67, 0.3)` | Soft terracotta accent border |

---

## 7. Interactive States & Micro-Animations

| Utility | State / Trigger | BuildBoard Use Case |
| :--- | :--- | :--- |
| `hover:bg-[#b85028]` | Hover | Darkens primary terracotta button on mouseover |
| `hover:-translate-y-0.5` | Hover | Lifts button/card by $2\text{px}$ for tactile elevation |
| `active:translate-y-0` | Click / Active | Presses button back down to normal height |
| `transition duration-200` | State change | Smooth $200\text{ms}$ easing between colors and transforms |
| `cursor-pointer` | Cursor hover | Pointer cursor on interactive cards, buttons, and pills |
| `focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-[#d96b43]` | Keyboard Tab Focus | High-visibility accessible focus ring for accessibility |
| `animate-spin` | Infinite CSS keyframe | Rotating loading spinner during page Suspense & API calls |
| `animate-pulse` | Infinite opacity pulse | Skeleton loading boxes for live GitHub repo insights |

---

## 8. Responsive Design Breakpoints

| Breakpoint Prefix | Screen Width Threshold | Example Pattern in BuildBoard |
| :--- | :--- | :--- |
| *(None / Mobile First)* | `< 640px` (Phones) | Single column, stacked cards, full-width buttons (`w-full`) |
| `sm:` | `≥ 640px` (Tablets / Phablets) | `sm:flex-row sm:items-center sm:grid-cols-2` |
| `md:` | `≥ 768px` (Small Laptops) | `hidden md:flex` (hides mobile menu, displays desktop nav) |
| `lg:` | `≥ 1024px` (Desktop) | `lg:grid-cols-[1.1fr_0.9fr] lg:p-14` (split layout) |
| `xl:` | `≥ 1280px` (Widescreen) | `xl:grid-cols-3` (3-column product catalog) |

---

## 9. Dark Mode Styling Pattern (`dark:`)

BuildBoard defines a custom dark variant in CSS:
```css
@custom-variant dark (&:where(.dark, .dark *));
```

This enables seamless pairing of light and dark utilities on the same element:

```jsx
<button
  className="
    /* Light Mode Default */
    border-rose-500/30 bg-rose-500/10 text-rose-700 hover:bg-rose-500/20
    /* Dark Mode Override */
    dark:border-rose-500/40 dark:bg-rose-500/20 dark:text-rose-300 dark:hover:bg-rose-500/30
  "
>
  Remove Listing
</button>
```

---

## 10. Common Component Recipes

### A. Primary Action Button (Terracotta CTA)
```jsx
<button
  type="button"
  className="inline-flex items-center justify-center gap-2 rounded-full bg-[#d96b43] px-6 py-3 text-sm font-bold text-white shadow-warm-xs transition hover:bg-[#b85028] hover:-translate-y-0.5 active:translate-y-0 cursor-pointer focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-[#d96b43]"
>
  <span>Open Live Prototype</span>
  <span aria-hidden="true">↗</span>
</button>
```

### B. Interactive Filter Pill
```jsx
<button
  type="button"
  className={`rounded-full px-4 py-2 text-sm font-semibold transition cursor-pointer ${
    isActive
      ? 'bg-[#d96b43] text-white shadow-warm-xs'
      : 'border border-[var(--border-main)] bg-[var(--bg-page)] text-[var(--text-muted)] hover:text-[var(--text-main)] hover:border-[var(--border-strong)]'
  }`}
>
  {category}
</button>
```

### C. Glassmorphism Sticky Navbar
```jsx
<header className="sticky top-0 z-40 w-full border-b border-[var(--border-main)] bg-[var(--bg-surface)]/90 backdrop-blur-md transition-colors">
  <div className="mx-auto flex h-16 max-w-7xl items-center justify-between px-5 sm:px-8">
    {/* Navigation Items */}
  </div>
</header>
```
