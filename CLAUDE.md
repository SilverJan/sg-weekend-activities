# Singapore Weekend Activities Generator

## Project Purpose

Generates a weekly HTML page showcasing weekend activities and events in Singapore. Deployed to GitHub Pages every Friday morning (9 AM SGT), but also run manually.

## Hard Rules

1. **Output locations**:
   - `public/index.html` — main page with This Weekend + Upcoming Weekend + Past Weekends
   - `public/archive/{CURRENT_SAT_ISO}.html` — standalone snapshot of the "This Weekend" section (permalink)
2. **Self-contained HTML**: Single file, all CSS inlined. No external stylesheets or JS frameworks. External `<img>` URLs from source sites are OK; external event links are OK.
3. **Reject past events**: Never include any event whose end date is before the start of "This Weekend" (in SGT). If a source is ambiguous about the date, skip it.
4. **Cover both weekends**: Research and show activities for This Weekend AND Upcoming Weekend on the same page.
5. **Real content only**: Only include events/activities found via web search. Never fabricate names, dates, venues, or prices.
6. **Mobile-first**: Responsive, readable on phones.
7. **Every activity entry** must include: name, date/time, location, cost (or "Free"), source link.

## Content Preferences

**Prioritize these categories:**
- Outdoor: new park connectors, parks, boardwalks, nature trails, hiking, cycling
- Japanese culture: events, festivals, film, food, Japan Creative Centre, Japanese Association SG
- German culture: events, Goethe-Institut, Brotzeit / Paulaner events, German-speaking community
- Indonesian culture: festivals, food bazaars, events

**Skip entirely:**
- Museums (unless there's a special outdoor/nature/Japanese/German/Indonesian angle)
- Art galleries
- Abstract/contemporary art exhibitions

## Fallback for Japanese / German / Indonesian sections

If no confirmed weekend events exist for one of these cultures, include 1–3 evergreen "Worth visiting this weekend" picks — notable venues always open on weekends (e.g. Brotzeit outlets, Goethe-Institut library, Japan Rail Cafe, Japanese bookshops, Indonesian food streets). Label these clearly so they're not confused with time-bound events.

## Archive behavior

- Before finishing, Glob `public/archive/*.html` to build the "Past Weekends" section on `index.html`.
- Sort past weekends newest-first.
- The archive file for the CURRENT weekend (`{CURRENT_SAT_ISO}.html`) should NOT appear in the past list on its own page.
