# Phone Bank for Fishback — Redirect

A minimal redirect site. Any visit forwards to the phone bank Signal group invite:

**→ https://signal.group/#CjQKIGbuVN5QOwzaz85J50ebg05hPmStJFLm15S7wr9PS-wEEhDrXySme5jq8KIj7FJj-k0s**

## How it works

- [`vercel.json`](vercel.json) issues a server-side 307 redirect for every path (`/(.*)`).
- [`index.html`](index.html) is a static fallback (meta refresh + JS) in case the platform config isn't applied.

### The invite payload lives in the fragment

Everything after `#` is the group invite itself — strip it and the link is dead.
Fragments are never sent to a server, so they survive only because the
`Location` header (and the meta/JS fallbacks) carry the fragment verbatim. Keep
the `#…` intact everywhere it appears, and don't URL-encode the `#`.

## Deploy (Vercel)

1. Import this repo in Vercel — no build step or framework needed.
2. Attach the desired domain in the Vercel project settings.

To change the destination, update the URL in both `vercel.json` and `index.html`
(it appears four times in `index.html`: the `<meta http-equiv="refresh">`, the
`<link rel="canonical">`, the `location.replace()` call, and the visible `<a>`).
