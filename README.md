# Drug Pronunciation Guide

An audio reference tool for medical students to hear the correct pronunciation of drugs across all major pharmacology categories.

**Live site:** `https://<your-github-username>.github.io/drug-pronunciations/`

---

## Project Structure

```
drug-pronunciations/
├── index.html                  # Home page — drug class hub
├── .nojekyll                   # Tells GitHub Pages to skip Jekyll processing
│
├── assets/
│   ├── css/
│   │   └── styles.css          # Shared stylesheet for all pages
│   └── audio/
│       ├── antipsychotics/     # One folder per drug class (kebab-case slug)
│       ├── anesthetics/
│       ├── antiarrhythmics/
│       ├── anticonvulsants/
│       ├── antidepressants/
│       ├── antiparkinson/
│       ├── glaucoma/
│       ├── muscle-relaxants/
│       └── sedative-hypnotics/
│           └── *.mp3           # Drug name as filename, e.g. Haloperidol.mp3
│
├── pages/
│   ├── antipsychotics.html     # One HTML page per drug class
│   ├── anesthetics.html
│   └── ...                     # All other class pages
│
└── data/
    └── drugs.json              # Master registry of all drug classes and drugs
```

---

## Adding a New Drug Class

Follow these four steps every time you add a new drug category:

### Step 1 — Create the audio folder

```
assets/audio/<slug>/
```

Use a lowercase kebab-case slug (e.g. `antibiotics`, `calcium-channel-blockers`).

### Step 2 — Add audio files

Drop MP3 files into the new folder. Name each file exactly as the drug name with no spaces — use hyphens if needed:

```
assets/audio/antibiotics/Amoxicillin.mp3
assets/audio/antibiotics/Azithromycin.mp3
```

### Step 3 — Create the page

Copy `pages/antipsychotics.html` as a starting template.
Save it as `pages/<slug>.html` and update:

| What to change | Example |
|---|---|
| `<title>` | `Antibiotics — Drug Pronunciation Guide` |
| `<h1>` text and icon | `💊 Antibiotics` |
| `--class-color` CSS variable | A hex colour for the accent |
| `<h2>` and drug count `<p>` | `Antibiotic Drugs` / `12 drugs` |
| Each `.drug-card` block | See template below |
| Audio `src` path | `../assets/audio/antibiotics/Amoxicillin.mp3` |

**Drug card template:**

```html
<div class="drug-card">
  <h3>Drug Name</h3>
  <audio controls>
    <source src="../assets/audio/<slug>/DrugName.mp3" type="audio/mpeg" />
    Your browser does not support the audio element.
  </audio>
</div>
```

### Step 4 — Add the card to index.html

Copy any `.class-card` block in `index.html`, update the `href`, color, icon, name, description, and badge drug count.

### Step 5 — Register in data/drugs.json

Add an entry to the `classes` array in `data/drugs.json`:

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
    { "name": "Amoxicillin", "file": "Amoxicillin.mp3" },
    { "name": "Azithromycin", "file": "Azithromycin.mp3" }
  ]
}
```

---

## Adding a New Drug to an Existing Class

1. Drop the MP3 into `assets/audio/<slug>/`.
2. Add a new `.drug-card` block in `pages/<slug>.html`.
3. Update the drug count in the `.page-header` `<p>` tag.
4. Update the badge count in the `index.html` card.
5. Add the drug entry to the `drugs` array in `data/drugs.json`.

---

## Hosting on GitHub Pages

1. Push this repository to GitHub (public repository).
2. Go to **Settings → Pages**.
3. Under **Source**, select **Deploy from a branch**.
4. Choose **main** branch, **/ (root)** folder, and click **Save**.
5. Your site will be live at:
   `https://<your-username>.github.io/<repository-name>/`

GitHub Pages serves `index.html` from the root automatically.
The `.nojekyll` file at the root ensures audio files and all assets load correctly.

---

## Audio File Naming Convention

| Rule | Example |
|---|---|
| Use the generic (INN) drug name | `Haloperidol.mp3` not `Haldol.mp3` |
| Capitalize first letter | `Quetiapine.mp3` |
| No spaces — use hyphens when needed | `Lithium-Carbonate.mp3` |
| Format: MP3 | `.mp3` only |

---

## Planned Future Drug Systems

The `data/drugs.json` file contains a `_future_systems` list of all planned pharmacology categories to be added over time, covering the full medical school curriculum:

- Cardiovascular, Respiratory, Gastrointestinal, Endocrine
- Renal / Diuretics, Antimicrobials, Antifungals, Antivirals
- Chemotherapy, Immunosuppressants, Corticosteroids
- NSAIDs / Analgesics, Opioids, Anticoagulants
- Biologics / Monoclonal Antibodies, Vaccines, and more

---

## License

MIT — see [LICENSE](LICENSE) for details.
