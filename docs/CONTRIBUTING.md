# Contributing — Adding Drug Classes & Drugs

This guide covers how to expand the site with new drug categories and individual drugs.

---

## Adding a New Drug Class

Follow all five steps to add a new category from scratch.

### Step 1 — Create the audio folder

```
assets/audio/<slug>/
```

Use a lowercase, kebab-case slug (e.g. `antibiotics`, `calcium-channel-blockers`).

### Step 2 — Add audio files

Drop MP3 files into the new folder. Name each file as the drug name — capitalize the first letter, no spaces (use hyphens if needed):

```
assets/audio/antibiotics/Amoxicillin.mp3
assets/audio/antibiotics/Azithromycin.mp3
assets/audio/antibiotics/Ciprofloxacin.mp3
```

See [AUDIO-CONVENTIONS.md](AUDIO-CONVENTIONS.md) for full naming rules.

### Step 3 — Create the page

Copy `pages/antipsychotics.html` as your starting template. Save it as `pages/<slug>.html` and update the following:

| What to change | Example |
|---|---|
| `<title>` tag | `Antibiotics — Drug Pronunciation Guide` |
| `<h1>` text and emoji icon | `💊 Antibiotics` |
| `--class-color` CSS variable | `#2ecc71` (any hex color) |
| `<h2>` heading | `Antibiotic Drugs` |
| Drug count in `<p>` | `12 drugs — Click play to hear pronunciation.` |
| Each `.drug-card` block | See template below |
| Audio `src` path | `../assets/audio/antibiotics/Amoxicillin.mp3` |

**Drug card template — copy and repeat for every drug:**

```html
<div class="drug-card">
  <h3>Drug Name</h3>
  <audio controls>
    <source src="../assets/audio/<slug>/DrugName.mp3" type="audio/mpeg" />
    Your browser does not support the audio element.
  </audio>
</div>
```

### Step 4 — Add the class card to index.html

Copy any existing `.class-card` block in `index.html` and update:

- `href` → `pages/<slug>.html`
- `--class-color` → your chosen hex color
- Icon emoji
- Class name
- Description
- Badge drug count (or `coming-soon` class if not yet ready)

### Step 5 — Register in data/drugs.json

Add a new entry to the `classes` array in `data/drugs.json`:

```json
{
  "id": "antibiotics",
  "name": "Antibiotics",
  "icon": "💊",
  "color": "#2ecc71",
  "system": "Infectious Disease",
  "description": "Agents used to treat bacterial infections.",
  "status": "active",
  "page": "pages/antibiotics.html",
  "audioDir": "assets/audio/antibiotics",
  "drugs": [
    { "name": "Amoxicillin",    "file": "Amoxicillin.mp3" },
    { "name": "Azithromycin",   "file": "Azithromycin.mp3" },
    { "name": "Ciprofloxacin",  "file": "Ciprofloxacin.mp3" }
  ]
}
```

Set `"status"` to `"active"` when audio is ready, or `"coming-soon"` while it is in progress.

---

## Adding a New Drug to an Existing Class

1. Drop the MP3 into `assets/audio/<slug>/`.
2. Add a new `.drug-card` block in `pages/<slug>.html`.
3. Update the drug count in the `.page-header <p>` tag on that page.
4. Update the badge count on the matching card in `index.html`.
5. Add the drug entry to the `drugs` array in `data/drugs.json`.

---

## Checklist Before Committing

- [ ] MP3 is in the correct `assets/audio/<slug>/` folder
- [ ] MP3 filename matches the `src` path in the HTML exactly (case-sensitive)
- [ ] Drug card added to `pages/<slug>.html`
- [ ] Drug count updated on the class page and on the `index.html` card
- [ ] Entry added to `data/drugs.json`
- [ ] Site tested locally by opening `index.html` in a browser
