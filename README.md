# My Personal Language Tutor — Filipino / English / 中文

A single-page web app for learning Mandarin, with lesson reference data and AI study tools
(powered by the Anthropic Claude API). Trilingual throughout: every item carries Filipino
(Tagalog), English, Chinese characters, and pinyin, plus built-in Chinese text-to-speech.

## Files

```
index.html               redirects the site root to the app
mandarin_tutor.html      the whole app (one self-contained file: HTML + CSS + JS)
manifest.json            index of lessons — add new lessons here
data/
  lessons/
    lesson02.json        Greetings & Apologies
    lesson03.json        Pronouns and Persons
    lesson04.json        Self-Introduction & Simple Questions
    lesson05.json        Numerals / Money
    lesson06.json        Calendar / Time
    lesson07.json        Adjectives / Grammar
    lesson08.json        Verbs / Grammar
    lesson09.json        Pets, Pests and Insects
    lesson10.json        Colors and Shapes
    lesson11.json        Places and Directions
    lesson12.json        Going Abroad / Travel
    lesson13.json        Shopping / Personal Belongings
    lesson14.json        Telephone Conversation
    lesson15.json        Parts of the House, Housewares & Appliances
    lesson16.json        Household Chores
    lesson17.json        Food & Condiments
    lesson18.json        Caring for the Sick
    lesson19.json        Parts of the Body
    lesson20.json        Common Illness
    lesson21.json        Units of Measurement & Specifiers
    lesson22_roleplay.json   Sample Conversation for Role Play
    lesson23_songs.json      Chinese Songs
    lesson24_exercises.json  Exercises
```

Note: Lesson 1 (Pinyin & Tones) is **built into the HTML**, not a JSON file. It appears under
the "📖 Pinyin & Tones" tab and is listed in `manifest.json` under `references`.

**Opening the app:** the site root (e.g. `https://<user>.github.io/<repo>/`) auto-redirects to
the app via `index.html`. You can also open it directly at
`https://<user>.github.io/<repo>/mandarin_tutor.html`.

## Features

The app has seven tabs:

- **📚 Lessons** — browse lesson reference data with a dropdown picker or a "Browse all" grid.
  Toggle any of the four languages on/off. Tap 🔊 next to any Chinese line to hear it.
- **📖 Pinyin & Tones** — built-in Lesson 1: the four tones, vowel and consonant tables with
  audio examples (no API key needed).
- **🔎 Explain / Translate** — type Chinese, English, or Filipino; get characters, pinyin with
  tone marks, English + Filipino meaning, and a usage note. (Needs API key.)
- **✍️ Practice** — generate 5 leveled practice sentences on an optional topic. (Needs API key.)
- **🎯 Quiz** — multiple-choice quizzes on tones, pinyin, or vocabulary drawn from loaded
  lessons. Keeps score. (Needs API key.)
- **💬 Tutor Chat** — a patient conversational tutor that replies in Chinese + pinyin + English
  (and Filipino if you write in it). (Needs API key.)
- **⚙️ API Key** — enter/manage your Anthropic key and pick the model.

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
- It is stored **only in your browser's localStorage**, on your own device
  (key name `mandarinTutor.anthropic_api_key`).
- It is **never** written to any file, **never** committed to GitHub, and **never** sent
  anywhere except directly to Anthropic's API (`https://api.anthropic.com`) when you use a feature.
- The app calls the API directly from the browser using the
  `anthropic-dangerous-direct-browser-access` header.
- Each visitor to your page enters their own key; keys are not shared between people.
- **Never** paste your key into the HTML source before committing. Only type it into the field at runtime.

### Model selection

The ⚙️ API Key tab also has a model picker (stored as `mandarinTutor.anthropic_model`).
Options: `claude-opus-4-8`, `claude-sonnet-4-6` (default), and `claude-haiku-4-5`.

## Adding more lessons

1. Create `data/lessons/lessonNN.json` (copy an existing one as a template — see the
   architecture doc for the JSON schema).
2. Add one entry to the `lessons` array in `manifest.json` (set `"file": "data/lessons/lessonNN.json"`).

That's it — the HTML never needs editing to add lessons.

## Audio

Pronunciation uses your device's built-in Chinese text-to-speech voice via the browser's
Web Speech API (`speechSynthesis`) — no cost, works offline. You can pick a voice and adjust
playback speed in the Lessons tab audio bar.
If you hear nothing or the wrong accent, install a Chinese voice (see the in-app "Voice install tip").
Chrome, Edge, and Safari work best.
