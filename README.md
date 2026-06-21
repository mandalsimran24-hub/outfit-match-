# Outfit Match

A small web app that helps you decide what to wear. Add your wardrobe — tops, bottoms, dresses, shoes, bags, accessories — pick the occasion, and it suggests outfit combinations ranked by color pairing and how well each piece suits the event.

No backend, no build step, no dependencies. It's a single HTML file that runs entirely in the browser.

## Why I built this

I wanted a portfolio project that solved a problem I actually have — figuring out what goes with what every morning — rather than a generic todo-list clone. Building something I'd genuinely use made it easier to think through edge cases (what happens with an empty wardrobe, what counts as a "neutral" color, how gym clothes should be scored differently from formal wear) instead of just filling in a template.

## How it works

- **Wardrobe:** items are stored with a name, category, and color, and saved to the browser's local storage so they persist between visits.
- **Color matching:** each item's hex color is converted to HSL, and pairs of items are scored using basic color theory — analogous hues (close together on the color wheel) and complementary hues (opposite each other) score well, while colors in between score lower. Low-saturation or very light/dark colors are treated as neutrals that pair with anything, which is roughly how people actually think about black, white, navy, and beige.
- **Event fit:** each category (top, dress, shoes, etc.) has a suitability weight per event type — for example, dresses are weighted low for the gym, gym shoes are weighted low for a wedding. This filters out combinations that wouldn't make sense before scoring is even applied.
- **Outfit generation:** the app builds candidate outfits two ways — dress-based (dress + best-matching shoes/bag/accessory) and separates-based (top + bottom + best-matching outerwear/shoes/bag/accessory) — scores each by a blend of color match (60%) and event fit (40%), then shows the top results.

## Tools used

- **Claude** (Claude.ai) — used to think through the scoring approach, write the HTML/CSS/JS, and review the result. I worked through this conversationally: described what I wanted, reviewed what was built, and asked for changes (e.g. the event-based filtering, the local storage persistence).
- No frameworks, no build tools — plain HTML, CSS, and JavaScript so it's easy to read top to bottom.

## Running it

Open `index.html` in any browser. That's it. To try it online without downloading anything, see the GitHub Pages link in the repo description (if enabled).

## Issues I ran into

- **Deciding what "matches" actually means.** Color matching is subjective, and a naive approach (e.g. "only show exact same color") would have been both wrong and boring. I settled on analogous + complementary hue matching with a neutral exception, which is a simplified version of real color theory and produces reasonable-looking suggestions without needing a design background to implement.
- **Avoiding nonsensical outfits.** Early versions could suggest a cocktail dress for the gym if the colors happened to match well. Adding the event-fit weighting as a filter *before* scoring (rather than just a tiebreaker) fixed this.
- **Floating point noise in scores.** Raw match scores came out as things like `0.7820000000000001`. Rounded with `Math.round()` before display.

## Possible next steps

- Let users upload a photo of each item instead of picking a flat color
- Weather-aware suggestions (skip the wool coat in summer)
- Outfit history, so it doesn't repeat the same combination two days running
