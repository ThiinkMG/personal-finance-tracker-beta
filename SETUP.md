# Oliver AI Chat Setup Guide

Oliver, the AI budget assistant in the Personal Finance Tracker, is powered by **Google Gemini** (free tier). Follow these steps to connect it.

---

## Step 1: Get a Free Gemini API Key

1. Go to **[Google AI Studio](https://aistudio.google.com/apikey)**
2. Sign in with your Google account
3. Click **"Create API Key"**
4. Copy the generated key (it looks like `AIzaSy...`)

> **Cost:** The Gemini API free tier includes **15 requests per minute** and **1,500 requests per day** — more than enough for a student tool.

---

## Step 2: Paste Your Key into `index.html`

Open `index.html` in any text editor and find this section near **line 419**:

```javascript
// ===== GEMINI API CONFIG =====
// Paste your free Gemini API key between the quotes below.
// Get one at: https://aistudio.google.com/apikey
const GEMINI_API_KEY = 'YOUR_GEMINI_API_KEY_HERE';
const GEMINI_MODEL = 'gemini-2.0-flash';
// =============================
```

Replace `YOUR_GEMINI_API_KEY_HERE` with your actual key:

```javascript
const GEMINI_API_KEY = 'AIzaSyD...your-actual-key-here...';
```

Save the file. That's it — Oliver is now connected.

---

## Step 3: Test It

1. Open `index.html` in your browser
2. Click the **"Chat with Oliver"** button (bottom-right)
3. Try one of the starter prompts like "What's the 50/30/20 rule?"
4. Oliver should respond within a few seconds

If Oliver says "Oliver isn't connected yet," double-check that:
- You replaced `YOUR_GEMINI_API_KEY_HERE` with your actual key
- The key is inside the single quotes
- You saved the file after editing

---

## Model Options

The default model is `gemini-2.0-flash` which is fast and free. You can change it by editing the `GEMINI_MODEL` line:

| Model | Speed | Quality | Free Tier |
|-------|-------|---------|-----------|
| `gemini-2.0-flash` | Fast | Good | Yes |
| `gemini-2.5-flash` | Fast | Better | Yes |
| `gemini-2.5-pro` | Slower | Best | Limited |

---

## Security Note

**Important:** The API key is embedded in the HTML file, which means:

- **For personal use / testing:** This is fine. Only you can see the key.
- **For a live public website:** Anyone can view source and see your key. For production, you should set up a simple backend proxy (Cloudflare Worker, Vercel serverless function, etc.) that holds the key privately and forwards requests.

For a classroom or course embed where students access through an LMS (like in an iframe), the key is reasonably protected since students won't typically view source. But for a fully public site, use a backend.

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| "Oliver isn't connected yet" | Check that GEMINI_API_KEY is filled in and saved |
| "I'm having trouble connecting" | Check your internet connection; Gemini may be temporarily down |
| Oliver gives an error | Open browser console (F12) to see the error details |
| Responses are slow | Normal for first request; subsequent ones are faster |
| "API key not valid" | Regenerate your key at [AI Studio](https://aistudio.google.com/apikey) |

---

## Free Tier Limits (Google Gemini)

- **15 requests per minute** (RPM)
- **1,500 requests per day** (RPD)  
- **1,000,000 tokens per minute** (TPM)
- No credit card required
- No expiration

For a student finance tracker, you'll never come close to these limits.

---

*Last updated: March 2025*
