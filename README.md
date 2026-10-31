# Oliworx Arcade

Oliworx Arcade is a searchable browser-game directory. Games open in an embedded player when their host allows framing; the optional fallback opens the original game site.

## Publishing

GitHub Actions deploys this repository to GitHub Pages at [oliworx.dev](https://oliworx.dev/).

## AI game helper

The chat interface and Cloudflare Worker source are included. The Worker uses Cloudflare Workers AI and a per-IP rate limit. It must be deployed separately from the GitHub Pages site.

This account currently serves the domain through Namecheap DNS, so the Worker is configured for a Cloudflare `workers.dev` address. After deployment, set the Worker URL in the chat request in `index.html` (currently `fetch("/api/chat", ...)`) to the URL Wrangler prints, followed by `/api/chat`. Then commit the change so GitHub Pages redeploys.

To deploy the Worker:

1. Install Node.js if needed and open a terminal in this repository.
2. Run `npx wrangler login` and finish the Cloudflare sign-in.
3. Run `npx wrangler deploy`.
4. Use the printed Worker URL in `index.html` as described above.

The chat will show a connection message until the Worker is deployed and the page points to its `workers.dev` URL. The GitHub Pages workflow publishes only the static website; it does not deploy the Worker.

## Updating the games

Edit the `games` array in `index.html`. Game names and URLs belong to their respective owners.
