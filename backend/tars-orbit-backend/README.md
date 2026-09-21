# TARS ORBIT Backend

Node.js + Express + PostgreSQL backend for TARS ORBIT — Grow At Your Own Space.

## Core capabilities

- JWT authentication and profile management
- Course catalog + enrollment
- Automatic course workspace creation on enrollment
- Course modules and 3 daily assignments per learning day
- Assignment completion and course progress tracking
- Study workspaces and personal library uploads
- Persistent T.A.R.S. chat sessions/history
- PDF/DOCX/TXT/MD/CSV/JSON attachment extraction for T.A.R.S.
- Local-first Ollama AI with Qwen model configuration
- Optional cloud AI fallback
- Optional web research (Tavily when configured, public Wikipedia/DuckDuckGo fallback) with a learner-controlled Web Research toggle
- Workspace-aware tutoring and course-module context
- Assessments, skill analytics, classroom announcements and admin APIs

## Setup

```powershell
npm install
copy .env.example .env
npm run db:init
npm run dev
```

Set `DATABASE_URL` and `JWT_SECRET` in `.env` first.

## Local AI

Install Ollama, then:

```powershell
ollama pull qwen2.5:3b
ollama list
```

Default configuration:

```env
LOCAL_AI_ENABLED=true
OLLAMA_URL=http://127.0.0.1:11434
OLLAMA_MODEL=qwen2.5:3b
```

## Optional web research

No web API key is required for the basic fallback research path. T.A.R.S. can use public Wikipedia/DuckDuckGo lookups for research-intent questions.

For stronger search grounding, configure:

```env
WEB_RESEARCH_ENABLED=true
WEB_SEARCH_API_URL=https://api.tavily.com/search
WEB_SEARCH_API_KEY=
```

## Notes

- The database initializer creates the seeded courses, modules and 90 days of 3-per-day assignments.
- Re-running `npm run db:init` is safe for the seeded content.
- Admin bootstrap credentials are development/demo credentials; change them before public deployment.

V8 update: course-specific daily rotating quiz banks for the eight seeded learning paths.
