# Services Page — Build Plan (`services.html`)

**Trademarks with Chelsea · Task 3.2 · 10 blocks**

Goal: build `/services` as a standalone single-file page that is **visually indistinguishable in system** from the approved homepage (`index.html`). Same tokens, same fonts, same nav, same footer, same motion, same button styles. New page-specific components (pricing cards, stat band, mid-CTA) are built *from the homepage's existing values* so nothing looks bolted on.

> **Source of truth:** `index.html` (the approved homepage). When this plan says "match X," copy the exact CSS values from that file. Do not invent new colors, radii, or type scales.

---

## 0. Global setup — reuse from `index.html` exactly

Build `services.html` as one file, no framework, no build step, all CSS inline in a single `<style>` block. Copy these wholesale from the homepage and change nothing:

- **`:root` token block** — `--cream-1 #FFFEF2`, `--cream-2 #F6F5E8`, `--ink #252525`, `--clay #A76C4E`, `--oxblood #643335`, `--oxblood-deep #4E2728`, `--hairline`, `--hairline-light`, `--display`, `--body`.
- **Fonts** — same Google Fonts `<link>` (Bricolage Grotesque 300/500/700/800 + Inter 400/500/600).
- **Base resets, `body`, `::selection`, film grain (`body::after`), `.wrap`** (`max-width:1280px; padding:0 clamp(20px,4vw,56px)`).
- **`section`** padding `clamp(88px,11vw,150px) 0`.
- **`.btn` / `.btn.small` / `.btn.ghost`** — clay pill, cream text, hover-invert, `:active{transform:scale(.97)}`.
- **`.eyebrow`** — flex, 12px, weight 600, `.32em`, uppercase, **color `var(--oxblood)`**, `::before` 36×1px clay dash; `.centered` variant. (This already reflects the eyebrow contrast fix — keep it oxblood.)
- **`.reveal` + the IntersectionObserver script** at the bottom of `<body>` (threshold `0.12`), and the `prefers-reduced-motion` rule.
- **Footer** — copy the entire `<footer>` verbatim (wordmark, links, the legal/licensing line, copyright). It must be identical to the homepage footer so it reads as the same global asset.

### Canonical H2 (use everywhere on this page)
```
font-family: var(--display);
font-weight: 700;
font-size: clamp(34px, 4vw, 56px);
letter-spacing: -0.03em;
line-height: 1.05;
```
Per-section H2s may keep an `em` accent (`font-style:normal; color:var(--clay)` or `var(--oxblood)`) but **must not change the size**. Consistent H2 size is a hard SEO requirement (Task 4.3).

### Canonical H3
```
font-family: var(--display);
font-weight: 700;
font-size: clamp(23px, 2.4vw, 32px);
letter-spacing: -0.02em;
```

---

## 1. Nav — same bar, real site links, **with working hamburger**

Reuse the homepage nav visual exactly (fixed, `backdrop-filter:blur(12px)`, hairline bottom, wordmark left). Two differences:

1. **Links are site-level, not on-page anchors:**
   `Home → /` · `Services → /services` (mark active) · `Speaking → /speaking` · `Podcast → /podcast` · `Blog → /blog` · **Book a Free Consultation** (clay `.btn.small` → `/consultation`).
   Active state for Services: `opacity:1` and a 1px clay bottom-border on the link.
2. **Add a hamburger** for `≤820px` (the homepage is missing this — Task 2.4/6.1 — so build it correctly here and back-port to home). Minimal + accessible:
   - A `<button class="nav-toggle" aria-label="Menu" aria-expanded="false">` with three 1px `var(--ink)` bars.
   - Hidden `>820px`; shown `≤820px`, where `.nav-links` collapses into a dropdown panel: full-width, `background:var(--cream-1)`, `border-bottom:1px solid var(--hairline)`, links stacked, 18px, uppercase, generous tap targets.
   - JS toggles an `.open` class + flips `aria-expanded`; close on link click and on `Escape`. No library.

---

## 2. Section background rhythm (lock this order)

Alternate cream tones with a **single dark moment** (the stat) so the page has rhythm without feeling striped:

| Block | Section | Background |
|---|---|---|
| 1 | Hero | `--cream-1` + grain |
| 2 | The Process | `--cream-2` (self-contained block already uses `#F6F5E8`) |
| 3 | Statistic | **`--oxblood`** (the page's dark moment) |
| 4 | Why Choose Chelsea | `--cream-1` |
| 5 | Mid-CTA | `--cream-2` strip |
| 6 | Search Services | `--cream-1` |
| 7 | Application Services | `--cream-2` |
| 8 | Mid-CTA | `--cream-1` strip |
| 9 | Registration & Maintenance | `--cream-1` (quiet) |
| 10 | Final CTA | `--cream-2` |
| — | Footer | `--ink` |

---

## Block-by-block

### BLOCK 1 — HERO  *(reuse homepage hero pattern)*
Copy the homepage `.hero` structure: `min-height:100dvh`, centered, `.hero-grain` layer, `.hero-kicker` + `.hero-display` + `.hero-sub`.

- **H1 = the SEO kicker line** (small, uppercase, oxblood — same as home): `Trademark Attorney | USPTO Search, Application & Registration Services`
- **Display line = styled `<p class="hero-display">`** (Bricolage 800, `clamp(44px,6.8vw,92px)`, `-0.035em`, line `.98`): `Clarity, from search to registration.`
  - Echo the home hero: wrap **registration** in the `.lowlight` clay band so the two hero pages rhyme visually.
- **Body (`.hero-sub p`, verbatim):**
  > I'm a federal trademark attorney—meaning this practice is 100% USPTO trademark work, not an after-thought service tacked onto a general law firm. And not an online service marking up processing forms you fill out yourself. Every flat-fee service below is priced clearly upfront, and every step comes with the kind of guidance a DIY filing service simply can't offer.
- **CTA:** one primary `.btn` → `/consultation`, label **Book a Free Trademark Strategy Consultation**. (Optional secondary `.btn.ghost` "See the process" → `#process`.)

> **Note (intentional):** like the homepage, the big line is a `<p>`, not an `<h2>`, so the page keeps exactly one H1 and no competing hero heading. This deliberately deviates from the copy doc labeling it "H2."

---

### BLOCK 2 — THE PROCESS  *(reuse the self-contained process block)*
Copy the **entire** `PROCESS / SCROLL PATH — SELF-CONTAINED BLOCK` from `index.html` (its own `<style>`, markup, and `<script>`) so the scroll-drawn line, dots, and alternating cards are byte-identical. Then:

1. **Give it a unique id** (`id="process"`) and make sure its internal script selectors still resolve within the block.
2. **Add an eyebrow** above the heading: `THE TRADEMARK PROCESS` (use `.eyebrow`, centered variant to sit above the centered head).
3. **Change the head:** H2 → `One process, five stages, one attorney the whole way through`. Keep the intro `<p>` slot but replace with a one-line lead if desired (optional; can omit since the eyebrow + H2 carry it).
4. **Replace the 5 step cards** with the Services copy (H3 + body verbatim):
   - **01 Strategy Consultation** — We start by talking through what you're building and what's actually worth protecting, before we move into paid work together.
   - **02 Trademark Search** — Before you file anything, a clearance search confirms the path is open — so you're not building a brand around a name you can't keep.
   - **03 Application** — I draft and file the application, then monitor it through the USPTO process, handling routine correspondence as it comes in.
   - **04 Registration** — Once the USPTO approves your mark, it's officially registered — but the work of protecting it doesn't stop there.
   - **05 Maintenance** — A trademark registration has to stay active to stay protected. I track your filing deadlines and handle what's required, so it never lapses on your watch.

Keep the alternating `data-side="left/right"` order. **Do not** add the "See the full breakdown of services →" text link here (that link belongs on the homepage pointing *to* this page).

---

### BLOCK 3 — STATISTIC  *(new component, built on the homepage `.band` aesthetic)*
A slim **oxblood** band — the one dark moment on the page. Reuse the band's feel (oxblood bg, cream text, `overflow:hidden`, a faint radial glow like `.band::before`). Optional: reuse the concentric ripple SVG from the homepage band at low opacity for continuity.

- Slightly slimmer than a full section: `padding: clamp(64px,8vw,110px) 0`.
- **Comparison layout** — two figures with a hairline divider between:
  - `82%` — Bricolage 700, `clamp(56px,8vw,120px)`, cream. Label under it (Inter, uppercase, `.14em`, cream `.75`): `with an attorney`.
  - `60%` — same size but `opacity:.55` (echoes `.band h2 em`). Label: `without one`.
- **Caption sentence** (Inter, cream `.82`, `max-width:52ch`): *82% of attorney-filed trademark applications receive preliminary USPTO approval. Without an attorney, that drops to 60%.*
- **Citation** (12.5px, cream `.5`): *Gerhardt & McClanahan, "Do Trademark Lawyers Matter?" — UNC School of Law*
- No heading tag needed here (keeps the single-H1 rule clean); the figures are display numerals, the caption is a `<p>`.

---

### BLOCK 4 — WHY CHOOSE CHELSEA  *(editorial two-column, reuse `.about-grid` proportions)*
Reuse the homepage `about-grid` proportions (`grid-template-columns:5fr 7fr; gap:clamp(40px,6vw,96px)`, stack at `≤820px`).

- **Left column:** eyebrow `EXPERT GUIDANCE ALONG THE WAY` + H2 `Why Choose Chelsea as Your Trademark Attorney`. (Optional `position:sticky; top:120px` on desktop for an elevated feel.)
- **Right column:** the body, broken into short paragraphs with the key phrases bolded (`<strong>`, weight 600, `var(--ink)`), using the same measured body style as `.about-copy p`:
  > Online filing services are built around one assumption: that you already know exactly what to file, and how to file it correctly. **Most business owners don't** — and the cost of getting it wrong isn't just losing the filing fee, it's the time and money spent rebuilding a weak application later.
  >
  > I bring **a decade of trademark law experience** to every search and every application, which means catching the things a fill-in-the-blank form can't: a conflict that isn't obvious on the surface, a class of goods that doesn't quite match how you actually do business, language in your application that could create problems down the line.
  >
  > **When you hire me, you work with me.** There's no paralegal handling your file behind the scenes or an associate you get passed off to — one attorney, on every step, from search to registration.
  >
  > It's also why this practice works the way it does: forms and payments through a secure client portal, tasks assigned to you on your own schedule, no long phone calls in the middle of your workday.
  >
  > **Efficient support, without losing the part that actually matters:** someone paying close attention to your application.

---

### BLOCK 5 — MID-CTA  *(new reusable component — quiet, not the final CTA)*
A slim centered strip on `--cream-2` with hairline top/bottom. Deliberately lighter than Block 10 (no eyebrow, no giant H2, no closing note):

- Layout: centered, `padding:clamp(56px,7vw,90px) 0`.
- A single **bold line** (Inter 600, `clamp(19px,2vw,24px)`, ink): `Ready to talk through your situation with Chelsea?`
- One primary `.btn` → `/consultation`: **Book a Free Trademark Strategy Consultation**.

Build this as a class (e.g. `.midcta`) and reuse it for Block 8.

---

### BLOCK 6 — SEARCH SERVICES  *(new pricing-card component)*
Eyebrow `FEEL CONFIDENT IN WHAT YOU CAN PROTECT` + H2 `Trademark Search Services` + intro `<p>`:
> Before you invest in a name or logo — signage, packaging, a website, a launch — it's worth knowing whether you can actually own and protect it. I offer two levels of search, depending on how much certainty you need.

**Pricing card system (define once, reuse in Block 7):**
- 2-col grid, `gap:clamp(24px,3vw,40px)`, stack `≤768px`.
- Card: `background:var(--cream-2)` on cream-1 sections / `background:var(--cream-1)` on cream-2 sections (so cards always contrast their section), `border:1px solid var(--hairline)`, `border-radius:18px` (matches `.tcard`), `padding:clamp(28px,3vw,40px)`.
- **Tier label:** Inter 600, uppercase, `.16em`, `var(--oxblood)`, 12.5px.
- **Price:** Bricolage 700, `clamp(34px,3.4vw,48px)`, `var(--oxblood)` (matches the homepage `.strip .num`).
- **Description:** Inter 15.5px, ink `.82`.
- Highlight the deeper tier (Tier 2) with a `1px solid var(--oxblood)` border + a small pill tag `DEEPER CERTAINTY` (clay bg, cream text, Inter 600 11px) top-right.

Cards (verbatim):
- **Tier 1 — Knockout Search · $350** — A thorough search of USPTO records using GleanMark software that catches all versions and iterations of potential conflicts.
- **Tier 2 — Clearance Report + Call · $600** *(highlighted)* — A full clearance report (of USPTO records **and** public records), plus a recap call to walk through what it means for your brand.

**Note below cards** (italic, ink `.62`, 14px):
> *Looking at more than one name or logo design, or considering filing for multiple marks at once? I offer discounts for searches and applications handled together — we can talk through what discounts would be available to you during your consultation.*

---

### BLOCK 7 — APPLICATION SERVICES  *(reuse the pricing-card system)*
On `--cream-2`. Eyebrow `FILING, DONE RIGHT THE FIRST TIME` + H2 `Trademark Application Services` + intro:
> Once your search confirms the path is clear, I draft and file your application — then monitor it through the process, handling routine USPTO correspondence along the way.

Two cards (cards here use `background:var(--cream-1)` to contrast the cream-2 section):
- **One Mark, One Class · $1,850 total** — small subline: *($1,500 legal fee + $350 current USPTO fee)*. Then an **Includes** list using clay-dot bullets (reuse `.about-paths` dot: 7px clay circle):
  - Application drafting and filing
  - Monitoring through the USPTO process
  - Routine correspondence, including non-substantive Office Action responses (minor formalities, examiner's amendments)
- **Additional Class, Same Mark · $750 total** — subline: *($400 legal fee + $350 current USPTO fee)*.

**Note below cards** (italic, ink `.62`, 14px):
> *Substantive Office Action responses (such as a likelihood-of-confusion refusal) aren't included in the flat fees above — they're quoted separately based on what the specific refusal requires. We can talk through what to expect during your consultation.*

Verify pricing strings exactly: **$350, $600, $1,850, $750, $1,500, $350, $400, $350** (Task 6.3).

---

### BLOCK 8 — MID-CTA  *(reuse `.midcta` from Block 5)*
On `--cream-1`. Same component, same line and button.

---

### BLOCK 9 — REGISTRATION & MAINTENANCE  *(intentionally quiet, text-only)*
On `--cream-1`. **No cards, no pricing table** — keep it visually calmer than the blocks above (this is reassurance, not a transaction). Narrow measure (`max-width:64ch`).

- Eyebrow `PROTECTED DOESN'T MEAN DONE` + H2 `Trademark Registration & Maintenance Services`.
- Body (verbatim, standard `.about-copy p` style):
  > Once your mark is registered, it has to stay that way. The USPTO requires a handful of filings over the life of a registration — proof of continued use, periodic renewals — to keep it active. These are billed individually as they come due, priced as legal fee plus the current USPTO fee, with no markup.
  >
  > You won't need to track any of this yourself. I monitor your filing deadlines and reach out when something's due, well before it becomes urgent.
  >
  > You may also have practical questions along the way — how to display the correct symbol on your website, or how to prepare a statement of use. You can book me for a one-off strategy call for practical advice on how to use and protect your marks in your business.

---

### BLOCK 10 — FINAL CTA  *(reuse homepage `.cta` block verbatim, swap copy)*
Copy the homepage `.cta` section (cream-2, centered, `border-top:1px solid var(--hairline)`) so the site's closing moment is identical page to page.

- Eyebrow (`.eyebrow.centered`): `THE NEXT STEP IS A CONVERSATION` *(reused label for cross-page consistency — see flags)*.
- **H2:** `Let's figure out what your brand ` + `<em>` (clay) `actually` + ` needs` → renders *"Let's figure out what your brand actually needs"* with **actually** in clay, matching the homepage `em` treatment.
- **Body:** Every business is different, and so is every trademark strategy. The best way to know what yours should look like is a conversation — not a guess from a pricing page.
- **CTA:** primary `.btn` → `/consultation`: **Book a Free Trademark Strategy Consultation**.
- **Closing note** (`.cta-note`): `Trademark clarity for business owners who build for the long game`.

---

## SEO & accessibility checklist (verify before done)
- [ ] Exactly **one `<h1>`** (the hero kicker). Everything else is H2/H3 or non-heading.
- [ ] All `<h2>` render at the **same** canonical size; no per-section size overrides.
- [ ] All `<h3>` share the canonical H3 size + weight 700.
- [ ] Eyebrows are `<p class="eyebrow">`, **oxblood**, never a heading tag.
- [ ] `<title>` = `Trademark Attorney | USPTO Search, Application & Registration` · meta description = *Trademark attorney for business owners in the USPTO search, application, and registration process. Offering flat fee billing and practical guidance.*
- [ ] Every primary CTA → `/consultation`; nav → `/ , /services , /speaking , /podcast , /blog`.
- [ ] Hamburger works `≤820px`; `aria-expanded` toggles; closes on link + Escape.
- [ ] `prefers-reduced-motion`: reveals show instantly, grain freezes, process line renders fully drawn.
- [ ] Footer identical to homepage (global-asset parity).
- [ ] Pricing strings exact: $350 / $600 / $1,850 / $750 / $1,500 / $400 / $350.

---

## Flag to Chelsea before locking (don't silently "fix" client copy)
1. **H2 casing.** The copy doc writes several Services H2s in Title Case ("Why Choose Chelsea…", "Trademark Search Services", "Trademark Application Services", "Trademark Registration & Maintenance Services"), but the SEO rule says H2s should be **sentence case**. These are keyword/service-name headings, so it's a real judgment call — build them as written, but confirm whether she wants sentence case for the rule or Title Case for the service names.
2. **Button label.** Copy doc uses the full "Book a Free Trademark Strategy Consultation"; the homepage nav shortens it to "Book a Free Consultation." Plan keeps nav short + in-body full. Confirm she's fine with the two-length approach or wants one label everywhere.
3. **Final-CTA eyebrow** ("THE NEXT STEP IS A CONVERSATION") is reused from the homepage for consistency; it's not in the Services copy. Keep for parity or drop — her call.
