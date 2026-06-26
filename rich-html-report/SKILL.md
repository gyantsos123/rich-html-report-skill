---
name: rich-html-report
description: >-
  Generate rich, beautiful single-file HTML reports/presentations in the
  "Governance Gradient" house style — Salesforce-blue palette, particle.js
  animated background, glassmorphism nav, 3D stacked-shadow buttons, deep
  drop-shadow cards, pill tags, and interactive steppers. Use when the user
  asks for a polished HTML page, report, talk track, deck, walkthrough, or
  landing-style document, or references the look of
  text-to-html/output/agent-vs-person-observability.html.
---

# Rich HTML Report (House Style)

Produces a self-contained `.html` file matching the project's signature look: a
fixed particle background under a deep blue gradient, frosted-glass navigation,
glossy 3D buttons, and cards with layered drop shadows and depth.

The canonical reference is
`text-to-html/output/agent-vs-person-observability.html`. This skill distills
that design into reusable assets so any new page looks identical.

## Workflow

1. **Copy the skeleton.** Start from [template.html](template.html) — it already
   contains the complete `<style>` block, particle background, nav, hero,
   footer, and the particles.js init script. Never rebuild the CSS from scratch.
2. **Write output to `text-to-html/output/<slug>.html`** unless the user says
   otherwise.
3. **Fill in content** by swapping the hero copy and replacing the example
   section with real sections. Pull component markup from
   [components.md](components.md).
4. **Keep it single-file and portable.** All CSS/JS stays inline or on CDNs.
   If a logo/image is needed, embed it as a base64 data URI so the file never
   has broken links (see "Embedding images" below).
5. **Set the `<title>`, nav logo text, hero eyebrow/headline, and footer** to
   match the topic.

## Non-negotiable design rules

These are what make a page look "on brand". Do not deviate.

- **Color tokens**: use the `:root` CSS variables from the template verbatim.
  Primary spectrum is Salesforce blue (`--blue-900` `#032D60` → `--blue-400`
  `#57A3FD`), with semantic amber/green/red for status. Never hardcode hex
  values that aren't in the token set.
- **Particle background**: keep `#particles-js` as a `position: fixed` layer
  with the `linear-gradient(135deg, --blue-900, --blue-700, --blue-600)` and the
  particles.js init exactly as in the template. All real content sits in
  `.content-wrapper` with `z-index: 1`.
- **Fonts**: `Inter` for text, `JetBrains Mono` for code, Font Awesome 6 for
  icons (all via the CDN `<link>`s already in the template).
- **Depth & shadows**: buttons and cards use the stacked-shadow technique — a
  hard offset shadow (`0 6px 0 var(--blue-900)`) plus a soft ambient shadow plus
  an inset top highlight. Hover lifts with `translateY(-2px)`; active presses
  down with `translateY(4px)`. Cards use multi-layer `box-shadow` for a raised,
  glossy panel. Copy these from the template rather than inventing new shadows.
- **Glassmorphism**: nav, hero stat tiles, and slides use semi-transparent
  white backgrounds + `backdrop-filter: blur(...)`.
- **Section rhythm**: alternate `.section-light`, `.section-gray`, and
  `.section-featured` (dark blue) bands. Each section opens with a
  `.section-icon` tile, an `<h2 class="section-title">`, and a
  `.section-lede`.
- **Responsive**: keep the `@media (max-width: 1024px)` and `768px` blocks and
  the mobile menu; they are already wired in the template.

## Embedding images

To keep the file portable, convert any local image to a data URI instead of
linking a relative path:

```bash
python3 -c "import base64; print('data:image/png;base64,'+base64.b64encode(open('logo.png','rb').read()).decode())"
```

Put the result in `src="..."`. (This is how the reference file embeds the
Amer Security Architects logo.)

## Quality checklist

- [ ] Single self-contained `.html` (inline CSS/JS, CDN libs, base64 images)
- [ ] `:root` tokens unchanged; no off-palette colors
- [ ] `#particles-js` + particles.js init present and unmodified
- [ ] Nav + mobile menu anchors point to real section `id`s
- [ ] Sections alternate light/gray/featured and use icon + title + lede
- [ ] Buttons/cards use the template's stacked-shadow + hover/active lift
- [ ] Responsive media queries retained
- [ ] Opens with no console errors and no broken image links
