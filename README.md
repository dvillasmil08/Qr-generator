# ultrashade-qr

A static QR code site for **Ultrashade Tattoos** (Grandview Heights, Columbus, OH).

- Top: a "Submit a Request" QR code, generated live in the browser, pointing to
  `ultrashadetattoos.com/request-form`.
- Below: a generator for making new plain black-and-white QR codes on the spot.

No build step, no backend, no image assets to keep track of — just one file:
`index.html`. All QR generation happens in the browser.

## Change what the main QR points to

Open `index.html`, find this near the top of the `<script>` block:

```js
var HERO_URL = "https://ultrashadetattoos.com/request-form";
```

Change it and save if the link ever needs to point somewhere else.

## 1. Push to GitHub

Easiest on an iPad or any browser, no terminal needed:

1. Go to [github.com/new](https://github.com/new) and create a repo (skip
   adding a README — you already have one here).
2. On the empty repo page, tap **uploading an existing file**.
3. Drag in `index.html` and commit. Make sure it's named exactly `index.html`
   (GitHub Pages/Cloudflare look for that name to serve as the homepage).

Or from a terminal:

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## 2. Deploy on Cloudflare Pages — free

1. Log into the [Cloudflare dashboard](https://dash.cloudflare.com).
2. In the sidebar: **Workers & Pages** → **Create** → **Pages** tab →
   **Connect to Git**.
3. Authorize Cloudflare to see your GitHub account, then pick this repo.
4. Build settings:
   - **Build command:** leave empty
   - **Build output directory:** `/`
5. Click **Save and Deploy**.

You'll get a live URL like `<project-name>.pages.dev` within a minute — free,
no time limit, no traffic cap that matters for a site this size. Every push
to `main` afterward auto-redeploys.

### Optional: custom domain

In the project → **Custom domains** tab, you can attach something like
`qr.ultrashadetattoos.com` if that domain is already on Cloudflare (or you
point its DNS there) — also free.
