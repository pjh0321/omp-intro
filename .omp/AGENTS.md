> **READ THIS ENTIRE FILE TO THE END BEFORE EDITING THIS REPO.** Agent context file: per the global authoring rule, keep it **English prose + tables only** — Korean only for functional literals (e.g. commit-label stems). Re-audit the whole file for non-English drift on every edit.

# omp-intro

Korean slide deck introducing the **omp (Oh-My-Pi)** terminal coding agent to a **developer** audience. Single standalone HTML (`index.html`). Theme: 3-way harness comparison — omp │ Claude Code + OMC │ Codex + OMX ("same model, different harness → different tokens / accuracy"). Intended for later URL sharing (static hosting).

## Repo shape

| Path | Role |
|---|---|
| `index.html` | The deck. One self-contained file (inline CSS/JS; Pretendard + JetBrains Mono; `--purple #7c6dff`). No build step. |
| `web-search-providers.md` | Reference: omp web-search provider comparison (researched). |
| `.omp/AGENTS.md` | This file (native project context, discovery priority 100). |

## Editing the deck

- `index.html` is a single file; prefer in-place string edits. Keep `<head>` / `<style>` / nav verbatim unless the task changes them.
- Page numbers are hardcoded and load-bearing (header/footer `.pg`, `data-i`, `titles[]`, nav jump-indices, TOC `data-goto`). Re-verify slide count and numbering after any add / remove / reorder.
- Tone: developer-level Korean "~다". Source every factual claim (file / section / URL); no overclaims.
- Layout / overflow check: render at **1920×1080** (the deck's design size; 1280×720 is too cramped). A slide already passing at a smaller viewport needs no re-check.

## Commit & push convention

Operator is a **non-developer** who reads git history as the primary retrospective artifact — write commit bodies they can follow.

### Cadence
- Never ask when/whether to commit. Commit at natural checkpoints; one coherent concern per commit.

### Message structure (every commit)
- Title: Korean, ≤50 chars, plain description. No `feat:` / `fix:` / `chore:` prefixes.
- Body: Korean content, **English** section headings, in this order:

| Section | Content |
|---|---|
| `## Why` | Problem / decision that triggered the change. |
| `## What` | Files / sections changed, written so a non-developer can follow. |
| `## Why this way` | Chosen approach vs alternatives; trade-offs. |
| `## Impact` | What changes for the user / next steps. |
| `## Verification` | How this commit was verified. |

### `## Why this way` — decision-origin label (required on each decision block)
`{actor}` = the exact model id the runtime exposes (read it, do not guess; e.g. `claude-opus-4-8`). Keep the Korean label stem byte-identical so cross-tool `git log --grep` matches regardless of which tool wrote the commit.

| Label | When |
|---|---|
| `[사용자 명시]` | User explicitly stated the decision. |
| `[사용자 위임 — {actor} 자율 결정]` | User delegated the decision; the running model chose autonomously. |
| `[{actor} 추가 제안]` | Model discovered and proposed independently. |
| `[사용자 통찰]` | Operator originated a reframe / breakthrough the model did not surface. |

### `## Why` — discovery-channel label (how the need surfaced)

| Label | When |
|---|---|
| `[운영 관측]` | Surfaced by running / using the system. |
| `[{actor} 발견]` | Model surfaced it during analysis. |
| `[사용자 발견]` | Operator spotted it. |

### After every commit
- Quote the full commit message body verbatim in the response (the UI collapses it; the operator cannot review otherwise).

### Push policy

| Action | Policy |
|---|---|
| Normal fast-forward (append-only) push | **Autonomous** — no confirmation. |
| History-rewriting push (amend / rebase of already-pushed commits, remote branch delete) | **Gated** — explicit operator OK first. |
| Force push (`-f` / `--force` / `--force-with-lease`) | **Never.** Warn of the risk even if asked directly. |

### Branch
- Commit directly to `main` (single operator, no PRs).
