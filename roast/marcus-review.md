# Marcus Tan — Product Designer Review
**Scope: Visual hierarchy, UX, responsiveness, iconology, high-res visual quality**

**Verdict: Solid bones. Several execution gaps that undermine the premium positioning.**

---

## Visual hierarchy — passing, not excellent

The typographic scale (Cormorant Garamond display + DM Sans body) is the right call and it's executed consistently. The amber accent reads as a deliberate system, not an accident. The dark-ground layout is confident.

What's missing is **contrast range**. Everything lives in a narrow band — dark backgrounds, dim text, amber highlights. The eye has nowhere to rest that feels genuinely different. A truly high-resolution site uses contrast as punctuation: one moment of stark brightness, one moment of near-black density. This site stays in the middle the whole way through.

The hero headline is the right size. The section headings are right. But the body copy (`var(--text-2)` at `#8c877e`) is too low-contrast against the dark backgrounds for extended reading. WCAG AA requires 4.5:1 for body text. That colour against `#101318` does not pass.

---

## Iconology and visual assets — this is the main problem

**There are no visual assets on this site beyond the diamond logo mark.**

For a high-resolution, production-grade personal brand site in 2025, this is a significant gap. A premium advisory site in Priya's competitive space would typically include:

- A professional photograph (not stock — her actual face)
- One or two subtle decorative graphic elements beyond the logo mark — perhaps an abstracted version of the diamond motif used as a section divider or background texture
- Potentially an abstract data or network visual in the hero to hint at the technology context

Right now the page is 100% text on dark backgrounds. That is a valid aesthetic choice — but only if the typography itself is exceptional enough to carry the visual weight at retina resolution. At 2x / Retina, pure text pages need to have near-perfect typographic execution: tighter leading on large headings, hanging punctuation, optically adjusted spacing. None of that fine-tuning has been done.

The diamond mark itself is geometrically clean and scales well. At small sizes (favicon, 32px) it loses the inner detail and reads as a solid amber square — the nested diamond effect disappears. **There is no favicon.** This is a basic omission. On a browser tab or bookmark, the site has no identity.

**The grain overlay on the hero** (noise texture via inline SVG data URI) is a smart detail — but it's set to `opacity: 0.4` on an element that is already `opacity: 0.03`. The net effect is invisible at normal screen brightness. It's doing nothing.

---

## CTAs and interactive states

The primary button (`btn-primary`) hover is clean — amber to lighter amber with a subtle lift and glow. The ghost/text CTA (`btn-text`) border-bottom hover is too subtle — most users won't register it as interactive.

The service cards have an amber top-bar that draws in on hover. This is refined. However it only works on desktop. On mobile (where hover states don't persist), the card differentiation disappears entirely — three identical dark blocks stacked vertically with no visual relief.

The nav CTA ("Let's talk") amber border styling is good and holds up on scroll.

---

## Whitespace — too conservative in some places, absent in others

The `--gap: clamp(80px, 10vw, 130px)` section padding is appropriate. The issue is *within* sections:

- The About section body has five paragraphs with `margin-top: 1.3rem` between them. That's tight for this typeface at this weight. The light 300-weight body text needs more breathing room — 1.8–2rem between paragraphs.
- The services grid on mobile collapses to a single column where each card is 500–600px of dense copy. There is no visual break between the card body and the "Typical outputs" sub-section except a thin border. At mobile width this reads as one undifferentiated wall.
- The differentiator list items are well-spaced on desktop. On mobile the `margin-inline: -1rem; padding-inline: 1rem` negative-margin hover area will clip against the viewport on small devices.

---

## Mobile responsiveness — mostly fine, specific failures

Tested at 375px viewport:

- **Nav logo SVG** at `height="34"` renders at roughly 180px wide on a 375px viewport — that's almost half the nav width before the hamburger menu. The "Technology Advisor" subtext in the SVG will be unreadable at this size (7.5px font rendered at 0.45× scale = ~3.4px effective). This needs a simplified mobile logo (mark only, or mark + name without tagline).
- **Hero headline** at `clamp(2.2rem, 9vw, 3rem)` on mobile — passes.
- **Services grid** single column on mobile — each card is very long. No sticky "Typical outputs" shortcut to jump past description. User has to scroll through ~1800px of service card text.
- **`hero-br` class** (`display: none` on mobile) works correctly.
- **"Why Priya Saira Mistry"** in the mobile nav dropdown is 24 characters. At `0.88rem` it fits but barely.
- **Form row** collapses to single column — correct.

---

## Load time and technical

- Two Google Fonts loaded (Cormorant Garamond + DM Sans, multiple weights and axes). This is a render-blocking resource with no `font-display: optional` or `font-display: swap` set in the CSS. On slow connections, users see a flash of unstyled text before the fonts load.
- No `<meta name="description">` tag — the browser will pull random text from the page for search snippets and link previews.
- No Open Graph tags (`og:title`, `og:description`, `og:image`) — if someone shares this URL on LinkedIn (likely for this audience), they get a blank preview.
- No favicon in any format.
- The contact form submits to nothing — `setTimeout(1200)` mock. Any technically literate visitor who inspects the source will see this.
- `hello@priya.com` and `https://linkedin.com` are placeholder values. These will bounce or go nowhere.

---

## Priority fixes from a design lens

1. **Favicon** — 5-minute fix, significant professionalism signal. Use the diamond mark.
2. **Add OG/meta tags** — invisible to visitors but essential for sharing and search.
3. **Mobile nav logo** — simplify to mark-only SVG below ~600px breakpoint.
4. **Body copy contrast** — lighten `--text-2` from `#8c877e` to at least `#a09890` for WCAG compliance.
5. **Add a photograph** — not a design problem per se, but the visual absence of a person is the biggest single gap in the high-res premium effect.
6. **Real contact details** — placeholder email and LinkedIn destroy trust for any visitor who clicks them.
7. **Font display** — add `font-display: swap` to prevent render-blocking text flash.
