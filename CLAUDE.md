# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains knowledge base documents for a German medical practice telephone AI agent (ElevenLabs integration). The AI handles incoming calls and arranges callbacks for various services.

## Architecture

```
docs/                     # Source definitions (German)
  services_datenerhebung.md   # MVP service & data point specifications

output/                   # AI agent knowledge base files (consumed by ElevenLabs)
  available_services.txt      # Service definitions with processes
  data_collection.txt         # Per-service data fields and scripts
  available_practices.txt     # Practice locations
```

**Workflow:** Source definitions in `docs/` define what services and data points exist. Output files in `output/` are the formatted knowledge base documents that the telephone AI agent uses.

## Language Convention

- **English**: All explanations, instructions, process descriptions in output files
- **German**: Example scripts, confirmation phrases, sample dialogues

## Services (MVP)

1. New Patient Registration
2. Appointment Booking for New Patients → routes to #1
3. Appointment Booking for Existing Patients
4. Prescription Refill Request
5. Sick Leave Certificate Request (AU)
6. General Callback Request

## Key Constraints

- All services are callback-based (AI collects data, staff calls back)
- Data collection happens only after service is confirmed, never at conversation start
- Different services require different data fields (see `data_collection.txt`)
