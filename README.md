# Sourcing & Nurturing Agent — Concept Review Page

**Live page:** https://rraju-ef.github.io/sourcing-agent-concept/
**Current version:** v1.2

A single-page concept document for the Sourcing & Nurturing Agent — an AI agent that
sources from the talent an organization already owns (owned-data first: internal
mobility → referrals → talent pool → content-driven demand), screens via the AI
Interviewer, schedules autonomously, and keeps a human approving every word candidates
or the public see.

The page doubles as the review tool: comments are made directly on it by highlighting
text, and everyone with the link sees everyone's comments.

## How to review

1. Open the live page. Short on time? Click **⚡ Exec view** (top bar) for the
   2-minute brief; click again for the full document.
2. Click the **💬 button** (bottom-right) to enter comment mode.
3. **Highlight any text** → *Add comment* → type your name once, then your note.
4. Click any amber highlight to **reply** or **resolve** a thread.
5. The **☰ button** opens the sidebar listing all comments in document order;
   **↻ Refresh** pulls in others' latest (the page also auto-syncs every 30s).
6. Press **Esc** anytime to exit comment mode and just read.

The sidebar header should read **👥 SHARED via API** — that confirms your comments
are saved centrally and visible to the group. If it reads 🔒, the comments backend
is unreachable; use **Export JSON** in the sidebar and send the file instead.

## How it works

| Piece | Where | What it does |
|---|---|---|
| `index.html` | This repo → GitHub Pages | The entire document, exec view, and comment UI — one self-contained file, no build step |
| Comments API | Fly.io (`/api/comments`) | A small JSON store all viewers read/write; comments persist on a Fly volume |

The page probes the API at load. If it's reachable, comments are shared; if not,
it degrades to browser-local storage with Export/Import as the fallback.

## Updating the page

The document text should stay **frozen during an open review round** — editing a
sentence orphans any comments anchored to it (they remain in the sidebar flagged
"anchor not found", but lose their highlight). Before publishing a revision:

1. Open the live page → sidebar → **Export JSON** (backup of all comments).
2. Replace `index.html` (Add file → Upload files → commit). Pages redeploys
   automatically in ~2 minutes.
3. Bump the version in the commit message and check the top bar shows it.

## Changelog

- **v1.2** — Reframed "internal-only" → "owned-data first" (LinkedIn boundary stays
  explicit; other compliant external channels remain open). Added the three-altitude
  hierarchy (company / function / role) to the Exec view.
- **v1.1** — Renamed to Sourcing & Nurturing Agent; added hierarchical vision,
  channel strategy, product-dependency tiers, and the review/commenting layer.
- **v1.0** — Initial concept: five capabilities, internal/referral channels,
  orchestration, automation boundary, hiring modes, buildability.

## Notes

- This is a **concept document** — compliance, change management, and security
  hardening are deferred to the design phase by intent.
- Anyone with the page URL can read the document and read/write comments; commenter
  identity is self-reported. Share deliberately.
