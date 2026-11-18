# 🪔 Goodnight Stories

A brand-new desi bedtime story, spun from moonlight just for tonight.

Enter the child's name, age, how many minutes the story should last, and what it should be about. Gemini writes an original, gentle bedtime story with a warm Indian flavour (idlis, saris, marigolds, monsoon rain, Nani…). The story appears word by word, and you can have it read aloud in an Indian-English voice where your device has one.

## Setup (one time)
1. Get a free Gemini API key at https://aistudio.google.com/apikey
2. Open the site, click **⚙️ Settings**, paste the key and save. The key is kept only in your browser's localStorage. It is never committed to this repo.

## Deploy on GitHub Pages
1. Push `index.html` to a repo (e.g. `goodnight-stories`).
2. Go to **Settings → Pages**, set Source to **Deploy from a branch**, then choose `main` / `(root)`.
3. Your site goes live at `https://<your-username>.github.io/goodnight-stories/`.

## How it works
- A single static `index.html`: no build step and no server.
- It calls the Gemini `streamGenerateContent` API straight from the browser. It tries `gemini-3.8-flash` first, then falls back to older models if that one isn't available.
- Length is set at about 120 words per minute, a slow read-aloud pace.
