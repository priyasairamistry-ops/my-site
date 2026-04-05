# Prioritised Fix List
*Based on independent reviews + panel discussion*

---

## P0 — Launch Blockers
*Do not share this URL until these are resolved.*

| # | Issue | Where | Who raised | Fix |
|---|-------|--------|------------|-----|
| P0-1 | `hello@priya.com` is a placeholder — will bounce or go nowhere | Contact section | Marcus, Ankit | Replace with real email address |
| P0-2 | LinkedIn link goes to `https://linkedin.com` (homepage, not profile) | Contact section | Marcus, Ankit | Replace with real LinkedIn profile URL |
| P0-3 | Contact form submits to a `setTimeout` mock — not a real backend | Form | Marcus, Ankit | Wire to Formspree, Netlify Forms, or email handler before launch |
| P0-4 | No favicon — site has no browser tab identity | `<head>` | Marcus | Generate favicon from diamond mark (16px, 32px, 180px apple-touch-icon). Add `<link rel="icon">` |
| P0-5 | No `<meta name="description">` — search and link previews will pull random body text | `<head>` | Marcus | Add: `<meta name="description" content="Technology advisor to telco, tech, and media organisations. Agentic AI strategy, IT cost reduction, and technology decisions that hold up commercially and technically.">` |
| P0-6 | No Open Graph tags — LinkedIn share preview will be blank | `<head>` | Marcus | Add `og:title`, `og:description`, `og:image`, `og:url` — essential given the target audience shares via LinkedIn |

---

## P1 — Important
*Fix before active promotion. These directly affect conversion and trust.*

| # | Issue | Where | Who raised | Fix |
|---|-------|--------|------------|-----|
| P1-1 | No photo of Priya anywhere on the site | About section | Shreya, Marcus, Meera, Rahul | Add professional headshot to About section — alongside or above the pull quote |
| P1-2 | Zero social proof — no testimonials, no client types, no outcomes | Entire site | All five panellists | Add at minimum: (a) one anonymised client quote, and (b) one scale signal e.g. "across engagements spanning FTSE 100 telcos and Series B tech companies" |
| P1-3 | Services describe deliverables, not outcomes | Services section | Shreya, Rahul | Add one outcome sentence per service: what changed as a result of the output? |
| P1-4 | Five differentiators are all self-asserted — no evidence attached | Why section | Shreya, Rahul, Meera | Add one micro proof point per differentiator: a brief anonymised scenario, a result, or a named capability with context |
| P1-5 | Body copy contrast fails WCAG AA (`#8c877e` on `#101318`) | Styles | Marcus | Lighten `--text-2` from `#8c877e` to `#a8a39a` minimum |
| P1-6 | Mobile nav logo is unreadable — "Technology Advisor" subtext renders at ~3px effective size | Nav, mobile | Marcus | At ≤600px: replace full wordmark SVG with mark-only SVG (the diamond, no text) |
| P1-7 | No secondary conversion path — only option is full contact form submission | CTAs | Ankit | Add a lower-friction CTA: downloadable one-pager, short email capture, or "See how I work" anchor to an engagement model section |
| P1-8 | Primary CTA text "Start a conversation" is passive and overused | Hero, CTA band | Ankit | Test alternatives: "Tell me what you're working on" or "Let's see if it fits" |
| P1-9 | "See the work →" links to Services, not actual work/case studies | Hero | Ankit | Either rename to "Explore services →" or remove until case studies exist |
| P1-10 | No engagement model or fee framing | Entire site | Meera, Rahul | Add even a brief signal: "Most engagements begin with a 2–4 week diagnostic" — reduces internal selling friction for the target buyer |

---

## P2 — Nice to Have
*Polish and growth improvements. Address post-launch.*

| # | Issue | Where | Who raised | Fix |
|---|-------|--------|------------|-----|
| P2-1 | "Why Priya Saira Mistry" section title reads as self-conscious | Nav + section label | Shreya, panel | Rename to "How I work" or "The approach" |
| P2-2 | The pull quote in About is unattributed — reads as self-written | About aside | Shreya | Either attribute it explicitly (Priya Saira Mistry, to [type of client], [year]) or reframe as a direct first-person statement |
| P2-3 | "Selected engagements only" pill is premature without established reputation | CTA section | Meera, Ankit | Either add context ("I work with 3–4 clients at a time to ensure the work gets proper attention") or hold until reputation is more publicly established |
| P2-4 | No `font-display: swap` in Google Fonts request — render-blocking text on slow connections | `<head>` | Marcus | Add `&display=swap` to Google Fonts URL (already partially done but verify it applies) |
| P2-5 | About section: five paragraphs before any proof = slow warm-up | About body | Rahul, Meera | Restructure: lead para → one proof/outcome signal → extended narrative. Don't cut — reorder. |
| P2-6 | Grain noise overlay in hero is set too low opacity to be visible | Hero CSS | Marcus | Either increase `opacity` of `.hero-bg::after` to 0.6+ or remove the element — it is currently doing nothing |
| P2-7 | Footer brand is a `<span>` — inconsistent with nav which uses the SVG logo | Footer | Marcus | Replace footer brand span with same mark-only SVG used in mobile nav |
| P2-8 | Mobile: negative-margin hover state on differentiator items may clip | Why section, mobile | Marcus | Test at 320px; adjust or remove the `margin-inline: -1rem` negative bleed at small breakpoints |
| P2-9 | Services cards on mobile are 500–600 words each — creates a long undifferentiated scroll | Services, mobile | Marcus, Ankit | Add a "show/hide" expand on mobile for the description body, keeping the number, title, and outputs list visible by default |
| P2-10 | No back-to-top mechanism on a long single-page site | Global | Marcus | Add a small fixed back-to-top button that appears after 600px scroll |
| P2-11 | No analytics | `<head>` | Ankit | Add GA4 or Plausible before any promotion — you need to know where people drop off |
| P2-12 | The "currently available" green dot could become stale | Contact | Ankit | Either make it dynamic or replace with a more static signal: "Taking on new engagements from [month]" |

---

## Summary: the one thing

If there is one fix that unlocks everything else on this list, it is **P1-2: add proof**.

The design is strong. The copy voice is real. The positioning is differentiated. None of that converts without evidence. One anonymised client outcome — one sentence with a before state, an intervention, and a result — changes the psychological contract entirely. It gives Shreya something to remember, gives Meera something to justify the outreach, gives Rahul something to attach a referral to, and gives Ankit something to put in the middle of a conversion funnel.

Everything else is polish. That one is load-bearing.
