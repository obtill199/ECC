---
name: taste
description: Anti-slop visual taste for pages people look at. Activate for landing pages, redesigns, hero/layout/typography/motion polish, "make it not look AI", or when the user says use taste. Not for spreadsheets, resumes, or sports notes.
---

# Taste

Adapted for Tilly Lite from [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) (`design-taste-frontend`, MIT, Copyright 2026 Leonxlnx). Full upstream is ~87KB of extra skeletons; this file is the part Claude should run so sessions stay cheap.

Use when a person will *look at* the result: `chad-chimney` pages, marketing HTML, `speaker_aggregator` UI chrome. Do not use for fantasy notes, resumes, or collector bugfixes unless the user asked for a visual pass.

## 1. Read the room first

Before code, write one line:

> Reading this as: \<page kind> for \<audience>, \<vibe>, leaning \<system or family>.

Signals: page kind, vibe words, references, audience, existing brand assets, quiet constraints (trust, accessibility, trades, public-sector).

If the brief splits two directions, ask **one** question. Otherwise declare the read and go.

For Tilly defaults when the brief is thin:

- `chad-chimney` / local trades: trust-first service site for Wichita homeowners. Warm, plain, phone-obvious. Not Awwwards, not purple SaaS.
- `speaker_aggregator`: listings product UI. Clear hierarchy, dense-enough results, no cinematic hero theater on a data page.

## 2. Anti-defaults

Do not ship the LLM starter kit unless the brief actually asks for it:

- purple/indigo gradients and dark mesh heroes
- Inter + slate-900 as the whole identity
- three equal feature cards as the only layout
- glassmorphism on every panel
- centered hero with a fake dashboard screenshot
- section labels like `01 — SERVICES`
- em dashes as a style tic

Reach past those on purpose.

## 3. Three dials

Set these once, then keep them consistent.

| Dial | Low | Mid | High |
| --- | --- | --- | --- |
| VARIANCE | one typeface, tight palette, repeating layout | one display + one body, 1 accent | mixed type, irregular layout |
| MOTION | none / CSS hover only | short fades, sticky header | GSAP, scroll-pin, kinetic type |
| DENSITY | lots of air, few elements | balanced marketing | product/listing density |

Tilly starting points:

- Local service HTML: VARIANCE low-mid, MOTION low, DENSITY mid (CTA must win).
- Listings app chrome: VARIANCE low, MOTION low, DENSITY high.

Do not crank MOTION high on a chimney site.

## 4. Design system

Prefer the files already in the repo (colors, type, spacing in `styles.css` or existing tokens). Do not add Tailwind + shadcn + Framer Motion to a static HTML site to "have taste."

Taste here means hierarchy, type, spacing, and one obvious action — not a new stack.

## 5. Editing grammar

- One job per view: call, book, inspect, or scan listings.
- Biggest type is the thing the audience came for, not the brand slogan.
- Spacing is a scale, not random 13/17/22px.
- Buttons look like buttons. Phone numbers are `tel:` and easy to tap.
- Images crop with intent. No stretched stock.
- Motion supports the read; it does not decorate emptiness.

## 6. Redesign vs tweak

If the site already exists (Chad Chimney):

1. Audit first: what already has taste, what is generic, what is load-bearing.
2. Keep working brand bits unless asked to overhaul.
3. Change the fewest surfaces that raise trust and conversion.

Do not restyle the whole site for a headline request.

## 7. Pre-flight before you call it done

- [ ] Design read stated
- [ ] Dials match the job
- [ ] No LLM-default stack unless intended
- [ ] Mobile: primary CTA reachable without hunting
- [ ] No invented testimonials, badges, or service areas
- [ ] Existing CSS variables/classes reused where they exist
- [ ] Motion off or tiny if the page is a trades site

## 8. How to invoke

User can say:

```text
Use skill taste. Redesign the Chad Chimney homepage hero only. Trust-first, Wichita, phone CTA wins.
```

Or slash command `/lite:taste`.

If taste conflicts with `html-local-service`, conversion and truth win. Taste cannot invent reviews or hide the phone number in a fancy animation.
