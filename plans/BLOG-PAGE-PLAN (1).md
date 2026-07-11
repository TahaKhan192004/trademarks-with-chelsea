# Blog Page — Build Plan (`blog.html`, served at `/blog`)

**Trademarks with Chelsea · Task 3.6 · 3 blocks**

Goal: build the Blog page as a standalone single-file page matching the approved homepage (`index.html`) and the rest of the site system exactly. This is a light utility page — a hero, a post feed (which Chelsea populates in GHL), and the shared closing CTA. Almost everything here is reused; the only page-specific piece is the placeholder feed grid, which is the same component as the Podcast "Show Posts" block.

> **Source of truth:** `index.html`. Reuse global setup unchanged: tokens, fonts, film grain, `.wrap`, `section` padding, `.btn`, `.eyebrow` (**oxblood** + clay dash), `.reveal` + observer, `prefers-reduced-motion`, the entire `<footer>`, and the `.cta` closing block.

### Canonical type
- **H2:** `var(--display)`, 700, `clamp(34px,4vw,56px)`, `-0.03em`, line `1.05` (Task 4.3).
- **H3:** `var(--display)`, 700, `clamp(23px,2.4vw,32px)`, `-0.02em`.

### Nav
Same bar: site-level links `Home / Services / Speaking / Podcast / Blog (active) / Book a Free Consultation`, with the working hamburger ≤820px. Mark Blog active (opacity 1 + 1px clay underline).

### Page `<head>`
- `<title>`: `Trademark Law Blog | Legal Basics for Business Owners`
- meta description: *Get basic business trademark questions answered by an attorney (and entrepreneur). Understand the benefits, cost & process of trademark registration in the US.*

---

## Section background rhythm

| Block | Section | Background |
|---|---|---|
| 1 | Hero | `--cream-1` + grain |
| 2 | Posts Feed | `--cream-1` (cards use `--cream-2` to contrast) |
| 3 | Final CTA | `--cream-2` (identical to home; `border-top` hairline separates it) |
| — | Footer | `--ink` |

*(No oxblood dark moment on this page by design — it's a short feed page. Kept light and fast.)*

---

## Block-by-block

### BLOCK 1 — HERO  *(reuse the home/services hero pattern)*
On `--cream-1` with the reused `.hero-grain` layer, sized to content, top padding clears the fixed nav. Follow the home pattern: **kicker H1 + big display `<p>`** (one H1, no competing hero heading). No CTA button in this hero (the copy doesn't specify one; the feed below is the point).

- **H1 = SEO kicker line** (small, uppercase, oxblood): `Trademark Law Blog | Legal Basics for Business Owners`
- **Display line = `<p class="hero-display">`** (Bricolage 800, `clamp(42px,5.8vw,80px)`, `-0.03em`): `Trademark law, explained the way business owners actually think about it.`
  - Optional `.lowlight` clay band under **explained** to echo the home hero.
- **Body** (`.hero-sub p`, verbatim):
  > Get straightforward answers to common trademark questions — what registration actually costs, what it protects, and whether it's the right move for where your business is right now. Written by an attorney who's also been the business owner asking these same questions.

---

### BLOCK 2 — POSTS FEED  *(reuse the Podcast "Show Posts" placeholder grid)*
On `--cream-1`. This holds **all** categories (podcast posts + long-form written posts); Chelsea sets up the feed and initial posts in GHL (Task 5.7). Build a clean placeholder grid now.

- Optional light eyebrow at top (`FROM THE BLOG`) — or omit for a heading-light feed (the copy gives no heading here; see flag).
- **Posts grid (`.posts-grid`)** — reuse the podcast component verbatim: responsive `repeat(auto-fit,minmax(240px,1fr))`, gap `clamp(20px,2.5vw,32px)`. Show **3 placeholder cards** now (the GHL feed populates the full 3×3). Quiet, on-brand cards (no drop shadow):
  - Card: `background:var(--cream-2)`, `border:1px solid var(--hairline)`, `border-radius:12px`, overflow hidden.
  - Thumbnail area: `aspect-ratio:16/10`, `background:var(--cream-1)`, centered faint label `Post image`.
  - Body pad: a small category tag (Inter 600, `.14em`, oxblood, 11px) — placeholder `Category` (real feed shows "Podcast," "Article," etc.) — then a title placeholder (Bricolage 600, ~18px) `Post title`, then a text-link `Read →` (oxblood, clay underline — reuse the process-block text-link style).
- Comment in code: Chelsea sets up categories + feed in GHL; these three cards are visual placeholders the GHL blog element replaces. Keep the outer grid wrapper so spacing holds.

---

### BLOCK 3 — FINAL CTA  *(reuse the homepage `.cta` block verbatim, swap copy)*
On `--cream-2`, centered, `border-top:1px solid var(--hairline)` — identical component to the rest of the site so the closing moment matches.

- Eyebrow (`.eyebrow.centered`): `THE NEXT STEP IS A CONVERSATION` *(reused label for cross-page parity — optional, see flags)*.
- **H2:** `Have a trademark question that's ` + `<em>` (clay) `not answered yet?`
- **Body:** *That's exactly what a consultation is for.*
- **CTA:** primary `.btn` → `/consultation`: **Book a Free Trademark Strategy Consultation**.
- **Closing note** (`.cta-note`): `Trademark clarity for business owners who build for the long game`.

---

## SEO & accessibility checklist (verify before done)
- [ ] Exactly **one `<h1>`** (the hero kicker). Everything else H2/H3 or non-heading.
- [ ] All `<h2>` render at the same canonical size; `em` accents recolor only.
- [ ] Any eyebrow is `<p class="eyebrow">`, **oxblood**, never a heading tag.
- [ ] Nav → `/ , /services , /speaking , /podcast , /blog`; CTA → `/consultation`.
- [ ] Posts grid is a clearly labeled placeholder with stable spacing; GHL feed replaces it.
- [ ] Hamburger works ≤820px; `aria-expanded` toggles; closes on link + Escape.
- [ ] `prefers-reduced-motion`: reveals instant, grain frozen.
- [ ] Footer identical to homepage (global-asset parity).

---

## Flag to Chelsea before locking
1. **Posts block has no heading in the copy.** Plan keeps it heading-light (optional `FROM THE BLOG` eyebrow, or nothing). Confirm whether she wants a small label above the feed or a bare grid.
2. **Feed is Chelsea's GHL setup** (Task 5.7) — placeholder cards now, real 3×3 feed later across all categories.
3. **Button label + final-CTA eyebrow.** Same cross-page consistency calls as the other plans (short nav label vs full in-body label; the reused final-CTA eyebrow is optional).
