# mayhem.technology

Solana-native culture site for **mayhem** — deployed as a static site on Vercel.

**Live:** https://mayhem-technology.vercel.app (custom domain after DNS setup: https://mayhem.technology)

## Auto-deploy

Every push to `main` triggers a GitHub Actions deploy to Vercel.

Required repo secret:

| Secret | How to get it |
|--------|----------------|
| `VERCEL_TOKEN` | [vercel.com/account/tokens](https://vercel.com/account/tokens) → Create Token |

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
