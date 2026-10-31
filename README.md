# Oliworx Arcade

Oliworx Arcade is a searchable directory of browser games. Cards launch each game in an embedded player on oliworx.dev. Some game sites may block being embedded; the player offers an optional link to open the original site.

## Publishing

The existing GitHub Actions workflow deploys this repository to GitHub Pages. Its custom domain is oliworx.dev.

## AI game helper

The chat panel calls `/api/chat`. Its backend is a Cloudflare Worker using the Workers AI binding, so no model API key is exposed in the browser.

To deploy or update the backend:

1. Install Node.js if needed, then open a terminal in this repository folder.
2. Run `npx wrangler login` and finish the Cloudflare sign-in.
3. Run `npx wrangler deploy`.

The root `wrangler.toml` configures Workers AI, an approximate per-IP rate limit, and the route `oliworx.dev/api/*`. The domain must be an active Cloudflare zone with a proxied DNS record. Workers AI usage is metered; check Cloudflare's current pricing and usage dashboard.

The chat UI is included in the site, but it cannot answer until the Worker is deployed. The GitHub Pages workflow publishes only the static website; it does not deploy Cloudflare Workers.

## Updating the games

Edit the `games` array in `index.html`. Each entry has the game name, official URL, category, icon, color, and short description.
