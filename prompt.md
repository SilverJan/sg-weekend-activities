# Generate Singapore Weekend Activities Page

Today (SGT) is **{{TODAY_DATE}}**.

You are generating a curated weekend activities page for Singapore. You must produce content for BOTH:

- **This Weekend**: {{CURRENT_SAT_DATE}} and {{CURRENT_SUN_DATE}} (Saturday through Sunday, SGT)
- **Upcoming Weekend**: {{UPCOMING_SAT_DATE}} and {{UPCOMING_SUN_DATE}} (Saturday through Sunday, SGT)

## CRITICAL DATE RULES — read carefully

1. An event belongs to "This Weekend" only if its date falls on {{CURRENT_SAT_DATE}} OR {{CURRENT_SUN_DATE}} (or spans both).
2. An event belongs to "Upcoming Weekend" only if its date falls on {{UPCOMING_SAT_DATE}} OR {{UPCOMING_SUN_DATE}} (or spans both).
3. **NEVER include an event that has already ended** (end date before {{CURRENT_SAT_DATE}}).
4. **NEVER include an event whose date you cannot confirm from the source.** When in doubt, skip it.
5. Recurring events (e.g. "every Saturday") are fine — state the specific date they will run (e.g. "{{CURRENT_SAT_DATE}}").

## HARD EXCLUSIONS — never include

- Museums or art galleries (unless the angle is outdoor/nature/Japanese/German/Indonesian)
- Contemporary/abstract art exhibitions
- Chinese music events
- Istana open house
- Makeup events / brand pop-ups
- Mall shopping events (flea markets and craft markets are OK)
- Anything located at Changi Airport
- Singapore Cable Car
- FRIENDS show (the TV-show themed event)

## Step 1: Research — This Weekend

Run web searches to find events on {{CURRENT_SAT_DATE}} and {{CURRENT_SUN_DATE}}:

- "Singapore events {{CURRENT_SAT_DATE}}"
- "Singapore events {{CURRENT_SUN_DATE}}"
- "Singapore weekend events {{CURRENT_SAT_DATE}}"
- "new Singapore park connector OR boardwalk OR park 2026"
- "Singapore hiking trails nature activities {{CURRENT_SAT_DATE}}"
- "Japan Creative Centre Singapore events {{CURRENT_SAT_DATE}}"
- "Japanese Association Singapore events"
- "Singapore Japanese festival OR matsuri OR pop-up {{CURRENT_SAT_DATE}}"
- "Goethe-Institut Singapore events {{CURRENT_SAT_DATE}}"
- "Brotzeit OR Paulaner Singapore events"
- "German Singapore {{CURRENT_SAT_DATE}}"
- "Singapore Indonesian food bazaar OR festival {{CURRENT_SAT_DATE}}"
- "Singapore hawker OR food festival OR night market {{CURRENT_SAT_DATE}}"
- "Singapore drum and bass OR DnB club night {{CURRENT_SAT_DATE}}"
- "things to do couples Singapore {{CURRENT_SAT_DATE}}"

For each promising result, verify the date against the rules above.

## Step 2: Research — Upcoming Weekend

Repeat the same searches using {{UPCOMING_SAT_DATE}} and {{UPCOMING_SUN_DATE}}.

## Step 3: Build past-weekends list

Glob `public/archive/*.html`. Each filename is `{YYYY-MM-DD}.html` for a past Saturday. Build a sorted-newest-first list, EXCLUDING `{{CURRENT_SAT_ISO}}.html` (the one you're about to create).

## Step 4: Read the design template

Read `templates/base.css` for color palette, typography, card styles.

## Step 5: Generate HTML

### Write `public/index.html` with this structure:

```
Header
  - Title: "Singapore Weekend Activities"
  - Sticky nav: This weekend | Upcoming weekend | Past weekends

<section id="this-weekend">
  h2: "This weekend — {{CURRENT_SAT_DATE}} to {{CURRENT_SUN_DATE}}"
  [Activity cards organized by category]

<section id="upcoming-weekend">
  h2: "Upcoming weekend — {{UPCOMING_SAT_DATE}} to {{UPCOMING_SUN_DATE}}"
  [Activity cards organized by category]

<section id="past-weekends">
  h2: "Past weekends"
  [Simple list of <a href="archive/YYYY-MM-DD.html">Weekend of DD Mon YYYY</a>]
  If empty: "No past weekends archived yet."

Footer
  "Generated {{TODAY_DATE}} with Claude. Updated every Friday 9 PM SGT."
```

### Write `public/archive/{{CURRENT_SAT_ISO}}.html`:

A standalone snapshot of the "This Weekend" section with the same styling. Include a small "← Back to latest" link at the top pointing to `../index.html`. Do NOT include Upcoming Weekend or Past Weekends sections in the archive file.

## Activity categories (use only what applies; skip empty)

- 🌳 **Outdoor & Nature** — new parks, park connectors, boardwalks, hiking, cycling, beaches
- 🇯🇵 **Japanese Culture** — Japan Creative Centre, Japanese Association, pop-ups, festivals, film
- 🇩🇪 **German Culture** — Goethe-Institut, Brotzeit / Paulaner events, German community
- 🇮🇩 **Indonesian Culture** — festivals, food bazaars, community events
- 🍜 **Food & Drink** — hawker events, food festivals, night markets, notable new restaurants
- 🎵 **Music & Nightlife** — concerts, live music
- 🛍️ **Markets & Shopping** — flea markets, craft markets, pop-ups
- 🎁 **Free Activities** — cost-free picks

## Fallback rule for culture sections

If Japanese/German/Indonesian section would otherwise be empty, add 1–3 evergreen "Worth visiting this weekend" picks (always-open venues): Brotzeit outlets, Goethe-Institut library, Japan Rail Cafe, Japanese bookshops (e.g. Books Kinokuniya Japanese section), Indonesian food streets (e.g. Geylang Serai). Label clearly as "Worth visiting" rather than a time-bound event.

## Each activity card must show

- Name (h3)
- One-line description
- Date and time (exact day, e.g. "Sat {{CURRENT_SAT_DATE}}, 10 AM – 4 PM")
- Location (venue + area, e.g. "Gardens by the Bay (Marina)")
- Cost (or a green "Free" badge)
- A "More info →" link

## Quality checks before finishing

1. `public/index.html` exists, is valid HTML5, self-contained
2. `public/archive/{{CURRENT_SAT_ISO}}.html` exists, standalone
3. Every "This weekend" event is confirmed on {{CURRENT_SAT_DATE}} or {{CURRENT_SUN_DATE}}
4. Every "Upcoming weekend" event is confirmed on {{UPCOMING_SAT_DATE}} or {{UPCOMING_SUN_DATE}}
5. No past events slipped in
6. Japanese + German + Indonesian sections each have at least something (event or "Worth visiting" fallback)
7. At least 6 events/items in "This weekend" overall
