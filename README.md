# InnYosemite Site

Static site for innyosemite.com, deployed to the Cloudflare Worker `innyosemitedev` (Workers Static Assets — no custom routing code needed; Cloudflare serves clean URLs like `/sunset-terrace` automatically from `public/sunset-terrace.html`).

## Structure

- `public/index.html` — homepage
- `public/sunset-terrace.html` — Sunset Terrace property page (`/sunset-terrace`)
- `public/woodustay.html` — WoodUStay property page (`/woodustay`)
- `public/casa-rio.html` — Casa Rio property page (`/casa-rio`)
- `wrangler.jsonc` — Workers Static Assets config
- `.github/workflows/deploy.yml` — deploys on every push to `main`

## One-time setup

Add a repo secret so the deploy workflow can authenticate to Cloudflare:

1. Create a Cloudflare API token at https://dash.cloudflare.com/profile/api-tokens using the **"Edit Cloudflare Workers"** template, scoped to this account.
2. In this repo: Settings → Secrets and variables → Actions → New repository secret.
3. Name: `CLOUDFLARE_API_TOKEN`. Value: the token from step 1.

After that, every push to `main` redeploys automatically. You can also trigger a deploy manually from the Actions tab ("Run workflow").

## Verify before relying on this

- Confirm `innyosemitedev` is the Worker actually bound to `innyosemite.com` (this repo assumes it is, based on it being the only Worker in the account, but routes/custom domains weren't independently verified).
- The WoodUStay and Casa Rio pages were built to match the Sunset Terrace template but haven't had a dedicated review pass yet — give them a look before treating them as final.
