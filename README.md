# mayhem.technology

Solana-native culture site for **mayhem** — deployed as a static site on Vercel.

**Live:** https://mayhem-technology.vercel.app (custom domain after DNS setup: https://mayhem.technology)

## Auto-deploy

**Option A — Vercel + GitHub (recommended)**

1. Open [Vercel project settings](https://vercel.com/heyrune-on-base-s-projects/mayhem-technology/settings/git)
2. Connect repository `pixelkittyfun/mayhem-technology`
3. Every push to `main` deploys automatically

**Option B — GitHub Actions**

Add repo secret `VERCEL_TOKEN` from [vercel.com/account/tokens](https://vercel.com/account/tokens), then push `.github/workflows/deploy.yml` from this repo.

## GoDaddy DNS (mayhem.technology)

In GoDaddy → **mayhem.technology** → **DNS**:

| Type | Name | Value | TTL |
|------|------|-------|-----|
| **A** | `@` | `76.76.21.21` | 600 |
| **A** | `www` | `76.76.21.21` | 600 |

Or switch nameservers to Vercel:

- `ns1.vercel-dns.com`
- `ns2.vercel-dns.com`

DNS can take up to 48 hours; usually 5–30 minutes.

## Local preview

```bash
python3 -m http.server 8787
# open http://localhost:8787
```

## Rebuild branding (from GAMETA root)

```bash
node scripts/rebrand-mayhem.mjs ./axol-dump/site
node scripts/patch-domain.mjs ./axol-dump/site mayhem.technology
cd axol-dump/site && git add -A && git commit -m "Update site" && git push
```
