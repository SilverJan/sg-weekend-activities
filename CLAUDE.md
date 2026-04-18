# Singapore Weekend Activities Generator

## Project Purpose

This project generates a weekly HTML page showcasing weekend activities and events in Singapore. The page is deployed to GitHub Pages every Friday evening (9 PM SGT).

## Rules

1. **Output location**: Always write the generated HTML to `public/index.html`.
2. **Self-contained HTML**: The output must be a single, self-contained HTML file with all CSS inlined. Do not reference external stylesheets or JavaScript files (except for links to external event websites).
3. **Read the base CSS**: Before generating, read `templates/base.css` and incorporate its design tokens (colors, fonts, spacing) into your inline styles.
4. **Mobile-first**: The page must be responsive and look great on mobile phones, since the users will primarily browse it on their phones.
5. **No JavaScript frameworks**: Use vanilla HTML and CSS only. Minimal vanilla JS is acceptable for interactions like accordion toggles or smooth scrolling.
6. **Content accuracy**: Only include events and activities you found via web search. Do not fabricate event names, dates, venues, or prices.
7. **Practical information**: Every activity entry must include: name, date/time, location, estimated cost (or "Free"), and a link to the source.
8. **Couple-friendly**: All activities should be suitable for a couple doing weekend activities together.

## Content Preferences

**Prioritize these categories:**
- Outdoor activities: new park connectors, parks, boardwalks, nature trails, hiking, cycling routes
- Japanese culture: festivals, food events, pop-ups, cultural experiences
- German culture: festivals, food events, Oktoberfest-style events, cultural experiences
- Indonesian culture: festivals, food bazaars, cultural events

**Skip these entirely:**
- Museums and art galleries
- Artsy exhibitions or installations
- Abstract/contemporary art events
