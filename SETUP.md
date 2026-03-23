# Oliver AI Chat Setup Guide (Secure Proxy)

Oliver is powered by Google Gemini, but the API key should never be in `index.html` for a public site.
This project now uses a **Cloudflare Worker proxy** so your key stays private.

---

## Step 0 (Important): Rotate Exposed Key

If a key was ever committed to GitHub:

1. Go to [Google AI Studio API Keys](https://aistudio.google.com/apikey)
2. Delete the exposed key
3. Create a new key for the proxy

---

## Step 1: Deploy the Cloudflare Worker

1. Go to [Cloudflare Workers](https://dash.cloudflare.com/)
2. Create a new Worker (HTTP handler)
3. Replace the Worker code with the contents of `cloudflare-worker.js`
4. Add Worker secret:
   - Name: `GEMINI_API_KEY`
   - Value: your new Gemini key (`AIzaSy...`)
5. Deploy the Worker

Your Worker URL will look like:
`https://mcf-oliver-proxy.<subdomain>.workers.dev`

The chat endpoint is:
`https://mcf-oliver-proxy.<subdomain>.workers.dev/api/chat`

Note: This Worker handles all POST paths, so `/api/chat` and `/` both work.

---

## Step 2: Add Proxy URL to `index.html`

Open `index.html` and update:

```javascript
const GEMINI_PROXY_URL = 'https://mcf-oliver-proxy.<subdomain>.workers.dev/api/chat';
const GEMINI_MODEL = 'gemini-2.0-flash';
```

Do not add API keys to the frontend.

---

## Step 3: Redeploy GitHub Pages

Commit and push changes:

```bash
git add .
git commit -m "Use Cloudflare Worker proxy for Gemini API"
git push
```

GitHub Pages will refresh automatically from `main`.

---

## Step 4: Test

1. Open your GitHub Pages site
2. Click **Chat with Oliver**
3. Ask a question
4. Confirm you get a response

If it fails, open DevTools Console and check Worker logs in Cloudflare.

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| "Oliver isn't connected yet" | Set `GEMINI_PROXY_URL` in `index.html` |
| 401/403 from proxy | Confirm `GEMINI_API_KEY` Worker secret is set correctly |
| 429 rate limit | Normal on free tier; app retries automatically |
| 500/502 from proxy | Check Cloudflare Worker logs and redeploy |
| CORS error | Ensure Worker returns `Access-Control-Allow-Origin: *` (already in `cloudflare-worker.js`) |

---

## Free Tier Limits (Google Gemini)

- 15 requests per minute (RPM)
- 1,500 requests per day (RPD)
- 1,000,000 tokens per minute (TPM)

---

*Last updated: March 2026*
