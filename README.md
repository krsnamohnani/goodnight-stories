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
- It calls the Gemini `streamGenerateContent` API straight from the browser. It uses `gemini-3.5-flash-lite` (fast and cheap) first, and falls back to other Gemini models if that one is busy or unavailable.
- Length is set at about 120 words per minute, a slow read-aloud pace.

## Evals (Braintrust)
The eval sends 10 test cases (`evals/cases.json`) through the app's real prompt and scores each story on 7 metrics: length, child's name, desi names, entertaining, bedtime-safe, reading level and desi details. The rules are in `evals/rubric.md`.

```bash
cp .env.example .env              # then paste your BRAINTRUST_API_KEY and GEMINI_API_KEY into .env
python3 -m venv .venv && source .venv/bin/activate
pip install -r evals/requirements.txt
braintrust eval evals/eval_goodnight.py
```
To run each case 3 times for steadier averages, use `TRIALS=3 braintrust eval evals/eval_goodnight.py`.
