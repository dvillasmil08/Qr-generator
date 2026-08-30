# Ultrashade — QR Site

A single static page for **Ultrashade Tattoos** (Grandview Heights, Columbus, OH):

- A branded QR "plate" linking to `ultrashadetattoos.com`, styled to match the shop
  (dark, brass, engraved-plate look).
- A small generator underneath so you can make new QR codes for flyers, cards, or
  table tents any time — with the Ultrashade mark centered, or your own uploaded image.

No build step. It's one file: `index.html`. QR encoding runs entirely in the
browser via [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator)
(loaded from cdnjs), then it's drawn onto a `<canvas>` with the custom styling.

## Change what the main QR points to

Open `index.html`, find this line near the top of the `<script>` block:

```js
var HERO_URL = "https://www.ultrashadetattoos.com";
```

Change it to whatever link you want the main plate to encode (booking page,
Instagram, Google reviews, etc.) and save.

## 1. Put this in a GitHub repo

```bash
cd ultrashade-qr
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

(Create the empty repo on GitHub first at github.com/new — no README/license needed
there, since you already have one here.)

## 2. Deploy on Cloudflare Pages

1. Go to the Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** →
   **Connect to Git**.
2. Pick this repo.
3. Build settings: leave **Build command** empty and set **Build output directory**
   to `/` (this is a static site, nothing to build).
4. Deploy. Cloudflare will give you a `*.pages.dev` URL immediately, and you can
   attach a custom domain afterward under the project's **Custom domains** tab.

Every push to `main` will auto-redeploy.

## Notes

- The center mark on generated codes is drawn as a simple brass "U" monogram by
  default. Check "Add the Ultrashade mark" off, or upload a custom image, to
  change what sits in the middle.
- QR codes are generated at error-correction level H (highest), which leaves
  enough redundancy for a center image without breaking scannability — but
  always scan-test anything before printing it, especially with an uploaded
  logo.
