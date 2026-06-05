# App Blueprint Generator

> Natural Language → Structured App Blueprint via a 6-stage AI pipeline

Type any app description in plain English. Get back a complete, validated JSON blueprint with UI schema, API schema, database schema, and auth rules — ready to build from.

---

## Live Demo

[Insert your GitHub Pages URL here]

---

## What It Does

You type:
> "Build a CRM with login, contacts, dashboard, role-based access, and premium payments"

You get back:
- **UI Schema** — pages, routes, components, role access
- **API Schema** — endpoints, methods, auth rules
- **DB Schema** — tables, fields, relations
- **Auth Schema** — roles and permissions
- **Validation Report** — consistency score, issues found, fixes applied

---

## How the Pipeline Works

```
User Prompt
    ↓
[Stage 1] Intent Extraction      → entities, features, roles, business logic
    ↓
[Stage 2] Architecture Design    → pages, API modules, DB tables
    ↓
[Stage 3] UI Schema Generation   → pages, routes, components
    ↓
[Stage 4] API Schema Generation  → endpoints, methods, auth rules
    ↓
[Stage 5] DB + Auth Schema       → tables, fields, roles, permissions
    ↓
[Stage 6] Validation & Repair    → cross-layer consistency check + auto-fix
    ↓
Final Blueprint JSON
```

Each stage is a **separate focused AI call**. Output of each stage feeds into the next. If a stage returns broken JSON, the system auto-repairs it before failing.

---

## Setup (2 minutes)

### Step 1 — Get a free Groq API key
1. Go to [console.groq.com/keys](https://console.groq.com/keys)
2. Sign up with Google (free)
3. Click **Create API Key**
4. Copy the key (starts with `gsk_...`)

### Step 2 — Run locally
1. Download `index.html`
2. Double-click to open in your browser
3. Paste your API key
4. Type your app description → click **Generate Blueprint**

### Step 3 — Host on GitHub Pages (free live URL)
1. Create a new GitHub repository
2. Upload `index.html` and `README.md`
3. Go to **Settings → Pages → Branch: main → Save**
4. Live URL: `https://yourusername.github.io/your-repo-name`

---

## Project Structure

```
/
├── index.html    ← entire app (single file, zero dependencies)
└── README.md     ← this file
```

No npm. No build step. No server. Just open in browser.

---

## Technical Details

| Component | Detail |
|-----------|--------|
| AI Model | Groq — llama-3.3-70b-versatile |
| Pipeline stages | 6 (each focused on one task) |
| Auto-repair | Broken JSON → re-prompts model to fix it |
| Rate limits | 30 req/min on Groq free tier (plenty for 6 stages) |
| Cost | Free |
| Latency | ~15–30 seconds per full blueprint |

---

## Why 6 Separate Stages Instead of 1?

| One big prompt | 6 focused stages |
|---|---|
| Model tries to do everything at once | Each stage does ONE thing well |
| Output often incomplete or inconsistent | Each output feeds and constrains the next |
| Hard to debug failures | Failed stage is isolated and retried |
| Like writing code in one giant function | Like a real compiler pipeline |

---

## Validation Layer

Stage 6 checks cross-layer consistency:
- Every API endpoint references a real DB table
- Every UI page has a corresponding API endpoint
- All roles in UI/API schemas exist in auth schema
- Returns a **consistency score (0–100)**

---

## Architecture Decisions

**Why Groq?**
- Free tier with 30 RPM (vs Gemini's 5 RPM)
- Extremely fast responses (~2s per stage)
- No daily quota exhaustion

**Why single HTML file?**
- Zero setup — just open in browser
- Deploy anywhere (GitHub Pages, Netlify, S3)
- No server = no running costs

---

## License
MIT
