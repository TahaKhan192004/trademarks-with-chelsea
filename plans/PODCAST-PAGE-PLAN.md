# Podcast Page — Build Plan (`podcast.html`)

**Trademarks with Chelsea · Task 3.3 · 6 blocks**

Goal: build `/podcast` as a standalone single-file page that matches the approved homepage (`index.html`) and Services page system exactly — same tokens, fonts, nav, footer, motion, buttons. The page has several **placeholder** areas (cover art, player embed, listen-button URLs) that Chelsea fills at launch; build them as clean, sized holders so her drop-in code doesn't break layout.

> **Source of truth:** `index.html`. When this says "reuse X," copy the exact CSS values from that file — no new colors, radii, or type scales. Global setup (tokens, fonts, film grain, `.wrap`, `section` padding, `.btn`/`.btn.small`/`.btn.ghost`, `.eyebrow` in **oxblood** with clay dash, `.reveal` + observer, `prefers-reduced-motion`, the entire `<footer>`) is identical to the Services plan — carry it over unchanged.

### Canonical type (use everywhere)
- **H2:** `var(--display)`, 700, `clamp(34px,4vw,56px)`, `-0.03em`, line `1.05`. Same size on every H2 (Task 4.3). `em` accents may recolor (clay/oxblood) but never resize.
- **H3:** `var(--display)`, 700, `clamp(23px,2.4vw,32px)`, `-0.02em`.

### Nav
Same bar as Services: site-level links `Home / Services / Speaking / Podcast (active) / Blog / Book a Free Consultation`, **with the working hamburger** ≤820px. Mark Podcast active (opacity 1 + 1px clay underline).

### Page `<head>`
- `<title>`: `Trademark Law Basics Business Podcast With Chelsea Fournier`
- meta description: *Business owners don't care about becoming an expert in trademark law, but understanding the basics will help you develop a smart brand protection strategy.*

---

## Section background rhythm (lock this order)

| Block | Section | Background |
|---|---|---|
| 1 | Hero (cover art + player + listen) | `--cream-1` + grain |
| 2 | What You'll Learn | `--cream-2` |
| 3 | Mid-CTA | **`--oxblood`** (the page's one dark moment) |
| 4 | Podcast Host | `--cream-1` |
| 5 | Show Posts (blog feed) | `--cream-2` |
| 6 | Final CTA | `--cream-2` (identical to home; `border-top` hairline separates it) |
| — | Footer | `--ink` |

---

## Block-by-block

### BLOCK 1 — HERO  *(new podcast hero: cover art + text + listen buttons + player embed)*
On `--cream-1` with the reused `.hero-grain` layer. Structure: a **two-column top** (cover art left, text right), then a **full-width player embed** below, all inside one hero section. Not full-viewport like the home hero — size to content with generous top padding to clear the fixed nav (`padding-top: calc(72px + clamp(48px,7vw,90px))`).

**Left column — cover-art placeholder (`.cover-ph`):**
- Square (`aspect-ratio:1/1`), `max-width:360px`, `background:var(--cream-2)`, `border:1px solid var(--hairline)`, `border-radius:16px`, centered placeholder label (Inter, ink `.5`): `Podcast cover art`. Optionally a faint ® or ™ glyph behind the label (brand mood-board nod), Bricolage 300, clay `.12`.
- Comment in code: drops in at launch once logo + cover art are finalized. Image title when ready: `trademark-podcast-for-business-owners-with-chelsea-fournier`.

**Right column — title + intro + listen buttons:**
- **H1 (the page's only H1)** — the podcast title, styled display (`var(--display)`, 800, `clamp(38px,5vw,68px)`, `-0.03em`, line `1.0`): `Trademarks With Chelsea Podcast`
- **H2** at canonical size: `A trademark law podcast for business owners, one question at a time.`
- **Body** (verbatim, standard body style):
  > Trademark law makes a lot more sense when it's connected to real business decisions. Each episode tackles one question — a common trademark question, a legal definition explained in plain terms, or a specific example of how trademark strategy plays out for a real business — so you can see exactly how it applies to what you're building. Clear, practical, trademarks chat in under 12 minutes.
- **Listen buttons (`.listen-btns`)** — a wrap row of three `.btn.ghost` pills, `href="#"` placeholders (URLs pending, Task 5.5): `Listen on Apple` · `Listen on Spotify` · `Listen on YouTube`. Single-color only (ghost outline, ink→clay on hover) — do **not** use multi-color platform logos (off-brand). An optional small `ti-player-play`-style single-color glyph before each label is fine.

**Full-width player embed placeholder (`.embed-ph`):**
- Below the two columns, spanning `.wrap`. Bordered container (`border:1px dashed var(--hairline)`, `border-radius:14px`, `background:var(--cream-2)`), `min-height:180px`, centered label (ink `.5`): `Podcast player embeds here — trailer first, then latest 5 episodes`.
- Comment: Chelsea replaces this container's contents with embed code later; keep the outer wrapper so padding/rhythm hold.

**Responsive:** stack to one column ≤820px (cover art on top, capped width, centered).

---

### BLOCK 2 — WHAT YOU'LL LEARN  *(editorial numbered list — reuse the home "Who I Work With" numeral aesthetic)*
On `--cream-2`. Eyebrow `WHAT YOU'LL LEARN` + H2 `Trademark law, translated for the way you actually run your business`.

- **Intro `<p>`** (verbatim): *Every episode is built around the questions real business owners are actually asking — not the ones a law school textbook would cover. We'll cover questions like:*
- **Question list (`.qlist`)** — 6 rows, editorial style echoing the homepage numbered band: each row = a large **light** Bricolage numeral (`weight 300`, `clamp(22px,2.4vw,32px)`, clay/ink `.5`) + the question text (Inter, `clamp(16px,1.35vw,18px)`, ink `.85`), separated by 1px hairlines (`border-top`, last row `border-bottom`). This uses the brand guide's "hairlines & numerals in place of boxed card grids" language — no bullet boxes.
  - Task 2.8 defines optional custom bullet icons for this section; if/when they're ready they can replace the numerals. Default to numerals now so the page isn't blocked on icon delivery.
  - 01 — What does a trademark actually protect — and what doesn't it cover?
  - 02 — How does the trademark search and application process work, step by step?
  - 03 — Does my type of business actually need a trademark? (Coaches, authors, therapists, speakers, product-based brands, and more)
  - 04 — What are the most common trademark mistakes business owners make — and how do you avoid them?
  - 05 — How does trademark strategy play out in real businesses?
  - 06 — What can I do after my registration goes through to keep protecting my brand properly?
- **Closing `<p>`** (verbatim): *If you've been putting off thinking about trademarks because it felt too complicated or too far down the list — this is where to start.*

---

### BLOCK 3 — MID-CTA  *(oxblood dark variant — the page's single dark moment)*
On `--oxblood`, cream text (reuse the `.band` surface feel; optional faint radial glow / ripple echo like the homepage band). Centered, `padding:clamp(72px,9vw,120px) 0`.

- **H2** (canonical size, cream): `Prefer to talk it through directly?`
- **Body** (Inter, cream `.82`, `max-width:52ch`, centered): *If you already know you need a trademark strategy, you don't have to wait for the right episode to come along.*
- **CTA:** primary `.btn` → `/consultation`: **Book a Free Trademark Strategy Consultation**. (Clay button on oxblood with cream text stays high-contrast — fine.)

Build this as a reusable `.midcta.dark` so it can be reused on other pages.

---

### BLOCK 4 — PODCAST HOST  *(reuse the home "Meet Chelsea" arched-portrait two-column)*
On `--cream-1`. Reuse the `.about-grid` (`5fr 7fr`, stack ≤820px) and the arched `.about-photo` treatment. Put the **photo on the right** this time (mirror of home) for variety; keep the arched frame + thin clay outline.

- **Left column:** eyebrow `YOUR PODCAST HOST` + H2 `Chelsea Fournier, Trademark Attorney` + bio (verbatim, standard `.about-copy p` style):
  > Chelsea is a federal trademark attorney and founder of Trademarks with Chelsea, a boutique law practice focused exclusively on USPTO trademark work for business owners, professional service providers, and thought leaders.
  >
  > She started practicing law in 2008, and spent the years that followed not just inside a law firm — but also inside the entrepreneurial world as a startup team member, business coach, consultant, and marketing agency founder.
  >
  > That crossover is what makes her rare in her field: she understands what it actually costs to build something, which is why she's particular about making sure it's protected correctly.
  >
  > Chelsea lives in North Carolina and is licensed to practice law in Maine. Her practice serves clients nationwide in federal trademark matters before the USPTO.
  >
  > She created this podcast to do what she's always done best: bridge the gap between legal complexity and the real decisions business owners have to make.
- **Right column — arched portrait:**
  - `src`: `images/trademark-law-basics-business-podcast-with-chelsea-fournier.jpg`
  - `alt`: *Chelsea Fournier, US trademark attorney and host of the Trademarks With Chelsea Podcast, in a navy blue short sleeve shirt standing in an office room with lots of windows behind her*
  - Optional figcaption matching home style.
  - (Photo is Chelsea's Google-Drive headshot, run through TinyPNG before adding — Task 2.10 / 4.4.)

---

### BLOCK 5 — SHOW POSTS  *(blog-feed placeholder — quiet cards, becomes a GHL feed)*
On `--cream-2`. Eyebrow `LISTEN IN` + H2 `Start Binge-ing the Show Here` *(see flag on casing)*.

- **Posts grid (`.posts-grid`)** — responsive `repeat(auto-fit,minmax(240px,1fr))`, gap `clamp(20px,2.5vw,32px)`. Show **3 placeholder cards** now (the real feed will populate a 3×3). Quiet, on-brand cards (no drop shadow, consistent with the editorial direction):
  - Card: `background:var(--cream-1)`, `border:1px solid var(--hairline)`, `border-radius:12px`, overflow hidden.
  - Thumbnail area: `aspect-ratio:16/10`, `background:var(--cream-2)`, centered faint label `Episode art`.
  - Body pad: a small eyebrow-style category tag `PODCAST` (Inter 600, `.14em`, oxblood, 11px), then a title placeholder (Bricolage 600, ~18px) `Episode title`, then a text-link `Listen →` (oxblood, clay underline — reuse the process-block text-link style).
- Comment in code: Chelsea sets up the "podcast" blog category + feed in GHL; these three cards are visual placeholders that the GHL blog element replaces.

---

### BLOCK 6 — FINAL CTA  *(reuse the homepage `.cta` block verbatim, swap copy)*
On `--cream-2`, centered, `border-top:1px solid var(--hairline)` — identical component to home/services so the closing moment matches across the site.

- Eyebrow (`.eyebrow.centered`): `THE NEXT STEP IS A CONVERSATION` *(reused label for cross-page parity — optional, see flags)*.
- **H2:** `Ready to stop guessing and start ` + `<em>` (clay) `protecting` + ` what you've built?`
- **Body:** *If something in an episode got you thinking about your own brand, the next step is a conversation — not a search engine.*
- **CTA:** primary `.btn` → `/consultation`: **Book a Free Trademark Strategy Consultation**.
- **Closing note** (`.cta-note`): `Trademark clarity for business owners who build for the long game`.

---

## SEO & accessibility checklist (verify before done)
- [ ] Exactly **one `<h1>`** — the podcast title in the hero. Everything else H2/H3 or non-heading.
- [ ] All `<h2>` render at the same canonical size; `em` accents recolor only.
- [ ] Eyebrows are `<p class="eyebrow">`, **oxblood**, never a heading tag.
- [ ] Listen buttons are single-color ghost pills, `href="#"` (note: wire Apple / Spotify / YouTube URLs — Task 5.5).
- [ ] Cover-art holder and player embed holder are clearly labeled placeholders with stable outer padding.
- [ ] Host photo uses the exact SEO filename + alt text; image run through TinyPNG.
- [ ] Nav → `/ , /services , /speaking , /podcast , /blog`; every primary CTA → `/consultation`.
- [ ] Hamburger works ≤820px; `aria-expanded` toggles; closes on link + Escape.
- [ ] `prefers-reduced-motion`: reveals instant, grain frozen.
- [ ] Footer identical to homepage (global-asset parity).

---

## Flag to Chelsea before locking
1. **Which H1?** The page's SEO/meta field lists the H1 as "Trademarks With Chelsea," but Block 1 writes it as "Trademarks With Chelsea Podcast." Plan uses **"Trademarks With Chelsea Podcast"** (keeps the "podcast" keyword and is clearer as a page title). Confirm.
2. **H2 casing.** "Start Binge-ing the Show Here" is Title Case; the SEO rule says H2s should be sentence case. Kept as written (it's approved copy) — confirm whether to lowercase it ("Start binge-ing the show here").
3. **Pending drop-ins.** Cover art depends on logo approval (Task 1.3); player embed + listen URLs depend on show approval (Task 5.5); blog feed depends on Chelsea's GHL category setup (Task 5.7). All three are built as stable placeholders.
4. **Button label + final-CTA eyebrow.** Same two cross-page consistency calls as the Services plan (nav uses the short "Book a Free Consultation," in-body uses the full label; the reused final-CTA eyebrow is optional).
