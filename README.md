# Black Rim Solutions LLC — blackrimsolutions.com

Static marketing site for Black Rim Solutions LLC (software solutions and iOS apps, Denver, CO).
Hosted on Cloudflare as an assets-only Worker (same setup as movietrac.com, without Worker code).

## Layout

- `public/` — everything that is served. Plain HTML + one stylesheet, no build step.
  - `index.html` — home (Services, Apps, About, Contact)
  - `support.html`, `privacy.html`, `terms.html` — served at `/support`, `/privacy`, `/terms` (use these for App Store Connect)
  - `404.html`, `_headers` (security + cache headers), `robots.txt`, `sitemap.xml`
  - `img/logo.png` — brand logo (white; use on dark backgrounds only)
- `wrangler.jsonc` — Worker config and custom domains

## Develop

```sh
npm install
npm run dev        # http://localhost:8787
```

## Deploy

```sh
npx wrangler login # once
npm run deploy
```

The domain's DNS must be on Cloudflare. Deploy attaches `blackrimsolutions.com` and `www.blackrimsolutions.com`.
Redirect www → apex with a dashboard Redirect Rule (Rules → Redirect Rules → template "Redirect from WWW to root").

## Updating

- Add an app: copy an `.app-card` block in the Apps section of `public/index.html`.
- Change the copyright year / policy dates in the footers and page heads.
