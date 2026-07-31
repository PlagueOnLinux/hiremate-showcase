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

HireMate guides you through the complete application lifecycle — from discovering a job offer to tracking its outcome. It is not a mass-apply bot. It is a controlled assistant that keeps you in the loop at every step.

1. **Import** — Bring in job offers from URLs, pasted descriptions, or manual entry
2. **Parse** — AI extracts structured data from raw job descriptions
3. **Compare** — Score each offer against your CV
4. **Detect Gaps** — Identify missing requirements and stretch opportunities
5. **Recommend** — Receive a clear recommendation with reasoning
6. **Track** — Manage applications through the full pipeline

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
       │  Recommend  │   apply / maybe / reject + reasoning
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

**Currently Building**

- Application package generation (CV tailoring, recruiter messages, interview prep)
- Improved AI scoring accuracy (comparison-based approach)
- Progress indicators for long-running AI tasks

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

- **Complete privacy** — Your data never leaves your machine
- **No external uploads** — Nothing sent to OpenAI, Google, or third-party APIs
- **Local LLM execution** — All inference runs on your hardware via Ollama
- **No subscription fees** — Unlimited analyses at zero cost
- **Full data ownership** — You control all of your information
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

| Layer | Technology |
|-------|-----------|
| Backend | Python, FastAPI |
| AI | Ollama (local), qwen3:8b |
| Database | PostgreSQL 17 |
| Frontend | Jinja2, Vanilla JS |
| Automation | Playwright (Chromium, headless) |
| Infrastructure | Docker Compose |

---

## Project Goals

- Privacy-first by design — personal data stays under user control
- Local AI processing without reliance on cloud services
- Full ownership of candidate data at all times
- Transparent AI recommendations with clear reasoning
- Automation of repetitive job-search tasks while keeping humans in control

---

## Design Philosophy

HireMate is guided by the belief that AI should assist decision-making, not replace it. Privacy and transparency are core principles — users remain in full control of their data and every application decision they make. Local processing is preferred whenever possible, ensuring that sensitive career information never leaves the user's machine. The purpose of automation is to reduce repetitive work, not to remove the human from the process.

---

## Author

**Maciej Bledowski** — IT Support Engineer

- Website: [maciejbledowski.pl](https://maciejbledowski.pl)
- LinkedIn: [maciejbledowski](https://linkedin.com/in/maciejbledowski)
- GitHub: [@PlagueOnLinux](https://github.com/PlagueOnLinux)

---

## License

Released under the MIT License.
