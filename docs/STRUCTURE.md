# Project Structure

A reference for understanding how the repository is organized.

---

## Folder Layout

```
Medical-School-Drug-Pronunciations/
│
├── index.html                        # Home page — the drug class hub
├── .nojekyll                         # Prevents GitHub Pages from running Jekyll
│                                     # (required — without it, audio files may 404)
├── .gitignore
├── LICENSE
├── README.md                         # User-facing front page shown on GitHub
│
├── assets/
│   ├── css/
│   │   └── styles.css                # Single shared stylesheet for all pages
│   │
│   └── audio/
│       ├── antipsychotics/           # One folder per drug class
│       │   ├── Haloperidol.mp3       # Each MP3 named exactly as the drug
│       │   └── ...
│       ├── anesthetics/              # Empty folders = "coming soon" classes
│       ├── antiarrhythmics/
│       ├── anticonvulsants/
│       ├── antidepressants/
│       ├── antiparkinson/
│       ├── glaucoma/
│       ├── muscle-relaxants/
│       └── sedative-hypnotics/
│
├── pages/
│   ├── antipsychotics.html           # One HTML file per drug class
│   ├── anesthetics.html
│   ├── antiarrhythmics.html
│   ├── anticonvulsants.html
│   ├── antidepressants.html
│   ├── antiparkinson.html
│   ├── glaucoma.html
│   ├── muscle-relaxants.html
│   └── sedative-hypnotics.html
│
├── data/
│   └── drugs.json                    # Master registry of all drug classes and drugs
│
└── docs/                             # Administrative and housekeeping documents
    ├── STRUCTURE.md                  # This file
    ├── CONTRIBUTING.md               # How to add new drug classes and drugs
    └── AUDIO-CONVENTIONS.md          # Audio file naming and format standards
```

---

## Key Design Decisions

| Decision | Reason |
|---|---|
| All folder names are lowercase kebab-case | Prevents `%20` URL encoding issues on GitHub Pages |
| One HTML page per drug class | Simple to add, edit, or remove a class independently |
| CSS lives in `assets/css/` | Single file to update for any visual change across the whole site |
| Audio in `assets/audio/<slug>/` | Each class is isolated — adding one class never touches another |
| `data/drugs.json` as master registry | Single source of truth for all metadata — easy to query or script against in the future |
| `.nojekyll` at root | Required file for GitHub Pages to correctly serve assets when folder names or paths don't follow Jekyll conventions |

---

## Path Conventions

- **From `index.html`** (root level):
  - CSS: `assets/css/styles.css`
  - Pages: `pages/<slug>.html`

- **From `pages/*.html`** (one level deep):
  - CSS: `../assets/css/styles.css`
  - Audio: `../assets/audio/<slug>/DrugName.mp3`
  - Back to home: `../index.html`
