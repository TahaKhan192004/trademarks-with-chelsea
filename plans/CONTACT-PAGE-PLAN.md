# Contact Page — Build Plan (`consultation.html`, served at `/consultation`)

**Trademarks with Chelsea · Task 3.4 · 5 blocks**

Goal: build the Contact page as a standalone single-file page matching the approved homepage (`index.html`) and the Services/Podcast system exactly. This page **is** the conversion point (the whole site's "Book a Free Consultation" CTAs point here), so it has no separate final-CTA block — the booking block is the close, and this page's own CTAs scroll to it rather than linking away.

> **Source of truth:** `index.html`. Reuse global setup unchanged: tokens, fonts, film grain, `.wrap`, `section` padding, `.btn`/`.btn.small`/`.btn.ghost`, `.eyebrow` (**oxblood** + clay dash), `.reveal` + observer, `prefers-reduced-motion`, the entire `<footer>`, and the arched-portrait two-column (`.about-grid` / `.about-photo`).

### Canonical type
- **H2:** `var(--display)`, 700, `clamp(34px,4vw,56px)`, `-0.03em`, line `1.05` — same size on every H2 (Task 4.3). `em` accents recolor only.
- **H3:** `var(--display)`, 700, `clamp(23px,2.4vw,32px)`, `-0.02em`.

### Nav
Same bar as the other pages: site-level links `Home / Services / Speaking / Podcast / Blog / Book a Free Consultation`, with the working hamburger ≤820px. **On this page**, both the nav "Book a Free Consultation" button and the hero CTA scroll to the booking block (`href="#book"`, smooth scroll) instead of navigating — this is already `/consultation`. Mark no nav item "active" (Contact isn't in the nav), or optionally highlight none.

### Page `<head>`
- `<title>`: `Find a Flat Fee Trademark Attorney for Business Owners`
- meta description: *Explore whether pursuing trademark protection suits your business goals, stage of business, and brand. Book a free trademark strategy consultation.*

---

## Section background rhythm (lock this order)

| Block | Section | Background |
|---|---|---|
| 1 | Hero | `--cream-1` + grain |
| 2 | What Happens on the Call | **`--oxblood`** (the page's one dark moment) |
| 3 | Booking (scheduler embed) | `--cream-1` |
| 4 | After You Book | `--cream-2` |
| 5 | FAQs (accordion) | `--cream-1` |
| — | Footer | `--ink` |

---

## Block-by-block

### BLOCK 1 — HERO  *(reuse the home/services hero pattern)*
On `--cream-1` with the reused `.hero-grain` layer. Sized to content (not full-viewport), generous top padding to clear the fixed nav. Follow the home pattern: **kicker H1 + big display `<p>`** so the page keeps exactly one H1 and no competing hero heading.

- **H1 = SEO kicker line** (small, uppercase, oxblood): `Contact Chelsea, a Flat Fee Trademark Attorney for Business Owners`
- **Display line = `<p class="hero-display">`** (Bricolage 800, `clamp(40px,5.6vw,78px)`, `-0.03em`): `Let's talk about what protecting your brand actually looks like.`
  - Optional `.lowlight` clay band under **protecting** to echo the home hero.
- **Body** (`.hero-sub p`, verbatim): *This is a free, 30-minute strategy consultation — not a sales call. We'll talk through your business, what you're hoping to protect, and whether trademark registration makes sense for where you are right now. No pressure, no obligation.*
- **CTA:** one primary `.btn` → `#book` (smooth-scroll to Block 3): **Find a Time on My Calendar**.

---

### BLOCK 2 — WHAT HAPPENS ON THE CALL  *(oxblood band — the page's dark moment)*
On `--oxblood`, cream text (reuse the `.band` surface; optional faint radial glow / ripple echo). Centered or left, `max-width:760px`.

- **H2** (canonical size, cream; optional `em` in clay on a word): `What to expect during a Trademark Strategy Consultation`
- **Body** (Inter, cream `.85`), verbatim as two short paragraphs:
  > In our 30 minutes together, we'll talk through what you're building, what you're trying to protect, and what your options actually are. I'll ask questions to understand your business and what aspects of intellectual property are at play in your brand and work.
  >
  > You can ask anything you want about the process of pursuing trademark registration, the cost, or the timeline. By the end of the call, you'll know whether trademark registration is the right next step — and what it would look like to move forward together.

---

### BLOCK 3 — BOOKING  *(scheduler embed placeholder + email fallback)*
On `--cream-1`. Give the section `id="book"` (hero + nav scroll targets land here).

- **H2:** `Book Your Consultation` (centered).
- **Scheduler embed placeholder (`.embed-ph`)** — reuse the podcast plan's holder: bordered container (`border:1px dashed var(--hairline)`, `border-radius:14px`, `background:var(--cream-2)`), `min-height:520px` (calendars are tall), centered label (ink `.5`): `Google Appointments scheduler embeds here`. Comment: Chelsea creates the event type and pastes embed code (Task 5.3); keep the outer wrapper so padding holds.
- **Email fallback** (centered, below the embed, Inter, ink `.7`): *Don't see a time that works for you? Email me directly at* `chelsea@trademarkswithchelsea.com` *and we'll find a time / way to connect.* — wrap the address in a `mailto:` link styled like the process-block text link (oxblood, clay underline).

---

### BLOCK 4 — WHAT HAPPENS AFTER YOU BOOK  *(reuse the arched-portrait two-column)*
On `--cream-2`. Reuse `.about-grid` (`5fr 7fr`, stack ≤820px) with the arched `.about-photo` + thin clay outline. Photo can sit left (like home) — pick whichever balances the page; keep the arched frame.

- **Text column:** eyebrow `AFTER YOU BOOK` + H2 `One quick step before we talk` + body (verbatim):
  > Once you've booked your time, you'll receive a short, secure intake form to complete beforehand. It helps me understand your business and check for any conflicts of interest, so our call can go straight to what matters — your trademark strategy.
- **Photo column — arched portrait:**
  - `src`: `images/find-a-flat-fee-trademark-attorney-for-business-owners.jpg`
  - `alt`: *Chelsea Fournier, a flat fee trademark attorney for business owners, wearing a rose pink shirt and standing in front of a rock wall and hydrangea bush*
  - (Chelsea's Google-Drive headshot, run through TinyPNG first — Task 2.10 / 4.4.)

---

### BLOCK 5 — FAQs  *(new accordion component — accessible)*
On `--cream-1`. `max-width:820px`, centered head.

- **H2** (centered): `Common questions before you hire Trademarks With Chelsea`.
- **Accordion (`.faq`)** — use native `<details><summary>` for each item (keyboard-accessible, works with JS stripped):
  - `.faq details`: `border-top:1px solid var(--hairline)`; last item adds `border-bottom`. No boxes/shadows — editorial hairline style.
  - `.faq summary`: `list-style:none` (hide default marker), `cursor:pointer`, `padding:22px 0`, flex row with the question (Bricolage 600, `clamp(17px,1.5vw,20px)`, oxblood) on the left and a `+` / `–` indicator (clay, rotates on open) on the right. Focus-visible ring for a11y.
  - `.faq details[open] summary` swaps the indicator; answer (`.faq-a p`) is Inter, ink `.82`, `padding-bottom:24px`, `max-width:64ch`.
  - Honor `prefers-reduced-motion` (no height animation needed; native toggle is fine).
- **Five items — questions verbatim as `<summary>`, answers verbatim in `.faq-a`.** These answers contain legally precise language (attorney-client relationship, engagement letter, scope of practice) — **do not reword, condense, or paraphrase any of it** (Task 6.3):
  1. **Is this consultation really free?** — Yes. There's no charge for our 30-minute strategy consultation, and no obligation to move forward afterward.
  2. **Am I your client once I book this call?** — Not yet. Booking a consultation doesn't create an attorney-client relationship. During our call, we'll discuss whether engaging me as your trademark attorney is the right fit. If it is, I'll send an engagement letter outlining the scope of work and flat fees to be paid to begin our work together. Until that engagement is in place, please don't share confidential information with me.
  3. **Do you handle state trademarks, licensing agreements, contracts, or trademark disputes?** — No. My practice is exclusively transactional federal trademark work before the USPTO — searches, applications, registrations, and maintenance. I don't handle state-level trademark filings, licensing agreements, contract drafting, or litigation/disputes. If your situation falls into one of these categories, this consultation likely isn't the right fit.
  4. **What if I'm not ready to file yet?** — That's a fine place to start. This call is a good opportunity to talk through timing and budget, so you know what to expect and can move forward when you're ready.
  5. **Can you help me if I live in [your state]?** — Yes. Trademark law is federal law, which means it works a little differently than most legal services. I'm licensed by the State of Maine, and that license allows me to represent clients before the USPTO nationwide — in all 50 states — for federal trademark matters.

---

## SEO & accessibility checklist (verify before done)
- [ ] Exactly **one `<h1>`** (the hero kicker). Everything else H2/H3 or non-heading.
- [ ] All `<h2>` render at the same canonical size; `em` accents recolor only.
- [ ] Eyebrow is `<p class="eyebrow">`, **oxblood**, never a heading tag.
- [ ] Hero CTA + nav Book button scroll to `#book` (this is `/consultation`); nav links → `/ , /services , /speaking , /podcast , /blog`.
- [ ] Scheduler holder is a clearly labeled placeholder with stable padding; email is a working `mailto:`.
- [ ] After-You-Book photo uses exact SEO filename + alt; run through TinyPNG.
- [ ] FAQ is native `<details>`/`<summary>`: keyboard-operable, works with JS stripped, focus-visible ring.
- [ ] FAQ answer copy is **verbatim** — legal language unchanged.
- [ ] Hamburger works ≤820px; `aria-expanded` toggles; closes on link + Escape.
- [ ] `prefers-reduced-motion`: reveals instant, grain frozen.
- [ ] Footer identical to homepage (global-asset parity).

---

## Flag to Chelsea before locking
1. **H1 wording.** The SEO/meta field lists the H1 as "Find a Flat Fee Trademark Attorney for Business Owners," but Block 1 writes it as "Contact Chelsea, a Flat Fee Trademark Attorney for Business Owners." Plan uses the **Block 1** version (more natural as an on-page headline); the shorter meta-field version stays in the `<title>`. Confirm.
2. **"[your state]" placeholder.** FAQ 5's question reads literally "Can you help me if I live in [your state]?" — kept verbatim, but confirm whether she wants it left as a rhetorical placeholder or changed (e.g., "…if I live in a different state?").
3. **No final-CTA block by design.** Unlike Home/Services/Podcast, this page ends on FAQs — the booking block is the conversion. Confirm she's fine ending there (an optional slim closing line could be added if she wants the site's "…build for the long game" tagline to appear here too).
4. **Button label + scroll behavior.** Nav uses the short "Book a Free Consultation"; on this page it scrolls to `#book` rather than linking. Confirm the two-length label approach (short in nav, full "Book a Free Trademark Strategy Consultation" elsewhere).
