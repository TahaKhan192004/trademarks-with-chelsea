# Speaker Page — Build Plan (`speaker.html`, served at `/speaking`)

**Trademarks with Chelsea · Task 3.5 · 4 blocks**

Goal: build the Speaker page as a standalone single-file page matching the approved homepage (`index.html`) and the Services/Podcast/Contact system exactly. Like the Contact page, the conversion here is an on-page **inquiry form**, so the hero CTA scrolls to it rather than linking away — this is the documented Speaker-page exception.

> **Source of truth:** `index.html`. Reuse global setup unchanged: tokens, fonts, film grain, `.wrap`, `section` padding, `.btn`/`.btn.small`/`.btn.ghost`, `.eyebrow` (**oxblood** + clay dash), `.reveal` + observer, `prefers-reduced-motion`, the entire `<footer>`, the oxblood numbered `.band`, and the arched-portrait two-column (`.about-grid` / `.about-photo`).

### Canonical type
- **H2:** `var(--display)`, 700, `clamp(34px,4vw,56px)`, `-0.03em`, line `1.05` — same size on every H2 (Task 4.3).
- **H3:** `var(--display)`, 700, `clamp(23px,2.4vw,32px)`, `-0.02em`.

### Nav
Same bar: site-level links `Home / Services / Speaking (active) / Podcast / Blog / Book a Free Consultation`, with the working hamburger ≤820px. Mark Speaking active (opacity 1 + 1px clay underline). The nav "Book a Free Consultation" button still → `/consultation` (that's a different action from the speaker inquiry).

### Page `<head>`
- `<title>`: `Legal Keynote Speaker | Trademark Strategy for Business`
- meta description: *Bring a US trademark attorney into your online or in-person community. Explore how trademark search, application and registration can benefit a business.*

---

## Section background rhythm (lock this order)

| Block | Section | Background |
|---|---|---|
| 1 | Hero | `--cream-1` + grain |
| 2 | Ways We Can Collaborate | **`--oxblood`** (dark moment; numbered band) |
| 3 | Inquiry (form embed) | `--cream-1` |
| 4 | Why Chelsea | `--cream-2` |
| — | Footer | `--ink` |

---

## Block-by-block

### BLOCK 1 — HERO  *(reuse the home/services hero pattern)*
On `--cream-1` with the reused `.hero-grain` layer, sized to content, top padding clears the fixed nav. Follow the home pattern: **kicker H1 + big display `<p>`** (one H1, no competing hero heading).

- **H1 = SEO kicker line** (small, uppercase, oxblood): `Legal Keynote Speaker | Trademark Strategy for Business`
- **Display line = `<p class="hero-display">`** (Bricolage 800, `clamp(44px,6vw,84px)`, `-0.035em`): `Bring trademark clarity into your community`
  - Optional `.lowlight` clay band under **clarity** to echo the home hero.
- **Body** (`.hero-sub p`): *Chelsea Fournier loves translating trademark law into something a room full of business owners can actually use — whether that's a podcast conversation, a guest expert session inside a mastermind or certification program, or a keynote at your next event.* → **see Flag 1: the second sentence in the copy doc is cut off** and needs Chelsea's completion before this ships.
- **CTA:** one primary `.btn` → `#inquire` (smooth-scroll to Block 3): **Let's Connect**.
  - This is the documented Speaker-page exception: "Let's Connect" scrolls DOWN to the inquiry form on the same page, it does **not** link to `/consultation`.

---

### BLOCK 2 — WAYS WE CAN COLLABORATE  *(reuse the home oxblood numbered band — the page's dark moment)*
On `--oxblood`, cream text. Reuse the homepage `.band` treatment (oxblood surface, faint radial glow, decorative ripple SVG optional) and its numbered-row structure.

- **Head:** H2 (canonical size, cream) `Ways we can collaborate` + subheader `<p>` (Inter, cream `.78`): *A few ways Chelsea loves delivering value to audiences (virtually and in person).*
- **Three numbered rows** (reuse `.band-row`: large **light** numeral `01/02/03` in cream `.4`, then H3 in cream + body in cream `.78`, hairline dividers between — cream-tinted hairline `rgba(255,254,242,.16)`):
  - **01 · Podcast Guest** — Chelsea has been a guest on dozens of podcasts on a myriad of topics. Let's bring a lively conversation about trademarks, brand protection, or my journey as a lawyer and serial entrepreneur.
  - **02 · Guest Expert** — Masterminds, certification programs, and communities of business owners can add value to the experience by bringing Chelsea in to educate about the trademark process.
  - **03 · In-Person Speaking** — Chelsea is open to keynotes, panel presentations, and contributing at live events on a case-by-case basis, depending on your event's needs, budget and location.

*(See Flag 3: these rows mix third-person "Chelsea" with first-person "my" — kept verbatim, flag for a copy pass.)*

---

### BLOCK 3 — INQUIRY  *(form embed placeholder)*
On `--cream-1`. Give the section `id="inquire"` (hero CTA scroll target). `max-width:760px`, centered head.

- **H2:** `Tell me about your audience / show / event`
- **Body** (verbatim): *Whether you're looking for a podcast guest, a guest expert for your program, or a speaker for your next event, I'd love to hear more. Fill out the form below and I'll be in touch.*
- **Form embed placeholder (`.embed-ph`)** — reuse the holder style: bordered container (`border:1px dashed var(--hairline)`, `border-radius:14px`, `background:var(--cream-2)`), `min-height:420px`, centered label (ink `.5`): `Inquiry form embeds here`. Comment: Chelsea builds the form in MyCase or GHL (Task 5.4) — fields: name, email, organization/show name, opportunity type (dropdown), event date, "tell me about your audience," checkbox for an advance call — and pastes the embed code. Keep the outer wrapper so padding holds.

---

### BLOCK 4 — WHY CHELSEA  *(reuse the arched-portrait two-column, photo LEFT)*
On `--cream-2`. Reuse `.about-grid` (stack ≤820px) with the arched `.about-photo` + thin clay outline. Per the client mockup, **photo on the left, text on the right**.

- **Photo column — arched portrait:**
  - `src`: `images/legal-keynote-speaker-trademark-strategy-for-business.jpg`
  - `alt`: *Chelsea Fournier, a legal keynote speaker, wearing a teal blazer and white blouse standing in front of a brick wall and bushes*
  - (Chelsea's Google-Drive headshot, run through TinyPNG first — Task 2.10 / 4.4.)
- **Text column:** eyebrow `WHY BRING CHELSEA IN` + H2 `Legal expertise, translated for the room` + body (verbatim):
  > Most legal content is delivered for other lawyers. I built my career translating it for everyone else — business owners, entrepreneurs, and the experts in your community who need to understand what's at stake without sitting through a law school lecture.
  >
  > I bring a decade of trademark law experience and just as much time in the entrepreneurial trenches, which means I know how to make this topic land with a business-owner audience instead of going over their heads.

---

## Deferred (build leaves room, don't add now)
The copy doc's "future improvements" note lists items to add **later** as Chelsea builds speaking experience: full media-kit links, a list of organizations spoken for / guest-expert appearances, an updated bio, additional headshots + speaking reels, and testimonials. None are in scope now — build the 4 blocks clean; these slot in later (a testimonial section, if added, should reuse the editorial hairline-quote treatment from the homepage for consistency).

---

## SEO & accessibility checklist (verify before done)
- [ ] Exactly **one `<h1>`** (the hero kicker). Everything else H2/H3 or non-heading.
- [ ] All `<h2>` render at the same canonical size.
- [ ] Eyebrows are `<p class="eyebrow">`, **oxblood** (cream on the oxblood band), never heading tags.
- [ ] Hero "Let's Connect" CTA scrolls to `#inquire` (NOT `/consultation`); nav links → `/ , /services , /speaking , /podcast , /blog`; nav Book button → `/consultation`.
- [ ] Form holder is a clearly labeled placeholder with stable padding.
- [ ] Why-Chelsea photo uses exact SEO filename + alt; run through TinyPNG.
- [ ] Hamburger works ≤820px; `aria-expanded` toggles; closes on link + Escape.
- [ ] `prefers-reduced-motion`: reveals instant, grain frozen.
- [ ] Footer identical to homepage (global-asset parity).

---

## Flag to Chelsea before locking
1. **Hero body is incomplete.** The copy doc's second sentence ends mid-thought: *"If your audience is building something worth protecting, she will bring practical and energizing"* — no object, no period. **Do not invent the ending in the build.** Ship with the finished first sentence and get Chelsea's completion for the second (e.g., "…she'll bring a practical, energizing session your audience will actually remember," subject to her wording).
2. **H1 source.** The SEO/meta H1 field is blank; Block 1 supplies the H1. Plan uses the Block 1 line, which also fills the `<title>`. Confirm.
3. **Point-of-view mix.** Block 2 switches between third person ("Chelsea has been a guest…") and first person ("my journey," and Block 3's "I'd love to hear"). The writing-style KB specifies first person "I" throughout (solo practice, no "we"/third person). Kept verbatim here, but flag for a quick copy pass to settle on one voice.
4. **No final-CTA block by design.** Per Task 3.5 the page ends on Why Chelsea (4 blocks); the inquiry form is the conversion. Confirm she's fine ending there.
5. **Button label consistency.** Same nav-short vs body-full label note as the other pages.
