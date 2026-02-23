# Cloudflare Pages Deployment (reopenapp.kkuk.dev)

## Prerequisites
- Cloudflare API Token with permissions:
  - Account: Cloudflare Pages (Edit)
  - Zone: DNS (Edit) for `kkuk.dev`
- Set env var:

```bash
export CLOUDFLARE_API_TOKEN=YOUR_TOKEN
```

## 1) Create/Deploy Pages project

```bash
cd /home/ecs-user/feng6611/reopenapp
npx wrangler pages project create reopenapp --production-branch=main
npx wrangler pages deploy . --project-name=reopenapp
```

## 2) Bind custom domain

```bash
npx wrangler pages domain add reopenapp.kkuk.dev --project-name=reopenapp
```

## 3) Verify DNS in zone
Zone ID: `454b5d13d50218c7294a4ecd0f237b39`

If needed, add CNAME:
- Name: `reopenapp`
- Target: `<pages-project>.pages.dev`
- Proxy: ON

## 4) Post-deploy SEO checks
- `https://reopenapp.kkuk.dev/robots.txt`
- `https://reopenapp.kkuk.dev/sitemap.xml`
- Rich results test for SoftwareApplication + FAQPage schema
- Social debug (OpenGraph/Twitter)
