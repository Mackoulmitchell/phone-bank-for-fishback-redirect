# Phone Bank for Fishback — Redirect

A minimal redirect site. Any visit forwards to the phone bank sign-up form:

**→ https://forms.gle/3ZCMRTgiaox8fA7q8**

## How it works

- [`vercel.json`](vercel.json) issues a server-side 307 redirect for every path (`/(.*)`).
- [`index.html`](index.html) is a static fallback (meta refresh + JS) in case the platform config isn't applied.

## Deploy (Vercel)

1. Import this repo in Vercel — no build step or framework needed.
2. Attach the desired domain in the Vercel project settings.

To change the destination, update the URL in both `vercel.json` and `index.html`.
