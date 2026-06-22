# Axel

Landing page for Axel — governance readiness for Australian SMBs.

Deployed on Cloudflare Pages at **https://axel-sxh.pages.dev**

---

## Deploying

**Automatic:** pushing to `main` triggers `.github/workflows/deploy.yml`, which builds tokens and deploys to Cloudflare Pages. No manual steps needed.

**Manual** (local):

Credentials live in `.env` (not committed). They are read by wrangler automatically when you prefix the command with them or export them to the shell.

**One command to build and deploy:**

```bash
CLOUDFLARE_ACCOUNT_ID=$(grep CLOUDFLARE_ACCOUNT_ID .env | cut -d= -f2) \
CLOUDFLARE_API_TOKEN=$(grep CLOUDFLARE_API_TOKEN .env | cut -d= -f2) \
npm run deploy
```

Or export the vars first, then just run:

```bash
export $(grep -v '^#' .env | xargs)
npm run deploy
```

`npm run deploy` does two things in sequence (see `package.json`):

1. `npm run build:tokens` — compiles `design/global.json` + `design/semantic.json` into `public/tokens.css` via Style Dictionary
2. `wrangler pages deploy public` — uploads `public/` to the `axel` Cloudflare Pages project

---

## Changing the page

| What | Where |
|---|---|
| HTML content | `public/index.html` |
| Component styles | `public/styles.css` |
| Design tokens (colours, type, spacing) | `design/global.json`, `design/semantic.json` |
| Voice and copy rules | `design/voice-tone.md` |

After editing tokens, the CSS must be recompiled before deploying — `npm run deploy` handles this automatically. Do not edit `public/tokens.css` directly; it is generated and will be overwritten.

---

## Cloudflare Pages project

- **Project name:** `axel`
- **Production URL:** https://axel-sxh.pages.dev
- **Build output directory:** `public/`
- **Account:** see `.env`
