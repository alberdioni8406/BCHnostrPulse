# BCHnostr Pulse

**Live Bitcoin Cash Nostr Observatory**

A real-time, client-side dashboard for the BCHnostr community.  
Watch public network activity, active voices, conversations, hashtags, and signals — no accounts, no algorithm, no backend archive.

**Live:** [https://www.bchnostr.live/](https://www.bchnostr.live/)

---

## What it is

BCHnostr Pulse connects directly to the public Nostr relay `wss://relay.bchnostr.com` and observes public events in the browser. It derives:

- Live notes feed
- Unique notes & authors seen
- Activity over time and by hour of day
- Most active users
- Trending hashtags
- Trending conversations
- Top reactions
- Most mentioned
- Latency and posting pace

All statistics are computed from public events received since the page was opened, within the selected time window. Historical depth is limited by what the relay retains and what this client has observed. There is no separate archive server.

---

## Design philosophy

- **Independent** — not a corporate analytics product
- **Technical & transparent** — methodology is visible on the site
- **Privacy-respecting** — only public Nostr data; no private messages; no user accounts
- **Lightweight** — static HTML/CSS/JS, one WebSocket, Chart.js from CDN
- **Cypherpunk identity** — deep black, phosphor green, network grid, monospace technical labels

---

## Stack

| Piece | Detail |
|-------|--------|
| Frontend | Single-page HTML + inline CSS/JS |
| Charts | [Chart.js](https://www.chartjs.org/) 4.x (CDN) |
| Network | One persistent WebSocket to `wss://relay.bchnostr.com` |
| Hosting | Static (Vercel or any static host) |
| Backend | None |

No frameworks. No database. No extra network connections for status indicators.

---

## Project structure

```
BCHnostrPulse/
├── index.html              # Main dashboard (production entry)
├── advertise.html          # Sponsorship page
├── BCHnostr-pulse.html     # Legacy/alternate copy (prefer index.html)
├── assets/
│   ├── images/
│   │   ├── og-image.png    # 1200×630 Open Graph / X card
│   │   └── og-square.png
│   ├── icons/              # Favicons & PWA icons
│   └── site.webmanifest
└── README.md
```

---

## Running locally

Open `index.html` in a browser, or serve the folder:

```bash
npx serve .
# or
python3 -m http.server 8080
```

The dashboard needs network access to the relay. Mixed content is avoided by using `wss://`.

---

## Deploy

This is a static site. Point any static host (Vercel, Netlify, GitHub Pages, etc.) at the repository root.  
Production URL in use: **https://www.bchnostr.live/**

Ensure the `assets/` folder is deployed so OG images, favicons, and the web manifest resolve at:

- `/assets/images/og-image.png`
- `/assets/icons/...`
- `/assets/site.webmanifest`

---

## Configuration

Relay and behaviour live in the `CONFIG` object inside `index.html`:

```js
const CONFIG = {
  RELAY_URL: 'wss://relay.bchnostr.com',
  // … poll interval, limits, reconnect backoff, etc.
};
```

Sponsor banners are controlled via `AD_CONFIG` (same file). Set `active: false` or clear URLs to hide a slot without layout jumps.

---

## Sharing & SEO

- Full Open Graph and X (Twitter) Card metadata
- Canonical URL, theme-color, web manifest
- Native **SHARE PULSE** button (Web Share API + clipboard fallback)
- Custom OG image designed for social previews

---

## Support

Support the project with BCH:

```
bitcoincash:qrtv37u522gz8a5lezfqk5vukly93cu7gc8tn09040
```

Sponsorship / advertising: see [advertise.html](./advertise.html) or message [@alberdioni8406_](https://x.com/alberdioni8406_) on X.

---

## Related

- [BCHnostr](https://bchnostr.com)
- [CashCompass](https://cashcompass-bch.vercel.app/)

---

## License & ethos

Public Nostr data is public. This dashboard does not claim to own or control the network.  
It exists so the community can observe its own signal.

**Watching the signal. Measuring the network.**
