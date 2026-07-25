# HireMate

**A local-first AI assistant for job searching and application management.**

HireMate helps you find relevant job offers, analyze them against your profile, identify skill gaps, and prepare applications — all while keeping your data private and the final decision in your hands.

> This is the public showcase repository. The source code is maintained in a private repository.

---

## What It Does

HireMate is not a mass-apply bot. It's a controlled assistant that works with you:

1. **Collect** — Import job offers from URLs, pasted text, or add them manually
2. **Analyze** — AI extracts job requirements, salary, contract type, and work mode
3. **Score** — Each offer is scored against your profile with career fit and realistic match ratings
4. **Gap Analysis** — Identifies missing requirements, experience mismatches, and stretch opportunities
5. **Recommend** — AI generates a recommendation with risk level and application notes
6. **Track** — Full application pipeline: new → to apply → applied → interview → offer / rejected

---

## Key Features

### AI-Powered Job Scoring
- Dual scoring: **career fit** (how well it aligns with your goals) and **realistic match** (actual chances)
- Application chance levels: realistic / stretch / unrealistic
- Risk assessment: low / medium / high
- Detection of missing must-have requirements and experience gaps

### Smart Job Import
- Import from URL — fetches page, extracts text, parses details with AI
- Import from pasted job description
- AI-powered field extraction (title, company, salary, requirements, contract type)
- Preview and edit before saving

### Candidate Profile
- CV upload with automatic text extraction (PDF support)
- AI analysis of skills, tools, seniority, and experience level
- Career direction tracking (known path vs. exploring)
- Additional notes for skills not in CV
- Preferences for desired and unwanted job traits

### Dashboard
- Dark-themed job management interface
- Status tracking across the full pipeline
- Quick AI scoring from the job list
- Detailed job view with gap analysis and AI recommendations

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Backend | Python, FastAPI |
| Database | PostgreSQL |
| AI Engine | Ollama (local LLM — qwen3:8b) |
| Web Scraping | Playwright |
| Frontend | HTMX, Jinja2 (server-rendered) |
| Infrastructure | Docker Compose |

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
    Dashboard (HTMX/Jinja2)
        ↓
    User Decision
```

### Design Principles

- **Local-first** — All AI processing runs on your machine via Ollama. No data sent externally.
- **User stays in control** — AI recommends, you decide. No automated applications.
- **Privacy by design** — Your CV, preferences, and job history never leave your machine.
- **Modular** — Each component (scoring, import, profile) works independently.
- **Dockerized** — One `docker compose up` and you're running.

---

## Current Status

**Active development — Sprint 2.8 complete.**

### Completed
- Full job offer CRUD with dashboard
- AI scoring with career fit + realistic match dual analysis
- Job-vs-profile gap analysis with risk levels
- Candidate profile with CV upload and AI analysis
- Job import from URL and pasted text
- AI-powered job description parsing and field extraction
- Application status pipeline

### In Progress
- Application package generation (CV tailoring notes, recruiter messages)
- Structured AI output formatting

### Planned
- Automated job discovery from saved searches
- Playwright-based application form assistant
- Email alert collector
- Duplicate detection
- Daily summary dashboard

---

## Roadmap

```text
[====================] Sprint 0 — Foundation          ✓
[====================] Sprint 1 — Job Offers MVP      ✓
[====================] Sprint 2 — AI Scoring          ✓
[================    ] Sprint 2.5-2.8 — Profile & Import (90%)
[                    ] Sprint 3 — Application Generation
[                    ] Sprint 4 — Assisted Applications
[                    ] Future — Automated Discovery
```

---

## Why Local AI?

Most job search tools send your CV and preferences to cloud APIs. HireMate runs entirely on your hardware:

- **Ollama** handles all LLM inference locally
- **qwen3:8b** selected after benchmarking for best accuracy/speed balance
- Your data stays on your machine — period

---

## Author

**Maciej Błędowski**

- Portfolio: [maciejbledowski.pl](https://maciejbledowski.pl)
- GitHub: [@PlagueOnLinux](https://github.com/PlagueOnLinux)
- LinkedIn: [maciejbledowski](https://linkedin.com/in/maciejbledowski)

---

## License

This project is not open source. This repository serves as a public showcase of the project's scope and architecture.
