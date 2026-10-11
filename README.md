# Div's Rate Book

A phone-friendly price book (Abrasives, Power Tools, Spare Parts) with per-subcategory discounts.
Everything is static files, so it hosts for free on GitHub Pages.

## Files
- `index.html` – the whole app, including all prices
- `manifest.webmanifest`, `icon-*.png`, `apple-touch-icon.png` – home-screen icon and name
- `sw.js` – lets the app open offline after the first visit
- `.nojekyll` – tells GitHub to serve the files as they are

## Put it online (GitHub Pages)
1. Sign in at github.com and click **New repository**. Name it, for example, `rate-book`.
   Choose **Public** (free accounts can only use Pages with public repos).
2. On the empty repo page, click **uploading an existing file**.
3. Unzip this folder, select **all files inside it** (including `.nojekyll`; if your file picker hides it, skip it, the app still works) and drag them in. Click **Commit changes**.
4. Go to **Settings > Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
5. Wait a minute. Your link will be `https://YOUR-USERNAME.github.io/rate-book/`.

## Install on iPhone
Open the link in **Safari**, tap **Share**, then **Add to Home Screen**. It opens full screen like an app.
Open it once with internet so the offline copy is saved.

## Updating prices later
Edit `index.html` on GitHub (pencil icon). The price data sits near the top of the script in the block that starts with `const RAW =`.
Each line is: `item | carton pcs | price | stock` where stock is `Y` (in stock), `S` (arriving soon) or `N` (out).
Lines starting with `#` are subcategories, `##` are categories, `###` are the three tabs.
After changing prices, open `sw.js` and change `divs-rate-book-v1` to `divs-rate-book-v2` so phones pick up the new copy.

## Things to know
- Your saved discounts live in each browser and are tied to the web address. A new address starts with no discounts.
- The prices are public to anyone who has the link. If the rates are private, host on Cloudflare Pages or Netlify with a password instead; the same files work there unchanged.
