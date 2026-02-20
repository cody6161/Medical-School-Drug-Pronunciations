# Project Structure

A reference for understanding how the repository is organized.

---

## Folder Layout

```
Medical-School-Drug-Pronunciations/
|
|-- index.html                        # Main hub  12-system two-pane layout
|-- .nojekyll                         # Required: prevents GitHub Pages / Jekyll
|-- .gitignore
|-- LICENSE
|-- README.md                         # User-facing front page shown on GitHub
|
|-- assets/
|   |-- css/
|   |   `-- styles.css                # Single shared stylesheet for all pages
|   |
|   `-- audio/
|       |-- antipsychotics/           # One folder per drug class (slug-named)
|       |   |-- Haloperidol.mp3       # Each MP3 named exactly as the drug card
|       |   `-- ...
|       |-- anesthetics/              # Empty folders = "coming soon" classes
|       |-- antibiotics/              # Hub classes also have audio folders
|       |-- cell-wall-abx/
|       `-- ...                       # 72 folders total
|
|-- pages/
|   |-- antipsychotics.html           # Active class page (18 drug cards + audio)
|   |-- antibiotics.html              # Hub page -> links to 4 mechanism pages
|   |-- cell-wall-abx.html            # Subcategory detail page
|   |-- protein-synth-abx.html
|   |-- dna-rna-abx.html
|   |-- folate-abx.html
|   |-- anesthesia.html               # Hub page -> links to 3 anesthetic pages
|   |-- anesthetics.html              # Subcategory detail page
|   |-- local-anesthetics.html
|   |-- muscle-relaxants.html
|   |-- chemotherapy.html             # Hub page -> links to 5 chemo pages
|   |-- alkylating-agents.html        # Subcategory detail page
|   |-- antimetabolites-chemo.html
|   |-- antimicrotubule-agents.html
|   |-- topoisomerase-inhibitors.html
|   |-- antitumor-antibiotics.html
|   `-- ...                           # 72 pages total
|
|-- data/
|   `-- drugs.json                    # Master registry  all systems, classes & drugs
|
`-- docs/
    |-- STRUCTURE.md                  # This file
    |-- CONTRIBUTING.md               # How to add new drug classes and drugs
    `-- AUDIO-CONVENTIONS.md          # Audio file naming and format standards
```

---

## Navigation Architecture

The site uses a **three-tier navigation model**:

```
Tier 1  index.html (hub)
    12 system buttons (sidebar) -> drug class cards

        Tier 2  hub pages (for grouped categories)
            e.g. antibiotics.html, chemotherapy.html, anesthesia.html
            Shows mechanism/type subcategory cards

                Tier 3  detail pages (all other pages)
                    e.g. cell-wall-abx.html, antipsychotics.html
                    Shows individual drug cards with audio players
```

**Hub pages currently in use:**

| Hub Page | Subcategories |
|---|---|
| `pages/antibiotics.html` | Cell Wall, Protein Synthesis, DNA/RNA, Folate Inhibitors |
| `pages/anesthesia.html` | General Anesthetics, Local Anesthetics, NMB Agents |
| `pages/chemotherapy.html` | Alkylating, Antimetabolites, Antimicrotubule, Topoisomerase, Antitumor Abx |

All other drug class pages go directly from `index.html` to the detail page (Tier 1  Tier 3).

---

## Key Design Decisions

| Decision | Reason |
|---|---|
| All folder/file names are lowercase kebab-case | Prevents `%20` URL encoding issues on GitHub Pages |
| `body.hub-layout` class on index only | Lets one `styles.css` serve both the hub and all detail pages |
| Hub pages for large mechanism groups | Keeps index.html clean while preserving USMLE Step 1 subcategory structure |
| One audio folder per drug class slug | Each class is isolated  adding one class never touches another |
| `data/drugs.json` as master registry | Single source of truth for all metadata  easy to script against |
| `.nojekyll` at root | Required for GitHub Pages to correctly serve assets in non-Jekyll repos |

---

## Path Conventions

- **From `index.html`** (root level):
  - CSS: `assets/css/styles.css`
  - Pages: `pages/<slug>.html`

- **From `pages/*.html`** (one level deep):
  - CSS: `../assets/css/styles.css`
  - Audio: `../assets/audio/<slug>/DrugName.mp3`
  - Back to home: `../index.html`
  - Links to sibling pages (hub  subcategory): `<slug>.html` (relative, same folder)

---

## Systems in `data/drugs.json`

| ID | System Name | Cards on Index |
|---|---|---|
| `cardio` | Cardiovascular | 8 |
| `neuro` | Neurology & Psychiatry | 13 |
| `resp` | Respiratory | 6 |
| `gi` | Gastrointestinal | 5 |
| `renal` | Renal | 1 |
| `endo` | Endocrine | 4 |
| `repro` | Reproductive | 6 |
| `msk` | Musculoskeletal & Connective Tissue | 5 |
| `id` | Infectious Disease | 6 |
| `onco` | Oncology & Immunology | 4 |
| `ophtho` | Ophthalmology | 1 |
| `tox` | Toxicology | 1 |
