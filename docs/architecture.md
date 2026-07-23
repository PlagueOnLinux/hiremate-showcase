# Architecture

## Overview

HireMate is designed as a local-first job search assistant running entirely in Docker containers on the user's machine.

## System Components

```text
┌─────────────────────────────────────────────────┐
│                  Docker Compose                   │
├─────────────────────────────────────────────────┤
│                                                   │
│  ┌─────────────┐    ┌─────────────────────────┐ │
│  │ PostgreSQL  │◄───│   FastAPI Backend        │ │
│  │   (data)    │    │   ├── Job Offers API     │ │
│  └─────────────┘    │   ├── Candidate Profile  │ │
│                      │   ├── AI Scoring Service │ │
│                      │   ├── Job Import Service │ │
│                      │   └── Dashboard (HTMX)  │ │
│                      └───────────┬─────────────┘ │
│                                  │                │
└──────────────────────────────────┼────────────────┘
                                   │
                          ┌────────▼────────┐
                          │  Ollama (Host)   │
                          │  qwen3:8b model  │
                          └─────────────────┘
```

## Data Flow

### Job Import Flow
```text
URL or pasted text
    → Fetch HTML / accept raw text
    → Extract readable content
    → AI parses job details (title, company, salary, requirements)
    → Preview for user review
    → Save to database
```

### AI Scoring Flow
```text
Job offer data + Candidate profile
    → Build scoring prompt
    → Send to Ollama
    → Receive: career fit score, realistic match, recommendation,
      risk level, missing requirements, application note
    → Save results to database
    → Display in dashboard
```

### Application Pipeline
```text
New → To Apply → Applied → Interview → Offer / Rejected
```

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Local LLM via Ollama | Privacy, no API costs, works offline |
| PostgreSQL over SQLite | Better for concurrent access, JSONB support |
| HTMX over SPA framework | Simpler, faster dev cycle, SSR by default |
| Docker Compose | One command to run entire stack |
| Playwright for scraping | Handles JS-heavy job board pages |
| qwen3:8b model | Best balance of quality and speed in benchmarks |
