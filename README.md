# Oliworx Arcade

Oliworx Arcade is a browser-game directory. Games open in the built-in player when their host allows embedding.

## Publishing

GitHub Actions deploys the website to GitHub Pages at [oliworx.dev](https://oliworx.dev/).

## AI game guide

The chat panel connects to a Cloudflare Worker at `https://oliworx-arcade-chat.oliworx-chat-worker.workers.dev/api/chat`. The Worker uses Workers AI and limits each IP to 8 requests per minute. Its source is `cloudflare/arcade-chat.js`; `wrangler.toml` contains the deployment configuration.

Deploy Worker changes from this repository folder with:

1. `npx wrangler login`
2. `npx wrangler deploy`

The website and Worker deploy separately. GitHub Pages publishes website changes; Wrangler publishes Worker changes. The Worker uses a `workers.dev` address, so the domain can continue using Namecheap DNS.

## Updating the games

Edit the `games` array in `index.html`. Game names and links belong to their respective owners.
