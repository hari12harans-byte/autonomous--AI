# AI Usage Log — PROMPTS.md

This project was built through an extended conversation with Claude (Anthropic).
Below is a summary of the key prompts and development phases.

## Phase 1: Core System Build
- Built the initial multi-agent pipeline: TopicAgent, ResearchAgent, WriterAgent, Orchestrator
- Requested pluggable LLM provider support (Mock/Groq/OpenAI/Anthropic)

## Phase 2: Production Hardening (Sprint 3)
- Added structured logging, exponential-backoff retries
- Added pagination, health checks
- Improved Docker configuration
- Added smoke testing and load testing

## Phase 3: Frontend/Backend Split
- Prompt: "In this separately create folder and put frontend and backend files, don't change the actual file or code"
- Prompt: "Not only html, add whatever file need to frontend and backend, give me as a complete project"
- Split the monolithic FastAPI + static-HTML app into independently runnable `backend/` and `frontend/` projects
- Added a zero-dependency `server.js` static server for the frontend
- Updated README documentation for both halves

## Phase 4: Git & Deployment
- Guided step-by-step through: Git installation, Git Bash usage, `git init`, `git add`, `git commit`, resolving upstream branch errors, resolving GitHub secret-scanning push protection (Groq API key), fixing repository history
- Deployed backend to Render (Docker-based Web Service)
- Deployed frontend to Netlify (static site)
- Debugged: Render environment variables, RESEARCH_SOURCE_URLS tuning after failed research cycles, Render cold-start / sleep behavior, duplicate "Initialize agent" calls across multiple users

## Phase 5: Polish
- Updated root README with live demo links, tech stack, and run instructions
- Discussed LinkedIn API integration (already scaffolded in `linkedin_client.py`) and its OAuth/approval requirements

---

*Full conversation transcript available on request.*
