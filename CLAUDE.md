# CLAUDE.md

This file provides guidance to Claude when working with the ElevenLabs Phone Agent knowledge base.

## Architecture

```
SOURCE OF TRUTH (Obsidian Vault):
/Users/nikolaibockholt/Documents/obsidian/nikolai/Arbeit/GoMedicus/Projekte/ElevenLabs AI Phone Agent/
  ├── README.md              # Project overview & links
  ├── Services.md            # Service definitions
  ├── Data Collection.md     # Per-service data fields
  ├── Practices.md           # Practice locations
  ├── Conversation Flow.md   # Conversation rules
  ├── FAQ.md                 # Common questions
  ├── Privacy.md             # GDPR, AI transparency
  ├── Prime Program.md       # Hausarztprogramm info
  └── Preventive Care.md     # Vorsorge info

DERIVED OUTPUT (for ElevenLabs Agent):
/Users/nikolaibockholt/Documents/web/elevenlabs-knowledge/output/
  ├── services.txt
  ├── data_collection.txt
  ├── practices.txt
  ├── conversation_flow.txt
  ├── faq.txt
  ├── privacy.txt
  ├── prime_program.txt
  └── preventive_care.txt
```

## Workflow

1. **Edit in Obsidian** – All changes start in the Obsidian vault (source of truth)
2. **Sync to Output** – Claude converts and syncs changes to output folder
   - Remove Obsidian wiki-links `[[...]]` → plain text references
   - Convert blockquotes `>` → `Response:` format
3. **Deploy to Cloud** – Output files are synced to GCS for ElevenLabs

## Sync Conventions

| Obsidian | Output |
|----------|--------|
| `[[Practices]]` | `(see practices document)` |
| `> "German text"` | `Response: "German text"` |
| `**bold**` | plain text |

## Language Convention

- **English**: Instructions, process descriptions, file structure
- **German**: Example scripts, response phrases, dialogue samples

## Services (6 total)

1. New Patient Registration / Appointment Booking for New Patients
2. Appointment Booking for Existing Patients
3. Prescription Refill Request (Direct)
4. Sick Leave Certificate Request (AU)
5. General Callback Request
6. Referral Request

## Key Constraints

- All services are callback-based except Prescription Refill (direct)
- Data collection only AFTER service is confirmed
- One question at a time rule
- Phone number must be repeated digit by digit for confirmation
- Business hours: Mo-Fr 8:00-18:00

## Deployment

```bash
gsutil -m rsync -d -r -x '\.DS_Store$' output/ gs://gomedicus-public/elevenlabs/
```
