# Audio File Conventions

Standards for naming and formatting audio files in this project.

---

## File Format

| Rule | Detail |
|---|---|
| Format | MP3 only (`.mp3`) |
| Encoding | Standard MP3, any bitrate (128 kbps recommended for size vs. quality) |
| Content | Single word or phrase pronunciation only — no music, no background noise |
| Length | Typically 1–5 seconds |

---

## File Naming Rules

| Rule | Correct | Incorrect |
|---|---|---|
| Use the generic (INN) drug name | `Haloperidol.mp3` | `Haldol.mp3` |
| Capitalize first letter | `Quetiapine.mp3` | `quetiapine.mp3` |
| No spaces — use hyphens if needed | `Lithium-Carbonate.mp3` | `Lithium Carbonate.mp3` |
| No special characters | `Clozapine.mp3` | `Clozapine®.mp3` |
| Must match the `<source src="">` path exactly | case-sensitive on GitHub Pages | — |

---

## Folder Placement

Every audio file must go in the folder matching its drug class slug:

```
assets/audio/<drug-class-slug>/DrugName.mp3
```

Examples:

```
assets/audio/antipsychotics/Clozapine.mp3
assets/audio/antibiotics/Amoxicillin.mp3
assets/audio/calcium-channel-blockers/Amlodipine.mp3
```

---

## Why INN Names Only

INN (International Nonproprietary Name) is the official generic drug name. Using brand names would mean recording multiple files for the same drug and creates ambiguity. All drug cards on the site display the INN name.

---

## Source / Raw Audio Files

Do not commit raw audio project files (`.wav`, `.aiff`, `.aup3`, etc.) to this repository — they are excluded by `.gitignore`. Only the final rendered `.mp3` should be committed.
