# Features

## Implemented

### Job Management
- Manual job offer creation with all relevant fields
- Job editing and deletion
- Status pipeline: new → to_apply → applied → interview → offer → rejected
- Contract type tracking (B2B, UoP, UZ, mixed)
- Work mode (remote, hybrid, on-site)
- Salary range with period (monthly / hourly / project)

### AI Job Scoring
- Dual scoring: career fit + realistic match
- Application chance levels: realistic / stretch / unrealistic
- Risk assessment: low / medium / high
- Missing must-have requirement detection
- Years-of-experience mismatch detection
- Missing tools and technologies identification
- Penalty for unrealistic requirements
- Penalty for pure L1/call center roles
- Polish recommendation labels
- qwen3:8b as default model (benchmarked)

### Job Import
- Import from URL (fetches and parses page)
- Import from pasted job description text
- AI-powered field extraction
- Import preview with editable fields
- Source URL and source name tracking
- Contract type parsing with fuzzy matching
- Polish number format salary extraction
- Graceful error handling for failed imports

### Candidate Profile
- CV file upload (PDF)
- Automatic text extraction from CV
- AI analysis of CV content
- Skill, tool, and seniority detection
- Profile update suggestions from CV
- User approval before saving changes
- Dual CV support (Polish and English)
- Additional notes field
- Job preferences (desired / unwanted traits)
- Career direction with exploration mode

### Gap Analysis
- Job requirements vs profile comparison
- Split scoring into career fit and realistic match
- Missing must-have requirements list
- Experience gap identification
- Stretch offer warnings in dashboard
- Gap details on job detail page
- Integration with AI recommendations

### Dashboard
- Dark theme UI
- Job list with status, score, and quick actions
- Inline AI scoring trigger
- Job detail page with full analysis
- Candidate profile management
- Add/import offer forms

## Planned

### Application Generation (Sprint 3)
- Application summary generation
- Recruiter message drafts
- CV tailoring notes
- Risk/fit checklist
- Copy buttons for generated content

### Assisted Applications (Sprint 4)
- Playwright browser automation
- Form field auto-fill
- Stop before final submit
- User confirmation before status update

### Automated Discovery (Future)
- Saved search URL scanning
- Import candidate queue
- Quick AI pre-scoring
- Duplicate detection
- Daily summary with stats
