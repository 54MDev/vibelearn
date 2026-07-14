# Better Looks Update

Goal: make VibeLearn look genuinely good on **both desktop and mobile**. Right now everything is a 640px column — fine on a phone, a skinny strip on a laptop. This plan upgrades the visuals and adds real desktop layouts.

Files to change: `index.html`, `resources.html`. Keep it deployable on GitHub Pages with no build step (edit → push → done).

## 1. Framework: Tailwind CSS (Play CDN)

Add Tailwind via its CDN script tag in `<head>` of both pages — one line, no build step, works on GitHub Pages:

```html
<script src="https://cdn.tailwindcss.com"></script>
```

- Keep the existing color palette as Tailwind theme config (inline `tailwind.config` script): bg `#0d0d12`, card `#17171f`, accent `#c8ff00`, text `#f2f2f5`, dim `#9a9aa5`, border `#2a2a35`.
- Keep the Outfit/Inter Google Fonts.
- Migrate the inline `<style>` blocks to Tailwind utility classes. A small `<style>` block may remain for the typing-cursor animation and anything Tailwind can't express cleanly.

> Why not React: a 2-page static site with zero interactivity gains nothing from React, and it would force a build step (Vite/npm) that breaks the current "edit HTML and push" workflow. If interactivity is added later (signup logic, session data from an API), revisit — see "Optional: React path" at the bottom.

## 2. Desktop vs mobile: responsive breakpoints (not two sites)

One codebase. Use Tailwind's responsive prefixes — mobile styles are the default, desktop kicks in at `md:` (768px) and `lg:` (1024px). This *is* the "way to tell between the two": the browser width decides.

Concrete layout changes at desktop width:

### index.html
- **Container:** mobile stays ~640px; desktop widens to `max-w-5xl` (~1024px) with generous horizontal padding.
- **Nav:** add a slim sticky top nav on desktop (`VibeLearn ⚡` left, links to Sessions / Resources / "I want in" button right). On mobile, collapse to just the logo + button (no hamburger menu needed for 2 pages).
- **Hero:** desktop gets a bigger headline (`text-7xl`+), tagline on one line, more vertical breathing room, and a subtle radial glow behind the headline in the accent color (`radial-gradient`, low opacity).
- **Next sessions:** cards stack vertically on mobile (as now); on desktop, show them in a 2- or 3-column grid. Highlighted card gets a stronger accent glow.
- **What you'll make:** 2×2 grid on mobile (as now) → 4 across on desktop, with hover lift effect (`hover:-translate-y-1 transition`).
- **What's vibecoding:** on desktop, split into a 2-column layout — heading left, the 3 lines right — instead of one narrow stack.
- **Join section:** desktop gets a full-width accent-tinted band (very subtle, e.g. accent at 5% opacity background) so it stands out as the closing CTA.

### resources.html
- Same container/nav treatment.
- **Start here / Keep going cards:** single column mobile → 2-column grid desktop.
- **From class:** keep as a list (it'll grow week by week); just give the empty state a nicer dashed-border card.

## 3. Visual polish (both breakpoints)

- **Buttons:** add hover state (slight glow: `box-shadow` in accent at ~40% opacity) and `hover:scale-[1.03]` on desktop; keep the existing `:active` press effect.
- **Cards:** hover border shifts toward accent on desktop (`hover:border-accent/50 transition-colors`).
- **Section rhythm:** more vertical spacing on desktop (`py-24` vs mobile `py-12`); drop the hard 1px section dividers in favor of spacing, or keep them at lower opacity.
- **Headings:** each `h2` gets a small accent-colored eyebrow label above it (e.g. "01 — SESSIONS" in mono/uppercase tracking) for structure without clutter.
- **Footer:** slightly richer — logo, email, page links in a row on desktop, stacked on mobile.
- **Hero typing effect:** keep it, it's the one animation. Add `prefers-reduced-motion` media query to disable the blink for users who've turned animations off.
- Everything must stay readable: contrast of dim text on dark bg should pass WCAG AA (current `#9a9aa5` on `#0d0d12` is fine — don't go dimmer).

## 4. Acceptance checklist

- [ ] Both pages look intentional at 375px (iPhone), 768px (tablet), and 1440px (laptop) — no skinny-strip desktop layout
- [ ] No horizontal scrolling at any width
- [ ] No build step: opening `index.html` directly in a browser still works
- [ ] All existing content and links preserved (Google Form placeholder, mailto, cross-page links)
- [ ] Tap targets ≥ 44px on mobile
- [ ] Test by resizing the browser window across the breakpoints

## Optional: React path (only if requested)

If we decide we truly want React later: Vite + React + Tailwind, deployed to GitHub Pages via a GitHub Action that runs `npm run build` on push. Costs: node_modules, a build pipeline, and you can no longer edit a single HTML file to update session dates. Benefit today: none. Skip unless the site grows interactive features.
