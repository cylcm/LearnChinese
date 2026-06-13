# Mandarin Tutor — Filipino / English / 中文

A single-page web app for learning Mandarin, with lesson reference data and AI study tools
(powered by the Anthropic Claude API)..

## Files

```
mandarin_tutor.html      the whole app (one file)
manifest.json            index of lessons — add new lessons here
data/
  lessons/
    lesson02.json        Greetings & Apologies
    lesson03.json        Pronouns and Persons
```

## Hosting on GitHub Pages (recommended)

Opening the HTML straight from your hard drive (`file://`) does **not** work, because browsers
block reading the local `.json` files. Hosting fixes this. Steps:

1. Create a new GitHub repository and upload all these files (keep the folder structure).
2. In the repo: **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*, pick your branch
   (usually `main`) and folder `/ (root)`, then **Save**.
4. Wait ~1 minute. Your app will be live at
   `https://<your-username>.github.io/<repo-name>/mandarin_tutor.html`

## Running locally instead (no GitHub)

In this folder run a tiny web server, then open the printed URL:

```bash
python3 -m http.server
# then visit http://localhost:8000/mandarin_tutor.html
```

## Your API key — where it lives

- You enter your Anthropic API key in the app's **⚙️ API Key** tab.
- It is stored **only in your browser's localStorage**, on your own device.
- It is **never** written to any file, **never** committed to GitHub, and **never** sent
  anywhere except directly to Anthropic's API (`https://api.anthropic.com`) when you use a feature.
- Each visitor to your page enters their own key; keys are not shared between people.
- **Never** paste your key into the HTML source before committing. Only type it into the field at runtime.

## Adding more lessons

1. Create `data/lessons/lessonNN.json` (copy an existing one as a template).
2. Add one entry to the `lessons` array in `manifest.json` (set `"file": "data/lessons/lessonNN.json"`).

That's it — the HTML never needs editing to add lessons.

## Audio

Pronunciation uses your device's built-in Chinese text-to-speech voice (no cost, works offline).
If you hear nothing or the wrong accent, install a Chinese voice (see the in-app "Voice install tip").
Chrome, Edge, and Safari work best.
