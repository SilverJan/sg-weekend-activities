# Generate Singapore Weekend Activities Page

Today is Friday. Generate a curated weekend activities page for Singapore for this coming weekend: **{{SATURDAY_DATE}}** and **{{SUNDAY_DATE}}**.

## Step 1: Research

Search the web for current events and activities happening in Singapore this weekend. Perform these searches:

1. "Singapore events this weekend {{SATURDAY_DATE}}" — general weekend events
2. "Singapore new parks park connectors boardwalks opened 2026" — newly opened outdoor spots
3. "Singapore outdoor activities hiking trails cycling this weekend" — nature and outdoor
4. "Singapore Japanese festival events food this weekend" — Japanese culture
5. "Singapore German events festival this weekend" — German culture
6. "Singapore Indonesian events food bazaar this weekend" — Indonesian culture
7. "Singapore food markets hawker festivals this weekend" — food events
8. "things to do couples Singapore this weekend" — date ideas

For each search, extract concrete events with dates, times, locations, costs, and source URLs. Discard anything that:
- Is not happening this specific weekend or is not currently open/available
- Is a museum or art gallery exhibition
- Is an artsy/contemporary art event

## Step 2: Read the design template

Read `templates/base.css` to understand the design system (colors, fonts, spacing values).

## Step 3: Generate the HTML page

Create `public/index.html` with the following structure:

### Header
- Title: "Singapore Weekend Activities"
- Subtitle with the weekend dates
- A brief friendly intro (1-2 sentences, warm and inviting)

### Navigation
- A sticky "jump to section" navigation bar at the top with links to each category

### Activity Categories

Organize activities into these sections (skip any section with zero results):

- **Outdoor & Nature** — new parks, park connectors, boardwalks, hiking trails, cycling, gardens, beaches
- **Japanese Culture** — Japanese festivals, food events, cultural experiences, pop-ups
- **German Culture** — German festivals, food events, cultural experiences
- **Indonesian Culture** — Indonesian festivals, food bazaars, cultural events
- **Food & Drink** — food festivals, hawker events, night markets, new restaurants worth trying
- **Music & Nightlife** — concerts, live music, DJ events
- **Markets & Shopping** — flea markets, craft markets, pop-ups
- **Free Activities** — things that cost nothing

### Each activity card should show:
- Event/activity name (as a heading)
- One-line description
- Date and time
- Location (with area/neighborhood in parentheses)
- Cost (or "Free" with a green badge)
- A "More info →" link to the source website

### Footer
- "Generated on [current date] with Claude" attribution
- "Updated every Friday evening" note

## Design Requirements

- Clean, modern card-based layout with good whitespace
- Use the color palette from `templates/base.css`
- Category sections with clear headings
- Mobile-responsive: single column on phones, multi-column on desktop
- Smooth scroll behavior for navigation links
- "Free" badge on free activities (green pill/badge)
- Use a single relevant emoji per category heading as a visual indicator

## Quality Checks

Before finishing:
1. Verify `public/index.html` exists and is valid HTML5
2. Ensure all external links use https://
3. Confirm there are at least 8 activities total across all categories
4. Make sure the page is self-contained (no external CSS/JS dependencies)
