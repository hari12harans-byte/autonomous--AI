# Autonomous AI Content Agent — Split Project

Split into two independently runnable pieces. No application code or logic
was changed — only reorganized, plus a couple of small run-scripts added so
the frontend can be served on its own.

```
autonomous-content-agent/
├── backend/    FastAPI app — agents, API, DB, scheduler, tests, Docker
└── frontend/   Standalone dashboard (index.html) + tiny static server
```

## Quick start (both pieces)

**1. Backend** (in one terminal):
```bash
cd backend
docker compose up --build
# or, without Docker:
#   python -m venv venv && source venv/bin/activate
#   pip install -r requirements.txt
#   uvicorn app.main:app --reload
```
Runs at **http://localhost:8000** (docs at `/docs`).

**2. Frontend** (in another terminal):
```bash
cd frontend
node server.js
```
Runs at **http://localhost:3000**. Open it, set "API Base" to
`http://localhost:8000`, click **Connect**, then **Init Agent**.

## Why two separate servers now?

Originally FastAPI served `index.html` directly at `/`, so frontend and
backend were one process. This split lets you run/deploy/host them
independently (e.g. frontend on Vercel/Netlify, backend on Render/Fly.io).
CORS is already open on the backend (`app/main.py`), and the dashboard
already had a built-in "API Base" field for pointing at a remote backend —
so no application code needed to change, just where each part lives.

See `backend/README.md` and `frontend/README.md` for details on each half.
