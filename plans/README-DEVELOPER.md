# Trademarks with Chelsea — Homepage (Version A, approved)

Live reference: https://trademarks-with-chelsea-draft.netlify.app

## What's in this package
- `index.html` — the entire page. No build step, no framework, no dependencies. All CSS and JS is inline.
- `images/` — Chelsea's two photos (SEO-named; keep the filenames, they match the alt text).

Open `index.html` in a browser and it just works. Google Fonts (Bricolage Grotesque + Inter) load from a `<link>` in the `<head>`.

## Brand tokens
All colors live in one `:root` block at the top of the stylesheet:

| Token | Hex | Role |
|---|---|---|
| `--cream-1` | `#FFFEF2` | page background |
| `--cream-2` | `#F6F5E8` | alternate sections, panels |
| `--ink` | `#252525` | text, footer background |
| `--clay` | `#A76C4E` | buttons, small UI, highlights |
| `--oxblood` | `#643335` | dark band, headline accents |

Fonts: Bricolage Grotesque (headings, 700–800; large numerals 300) + Inter (body/UI, 400–600).

## Page structure (top to bottom)
1. Fixed nav (backdrop blur)
2. Hero — full viewport, centered; animated grain layer (`.hero-grain`); clay "lowlight" band behind the word Protected (`.lowlight`)
3. Stat strip — 3 cells on cream-2
4. Meet Chelsea — arched portrait + bio
5. Who I Work With — oxblood band, decorative ripple SVG, 3 numbered rows
6. **My Process — SELF-CONTAINED BLOCK** (see below)
7. Testimonials — two white cards with tilted color backings
8. Final CTA — cream-2, centered
9. Footer — ink, includes the required legal/licensing line

## The process section (important)
The "One continuous path" section is deliberately self-contained for GoHighLevel:
everything between the comments

    <!-- PROCESS / SCROLL PATH — SELF-CONTAINED BLOCK -->  ...  <!-- END PROCESS BLOCK -->

carries its own `<style>` and `<script>` and can be pasted as-is into a GHL custom
code element. The script draws the vertical line with scroll (stroke-dashoffset),
lights the dots, and positions everything from measured layout, so copy changes
won't break alignment. It rebuilds on resize and after fonts load.

## Animations
- Scroll reveals: IntersectionObserver adds `.in` to `.reveal` elements (script at the bottom of `<body>`).
- Hero grain: CSS keyframes jitter loop.
- Process line: scroll-driven, rAF-throttled, passive listener.
- All motion honors `prefers-reduced-motion: reduce` (reveals show instantly, grain freezes, process line renders fully drawn).

## Accessibility / conventions
- Body text is ink on cream (≈13.9:1). Clay is never used for small text (contrast); it's buttons (with cream text, 600 weight) and decoration only.
- The H1 is the SEO kicker line ("US Trademark Attorney...") per the client's SEO doc; the big display line is a styled `<p>`.
- Buttons use `transform: scale(.97)` on `:active`; transitions are transform/opacity only.

## GHL rebuild notes
- Section padding: `clamp(88px, 11vw, 150px)`; hairlines: 1px `rgba(37,37,37,.14)`.
- Hero display type: `clamp(44px, 6.8vw, 92px)`, tracking `-0.035em`, weight 800, explicit `<br>` before "Protected".
- Buttons: 100px-radius pills, clay bg, cream text, 14–15px/600.
- The footer must be built as a universal/global GHL asset (client requirement) so one edit updates all pages.
- If GHL strips the reveal script, the page degrades gracefully: set `.reveal{opacity:1;transform:none}` and everything is visible.

## Placeholder links (to wire up)
- All "Book a Free Consultation" buttons → booking/calendar URL
- "See the full breakdown of services" → services page
- Footer: Home / Services / Speaking / Podcast / Blog / Privacy / Terms / Disclaimer
