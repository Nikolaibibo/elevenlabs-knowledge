# ElevenLabs Phone Agent Knowledge Base

Knowledge base files for the GoMedicus ElevenLabs AI telephone agent.

## Structure

```
output/
├── services.txt          # Service definitions (6 services)
├── data_collection.txt   # Required data fields per service
├── practices.txt         # Practice locations
├── conversation_flow.txt # Conversation rules & guidelines
├── faq.txt               # Common questions & answers
├── privacy.txt           # GDPR & AI transparency info
├── prime_program.txt     # Hausarztprogramm information
└── preventive_care.txt   # Vorsorge information
```

## Services

1. **New Patient Registration** - Register new patients and book first appointments
2. **Appointment Booking** - Book appointments for existing patients
3. **Prescription Refill** - Order medication refills (direct, no callback)
4. **Sick Leave Certificate** - Request AU certificates (initial or follow-up)
5. **General Callback** - General inquiries requiring callback
6. **Referral Request** - Request specialist referrals

## Deployment

Sync output files to Google Cloud Storage:

```bash
gsutil -m rsync -d -r -x '\.DS_Store$' output/ gs://gomedicus-public/elevenlabs/
```

## Language

- Instructions and documentation: English
- Response scripts and dialogue: German
