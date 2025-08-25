# Bitcoin converter (BTC, SAT, THB)

Convert between Bitcoin (BTC), Satoshis (SAT), and Thai Baht (THB). The
app fetches the live BTC/THB price from Bitkub and updates every 30
seconds, with an offline fallback.

## Features

-   Live BTC/THB price from Bitkub (`THB_BTC`)
-   Auto-refresh every 30s + manual refresh
-   One-field input: type in THB, SAT, or BTC and see the other two
    update
-   Dark/light theme with preference saved to `localStorage`
-   "Life on a Bitcoin Standard" panel showing everyday items priced in
    sats and BTC
-   Input cleaning, range checks, and user-friendly number formatting
-   Responsive layout and accessible labels/announcements (`aria-live`)

## How it works

-   API endpoint: `https://api.bitkub.com/api/market/ticker?sym=THB_BTC`
-   Success path:
    -   Reads `data.THB_BTC.last` as the current BTC/THB price
    -   Displays "LIVE," recalculates fields, refreshes the items grid,
        and stamps the local update time
-   Error path:
    -   Falls back to `FALLBACK_PRICE = 3,250,000` THB/BTC
    -   Shows an error message and flags the rate as offline
-   Conversion rules:
    -   `1 BTC = 100,000,000 sats`
    -   THB and SAT are rounded to integers; BTC can display up to 8
        decimals

## Project structure

    index.html               # All markup, styles, and scripts (single-file app)
    scpreview.png            # Open Graph/Twitter preview
    favcon.png               # Favicon (referenced in <head>)

## Run locally

You can open `index.html` directly in a browser. If your browser
enforces stricter local file policies, serve it with a simple static
server.

Python (the quickest way):

``` bash
# From the project folder
python -m http.server 8080
# Visit http://localhost:8080
```

Node:

``` bash
npx serve .
```

## Configuration

Open `index.html` and adjust the constants inside the `BitcoinConverter`
class as needed:

-   `API_URL` --- Bitkub ticker endpoint (default `THB_BTC`)
-   `REFRESH_INTERVAL` --- auto-refresh period in ms (default `30000`)
-   `FALLBACK_PRICE` --- used when the API is unreachable (default
    `3250000`)
-   `commonItems` --- array of `{ name, price }` in THB for the "Bitcoin
    Standard" grid

Example item:

``` js
{ name: "â Coffee (Starbucks)", price: 150 }
```

## Accessibility and UX notes

-   Live region updates (`aria-live="polite"`) announce price refreshes
    and countdown
-   All inputs have `<label>` elements and clear validation messaging
-   Keyboard-friendly: focus selects the whole field; debounced updates
    reduce jumpiness

## Error handling

-   Network or non-200 responses trigger fallback mode
-   Invalid API payloads show an error and keep the app usable with the
    fallback price
-   BTC input sanity range: `0.00000001` to `21,000,000`

## Performance

-   No frameworks; vanilla HTML/CSS/JS
-   Debounced input handling (`750ms`) to avoid excessive recalculation
-   Minimal DOM writes; grid rebuilt on rate changes

## Notes on the Bitkub API

-   This app performs client-side calls directly to Bitkub's public
    ticker endpoint
-   No API keys are used or stored
-   Be mindful of endpoint availability and potential rate limits
-   If your environment blocks cross-origin requests, serve the app over
    HTTP and test in a modern browser

## Deployment

Any static hosting works (GitHub Pages, Netlify, Vercel, S3/CloudFront,
etc.). Ensure `scpreview.png` and `favcon.png` are deployed at the site
root so social previews and the favicon work.

## Roadmap

-   Optional currency selector (e.g., USD base with THB derived)
-   PWA installability and offline caching
-   Unit tests for conversion and formatting helpers
-   User-editable "Bitcoin Standard" items with `localStorage`
    persistence

## Attribution

-   **Bitkub API** for market data\
-   Created by [@SorawisitT](https://x.com/sorawisitt) Â· contact at
    [sorawisit.com](https://sorawisit.com)

## License

MIT. See `LICENSE` if included; otherwise consider adding one.