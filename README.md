# Onboarding welcome + setup-status screen — v4

This folder is a from-scratch pass at the **original brief** (welcome header, two-state setup checklist, feature intro, "Let's go" CTA — living inside the Payload admin panel, admin colour palette, single self-contained HTML file per screen). It is a *sibling* to `airzoon-onboarding-page-design-v.3/`, not a patch on it — v.3 explored a different, later brief (a pure status page with a 3-state checklist and no CTA), and the two briefs contradict each other on several points. Nothing in v.3 was changed; this folder exists so both explorations stay intact and comparable.

## What's here

- `index.html` — a small gallery page linking the five screens below. Self-contained, dev-only convenience, not one of the deliverables itself.
- `production-split-screen.html` — the original two-panel takeover (full-bleed photo + welcome copy on the left, checklist + CTA on the right), copied over **unchanged** from `airzoon-onboarding-page-design-v.3/index.html`. It already satisfied this brief before this round even started — two-state checklist, no progress bar — so it wasn't rebuilt, only brought into this folder so it sits alongside the newer directions instead of only living in v.3. One correction to the earlier audit: this file is *not* fully single-file — its left-panel hero photo is a real background-image reference to `hero-left.jpg`, not an embedded `data:` URI like the logo is. That file is copied alongside it here (`hero-left.jpg`, same folder) so the page renders correctly; if this ever ships as a truly single-file deliverable, that photo would need inlining too.
- `variant-1-timeline.html` — four stages connected left-to-right by a plain rule.
- `variant-2-status-cards.html` — one card per stage, dashboard-style.
- `variant-3-roadmap.html` — stages alternating either side of a centreline.
- `variant-4-current-focus.html` — a one-sentence "what's happening right now" line above a full reference-style checklist card.

Every file is a **single self-contained `.html`**: inline `<style>`, inline `<script>`, the logo embedded as a base64 `data:` URI. No external CSS/JS files, no CDN, no build step — open any one of them directly and it renders. Each one includes its own "Preview controls" bar (Day 1 / Partial / All complete + Light/Dark) so every checklist state and theme can be reviewed on the one page, per the brief. All five end with the same "What you'll be able to do" feature strip and a "Questions? Reach us via WhatsApp / email" contact line.

## What changed from v.3, and why

The brief pasted for this round is explicit on points v.3's variants didn't follow:

1. **Two states only** — every checklist item is either *done* or *in progress*. v.3's variants used a third "upcoming" state (muted, no spinner) for anything after the current item; that's gone here. Every pending item — not just the next one — shows the same hollow circle-with-number and a spinner.
2. **No progress bar, no percentage** — the brief says this outright, describing the reference checklist itself as having neither. v.3's variants leaned on progress-bar visual language (filled/coloured segments, a labelled "Overall progress" bar with an "X of 4" count) as their main way of being visually distinct from each other. All of that is removed here; connecting lines are now plain, static, uncoloured — a layout device, not a meter.
3. **Amber stays reserved for "in progress"** — v.3's Variant 2 and Variant 5 had swapped amber for grey on that state at your request last round. That's reverted here to match the admin's own convention ("the amber accent replaced the generic blue throughout the admin").
4. **The checklist is "the heart of the screen"** — v.3's Variant 4 gave most of the page's weight to a "what's happening now" hero card and reduced the actual four-item checklist to a small sidebar list. Here it's rebalanced: the "what's happening now" line is a single slim sentence, and the full checklist — styled close to the brief's own reference (one white card, hairline dividers, marker/label/evidence-or-spinner per row) — is what actually dominates the page.
5. **Single self-contained file** — v.3's variants share CSS/JS/logo across files in a `shared/` folder, which is a reasonable pattern for comparing five *layout* explorations quickly, but it isn't what the brief asked for ("Single file, no dependencies... has to render from the raw file"). Every file here is fully standalone again, the same way the original production `index.html` already was.

## Why there are four variants, not five

v.3's fifth direction ("Minimal Client Portal") had exactly one device for showing overall progress: a labelled bar with a fraction next to it ("Overall progress — 2 of 4"). That's precisely what this brief rules out. Removing it, and then also pulling the checklist forward to be the page's visual centre (also required), leaves nothing distinct about that layout — it stops being "minimal" and becomes a smaller, quieter version of one of the other three. Rather than ship a diluted fifth option, it was dropped. If a genuinely different fifth direction is wanted, it would need a new idea, not a patched-up version of the old one.

## Note on the logo

The four new variants (and the gallery) render the logo at 2x the size they originally shipped with in this folder, per a later request. `production-split-screen.html` was left as-is — it's an unedited copy of the already-approved v.3 file, and its logo was already sized generously (100px) for that specific full-bleed hero treatment, so doubling it again wasn't applied there.

## Known gaps / not verified here

- Copy hasn't been translated or stress-tested for the ~30%-longer German text the brief flags; headline and button containers are reasonably generous but this wasn't specifically checked.
- Tablet breakpoints exist (each file collapses its layout below ~700px) but weren't screenshotted at exact tablet widths this round — only phone-width and desktop were checked in the browser.
- The "Let's go" button doesn't actually dismiss anything on click — per the brief, this is meant to be a static mockup ("no real logic needed... just needs to look right in its enabled and disabled states"), so that's intentional, not a gap.
