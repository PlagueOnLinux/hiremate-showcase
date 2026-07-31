# HireMate

**Local-first AI career assistant that analyzes job offers, matches them against your profile, and helps manage your entire application pipeline — while keeping your data completely private.**

HireMate works as your personal recruitment analyst. It imports offers, compares them against your CV using a local LLM, detects skill gaps, calculates realistic match probabilities, and delivers actionable recommendations — without ever sending your data to an external service.

---

> **Public Showcase Repository**
>
> This repository contains architecture, documentation, development progress and feature overviews.
> The production source code is maintained in a private repository.

---

## What It Does

HireMate is not a mass-apply bot. It is a controlled assistant that works alongside you through the full job search cycle:

1. **Import** — Bring in job offers from URLs, pasted descriptions, or manual entry
2. **Parse** — AI extracts structured data: title, company, salary, contract type, work mode, requirements
3. **Compare** — Each offer is scored against your CV with career fit and realistic match ratings
4. **Detect Gaps** — Identifies missing requirements, experience mismatches, and stretch opportunities
5. **Recommend** — AI generates a clear recommendation with risk level and application strategy
6. **Track** — Manage applications through the full pipeline: new → to apply → applied → interview → outcome

---

## Core Workflow

```text
         Job Offer
             ↓
       ┌─────────────┐
       │   Import    │   URL fetch / paste / manual
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │  AI Parser  │   Extracts title, salary, requirements
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │   Scoring   │   Compares CV against offer requirements
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │ Gap Analysis│   Detects missing skills and experience
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │Recommendation│  apply / maybe / reject + reasoning
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │   Tracker   │   Manages application lifecycle
       └─────────────┘
```

---

## Key Features

### AI-Powered Scoring
- Dual scoring: **career fit** (alignment with goals) and **realistic match** (qualification match)
- Application chance levels: realistic / stretch / unrealistic
- Risk assessment: low / medium / high
- Comparison-based approach — AI checks each requirement against your CV directly

### Smart Import
- Fetches job page HTML, extracts readable text, parses structured data with AI
- Supports URL import, pasted descriptions, and manual entry
- AI-powered field extraction: title, company, salary, requirements, contract type
- Preview and edit before saving

### Candidate Profile
- CV upload with automatic text extraction (PDF)
- AI analysis of skills, tools, seniority, and experience level
- Dual CV support (Polish + English)
- Career direction tracking
- Additional notes for skills beyond CV
- Preferences for desired and unwanted job traits

### Job Discovery
- Automated scanning of saved search URLs
- Multi-page crawling with pagination support
- AI prescreening with quick scoring
- GPS-based distance calculation from candidate location
- Import queue with bulk actions

### Application Tracker
- Dark-themed management interface
- Status tracking across the full pipeline
- Quick AI scoring from the job list
- Detailed view with gap analysis and recommendations

---

## Current Status

### Sprint 2.8+

**Completed**

- Full job offer CRUD with dashboard
- AI scoring with career fit + realistic match dual analysis
- Job-vs-profile gap analysis with risk levels
- Candidate profile with CV upload and AI analysis
- Job import from URL and pasted text
- AI-powered description parsing and field extraction
- Application status pipeline
- Job source management and automated scanning
- AI prescreening with background processing
- GPS distance calculation for job locations
- Playwright browser integration

**Currently Building**

- Application package generation (CV tailoring, recruiter messages, interview prep)
- Improved AI scoring accuracy (comparison-based approach)
- Progress indicators for long-running AI tasks

**Next Milestones**

- Scheduled job discovery from saved searches
- Playwright-based application form assistant
- Email alert collector
- Duplicate detection
- Daily summary with top recommendations

---

## Roadmap

```text
[====================] Sprint 0 — Foundation          Done
[====================] Sprint 1 — Job Offers MVP      Done
[====================] Sprint 2 — AI Scoring          Done
[====================] Sprint 2.5 — Candidate Profile Done
[====================] Sprint 2.6 — CV Upload         Done
[====================] Sprint 2.7 — Gap Analysis      Done
[====================] Sprint 2.8 — Job Import        Done
[==========          ] Sprint 3 — Application Gen.    In Progress
[                    ] Sprint 4 — Assisted Apply
[                    ] Future — Automated Discovery
```

---

## Why Local AI?

Most job search tools require uploading your CV to cloud services. HireMate takes a different approach:

- **Complete privacy** — CV, preferences, and application history never leave your machine
- **No external uploads** — No data sent to OpenAI, Google, or any third-party API
- **Local LLM execution** — All AI processing runs on your hardware via Ollama
- **No subscription fees** — Unlimited analyses without per-request costs
- **Full data ownership** — You control every piece of your information
- **No rate limits** — Iterate as fast as your hardware allows

---

## Architecture

```text
Job Source (URL / paste / manual)
        ↓
    Collector
        ↓
    Database (PostgreSQL)
        ↓
    AI Engine (Ollama)
        ↓
    Backend API (FastAPI)
        ↓
    Dashboard (Jinja2)
        ↓
    User Decision
```

### Component Responsibilities

| Component | Role |
|-----------|------|
| **Collector** | Imports job offers from URLs, pasted text, or manual entry |
| **Parser** | Extracts structured data from raw job descriptions using local LLM |
| **AI Engine** | Analyzes candidate fit by comparing CV against job requirements |
| **Recommendation Engine** | Generates actionable recommendations with reasoning and risk assessment |
| **Application Tracker** | Manages application lifecycle from discovery through outcome |
| **Browser** | Handles JavaScript-rendered pages via Playwright |

---

## Tech Stack

**Backend**
- Python
- FastAPI

**AI**
- Ollama
- qwen3:8b (selected after model benchmarking)

**Database**
- PostgreSQL 17

**Frontend**
- Jinja2 (server-rendered)
- Vanilla JS

**Automation**
- Playwright (Chromium, headless)

**Infrastructure**
- Docker Compose

---

## Project Goals

- Reduce time spent on repetitive job search activities
- Keep candidate data fully private with no cloud AI dependencies
- Use local LLM inference instead of paid API services
- Help users make informed application decisions based on real skill matching
- Provide honest gap analysis rather than generic encouragement
- Support the full application lifecycle from discovery to outcome

---

## Design Philosophy

HireMate is built around a few core principles:

- Local-first by default — privacy is not optional
- AI should explain its recommendations, not just output a number
- Humans stay in control of every application decision
- Honest assessment over optimistic scoring
- Modular architecture that can evolve independently

---

## Author

**Maciej Bledowski**

- Portfolio: [maciejbledowski.pl](https://maciejbledowski.pl)
- GitHub: [@PlagueOnLinux](https://github.com/PlagueOnLinux)
- LinkedIn: [maciejbledowski](https://linkedin.com/in/maciejbledowski)

---

## License

This project is not open source. This repository serves as a public showcase of the project's scope, architecture, and development progress.
