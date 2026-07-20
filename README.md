# AI Recruiting Agent — interactive prototype

A self-contained, single-file interactive prototype of an AI recruiting agent for Eightfold: an end-to-end hiring flow (9 steps), a recruiter **Mission Control**, a guided walkthrough, an interactive **Recruiter Review** workspace with a natural-language command box, live "agent working" animations, and a narrated **Present mode** for demos.

Everything is in `index.html` — no build step, no dependencies. Just open it, or host it.

## Publish to GitHub Pages (2 minutes)

### Option A — GitHub website (no command line)
1. Go to https://github.com/new and create a repo, e.g. `eightfold-recruiting-agent` (Public).
2. On the new repo page, click **uploading an existing file** and drag in `index.html`, `.nojekyll`, and `storyboard-shot-list.md`. Commit.
3. Go to **Settings → Pages**. Under **Build and deployment**, set **Source = Deploy from a branch**, **Branch = main**, folder **/ (root)**. Save.
4. Wait ~1 minute. Your site is live at:
   `https://<your-username>.github.io/eightfold-recruiting-agent/`

### Option B — command line
This folder is already a git repo with an initial commit. From here:

```bash
# create the repo on GitHub first (website or `gh repo create`), then:
git remote add origin https://github.com/<your-username>/eightfold-recruiting-agent.git
git branch -M main
git push -u origin main
```

Then enable Pages in **Settings → Pages** (Source: `main` / root), same as step 3 above.

If you have the GitHub CLI installed and authenticated, the whole thing is one line:
```bash
gh repo create eightfold-recruiting-agent --public --source=. --push
```
…then enable Pages in Settings.

## Local preview
Just double-click `index.html`, or:
```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## What's inside
- **Home** — landing page with three ways in (play the story / explore the flow / Mission Control).
- **Mission Control** — the recruiter cockpit: "needs you" queue, live agent loop, requisition portfolio, plus a 30-second guided tour.
- **9-step flow** — Understand the Role → Build the Talent Plan (grouped as one "Prep" phase) → Recruiter Review → Execution → Qualify & Score → Orchestrate & Schedule → Human Escalation → Continuous Optimization → Role Filled.
- **Present mode** — a narrated, looping walkthrough (▶ Present); arrow keys to move between scenes.
- **Agent / Recruiter toggle** — see what the agent does in the background vs. what the recruiter sees.

`storyboard-shot-list.md` is the companion shot list for a storytelling video.

---
Prototype only — all data is illustrative; no real messages are sent.
