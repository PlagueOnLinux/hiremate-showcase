# HireMate

**Local-first AI job search assistant that analyzes job offers, matches them against your profile, and helps manage your entire application pipeline — while keeping your data completely private.**

HireMate works as your personal recruitment analyst. It imports offers, compares them against your CV using a local LLM, detects skill gaps, calculates realistic match probabilities, and gives you actionable recommendations — without ever sending your data to an external service.

---

> **Public Showcase Repository**
>
> This repository contains architecture, documentation, development progress and feature overviews.
> The production source code is maintained in a private repository.

---

## What It Does

HireMate is not a mass-apply bot. It's a controlled assistant that works alongside you through the full job search cycle:

1. **Import** — Bring in job offers from URLs (Pracuj.pl, LinkedIn, company sites), pasted descriptions, or manual entry
2. **Parse** — AI extracts structured data: title, company, salary, contract type, work mode, requirements
3. **Compare** — Each offer is scored against your CV with career fit and realistic match ratings
4. **Detect Gaps** — Identifies missing requirements, experience mismatches, and stretch opportunities
5. **Recommend** — AI generates a clear recommendation with risk level and application strategy
6. **Track** — Manage applications through: new → to apply → applied → interview → offer / rejected

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
       │  AI Parser  │   Extract title, salary, requirements
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │  Scoring    │   Compare CV vs. offer requirements
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │ Gap Analysis│   Missing skills, experience, languages
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │Recommendation│  apply / maybe / reject + reasoning
       └──────┬──────┘
              ↓
       ┌─────────────┐
       │  Tracker    │   Application status pipeline
       └─────────────┘
```

---

## Key Features

### AI-Powered Job Scoring
- Dual scoring: **career fit** (alignment with your goals) and **realistic match** (actual qualification match)
- Application chance levels: realistic / stretch / unrealistic
- Risk assessment: low / medium / high
- Comparison-based approach — AI checks each requirement against your CV

### Smart Job Import
- Import from URL — fetches page HTML, extracts readable text, parses with AI
- Import from pasted job description
- AI-powered field extraction (title, company, salary, requirements, contract type)
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

### Dashboard
- Dark-themed job management interface
- Status tracking across the full pipeline
- Quick AI scoring from the job list
- Detailed job view with gap analysis and recommendations

---

## Current Status

### Current Version — Sprint 2.8+

**Completed**

- Full job offer CRUD with dashboard
- AI scoring with career fit + realistic match dual analysis
- Job-vs-profile gap analysis with risk levels
- Candidate profile with CV upload and AI analysis
- Job import from URL and pasted text
- AI-powered job description parsing
- Application status pipeline
- Job source management and automated scanning
- AI prescreening with background processing
- GPS distance calculation for job locations
- Playwright browser integration

**Currently Building**

- Application package generation (CV tailoring, recruiter messages, interview prep)
- Improved AI scoring accuracy (comparison-based approach)
- Loading indicators and progress tracking

**Next Milestones**

- Automated job discovery from saved searches with scheduling
- Playwright-based application form assistant
- Email alert collector
- Duplicate detection
- Daily summary dashboard with recommendations

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

Most job search tools require you to upload your CV to cloud services. HireMate takes a different approach:

- **Complete privacy** — Your CV, preferences, and application history never leave your machine
- **No external uploads** — No data sent to OpenAI, Google, or any third-party API
- **Local LLM execution** — All AI processing runs on your hardware via Ollama
- **No subscription fees** — Run unlimited analyses without per-request costs
- **Full data ownership** — You control and own every piece of your data
- **Faster iteration** — No API rate limits, no waiting for cloud responses

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
| **Collector** | Imports job offers from URLs, pasted text, or manual entry. Handles HTML fetching, text extraction, and page crawling |
| **Parser** | Uses local LLM to extract structured data from raw job descriptions (title, salary, requirements, contract type) |
| **AI Engine** | Compares candidate CV against job requirements. Generates scores, gap analysis, and recommendations |
| **Recommendation Engine** | Produces actionable output: apply/maybe/reject with reasoning and risk assessment |
| **Tracker** | Manages application lifecycle from discovery through interview to outcome |
| **Browser (Playwright)** | Handles JavaScript-rendered pages and provides browser automation capabilities |

### Design Principles

- **Local-first** — All AI processing runs on your machine. No data sent externally.
- **User stays in control** — AI recommends, you decide. No automated applications without consent.
- **Privacy by design** — CV, preferences, and job history never leave your machine.
- **Modular** — Each component (scoring, import, profile) works independently.
- **Dockerized** — Single `docker compose up` to run the full stack.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Python, FastAPI |
| **Database** | PostgreSQL 17 |
| **AI** | Ollama, qwen3:8b (selected after model benchmarking) |
| **Browser** | Playwright (Chromium, headless) |
| **Frontend** | Jinja2 templates, server-rendered HTML |
| **PDF Processing** | PyMuPDF |
| **Infrastructure** | Docker Compose |
| **Version Control** | Git, GitHub |

---

## Project Goals

- Reduce time spent on repetitive job search activities
- Keep candidate data fully private — no cloud AI dependencies
- Use local LLM inference instead of paid API services
- Help users make informed application decisions based on real skill matching
- Provide honest gap analysis — not just encouragement
- Support the full application lifecycle from discovery to outcome tracking

---

## Author

**Maciej Bledowski**

- Portfolio: [maciejbledowski.pl](https://maciejbledowski.pl)
- GitHub: [@PlagueOnLinux](https://github.com/PlagueOnLinux)
- LinkedIn: [maciejbledowski](https://linkedin.com/in/maciejbledowski)

---

## License

This project is not open source. This repository serves as a public showcase of the project's scope, architecture, and development progress.
