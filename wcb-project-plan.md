# 🏗️ Work Crew Builder (WCB) — Complete Project Plan & Architecture

## Executive Summary

The Work Crew Builder is a **zero-code, drag-and-drop system** that any professional — regardless of technical skill — can install in Cursor IDE to generate a custom team of AI agent personas tailored to their specific job. The system uses the O*NET Generalized Work Activities Framework (41 standardized work activities used to classify all 900+ occupations in the US labor market) as its analytical backbone, combined with best-in-class context engineering practices from Anthropic and the BMAD Method's agent-as-code paradigm.

---

## System Architecture

### File Structure (Post-Installation)

```
My-Work-Crew/                     ← User's workspace
├── .cursor/
│   └── rules/
│       ├── wcb-agent.md          ← The Work Crew Builder agent persona
│       ├── crew-builder.mdc      ← Rules for building crews
│       ├── crew-sop.mdc          ← Operating rules for the crew (alwaysApply: true)
│       ├── riley.md              ← [Generated] Agent persona #1
│       ├── morgan.md             ← [Generated] Agent persona #2
│       ├── alex.md               ← [Generated] Agent persona #3
│       └── ...                   ← [Generated] Additional agents
├── AGENTS.md                     ← [Generated] Shared crew memory
├── STATUS.md                     ← [Generated] Task status & notification board
├── MYCREW.md                     ← [Generated] Crew summary & user guide
└── INSTALL-GUIDE.md              ← Installation instructions
```

### Artifact Inventory

| # | Artifact | Format | Purpose |
|---|----------|--------|---------|
| 1 | `wcb-agent.md` | Markdown persona | The builder agent — "Nova" — invoked via `@wcb-agent.md` |
| 2 | `crew-builder.mdc` | MDC rule file | Rules Nova follows to design & generate crews |
| 3 | `crew-sop.mdc` | MDC rule file | Operating procedures all crew agents follow |
| 4 | `INSTALL-GUIDE.md` | Markdown | Non-technical installation walkthrough |

---

## User Journey (Detailed)

### Step 1: Installation (2 minutes)

The user downloads a `.zip` containing the `.cursor/` folder with the three core files. They open Cursor, create a workspace folder, and drag-and-drop the `.cursor` folder in. No terminal, no npm, no git.

### Step 2: Invoke the Builder

User opens Cursor chat and types: `@wcb-agent.md Hi! I'd like to build a work crew.`

Nova greets the user warmly and collects:
- Job role & title
- Industry/company context
- Pain points & time sinks
- Existing tools in use

### Step 3: Task Analysis & Approval

Nova uses the **O*NET 41 GWA Framework** to systematically map the user's role to standardized work activities. For each applicable activity, Nova generates specific, contextualized tasks and presents them grouped by category with priority indicators (🔴 Critical / 🟡 Important / 🟢 Nice-to-have).

The user reviews, adds/removes tasks, and approves.

Nova then asks for the **autonomy level**:
- **LOW** 🟢 — Agents always ask before acting
- **MEDIUM** 🟡 — Agents execute routine tasks independently, ask for non-routine
- **HIGH** 🔴 — Agents work independently, escalate only when blocked

### Step 4: Crew Generation

Nova designs the optimal crew (3-7 agents) and generates:
- Individual agent `.md` files with full personas, tasks, skills, tools, and escalation triggers
- `AGENTS.md` — shared memory file with user context and crew roster
- `STATUS.md` — notification board and task tracker
- `MYCREW.md` — complete crew summary with quick-start guide

### Step 5: Operation

The user invokes any agent in a new chat: `@riley.md Please draft a weekly status report`

The agent:
1. Reads `AGENTS.md` for context
2. Reads `STATUS.md` for dependencies
3. Executes following `crew-sop.mdc` rules
4. Updates `STATUS.md` with results
5. Notifies the user per autonomy level

---

## Key Design Decisions

### Why O*NET as the Task Framework?

The O*NET (Occupational Information Network) is the US Department of Labor's comprehensive database covering 900+ occupations. Its 41 Generalized Work Activities provide a **universal taxonomy** that maps to every knowledge-worker role. This gives the WCB agent a structured, research-backed methodology rather than ad-hoc brainstorming.

### Why File-Based Coordination?

Cursor agents operate in isolated chat sessions — they cannot communicate directly. The file-based coordination pattern (AGENTS.md + STATUS.md) mirrors Anthropic's recommended "structured note-taking" approach and the AGENTS.md convention used by 60k+ open-source projects. It's simple, transparent, and the user can always see and edit the shared state.

### Why the Smart Zone Rule (<40% Context)?

Anthropic's research on context engineering confirms that LLM performance degrades as context fills — not at a hard cliff, but as a gradient. The 40% threshold ensures agents maintain peak attention quality while leaving room for conversation, tool outputs, and file contents.

### Why Three Autonomy Levels?

The three-tier system maps to natural trust progressions: LOW for initial setup or sensitive domains, MEDIUM for most workflows once trust is established, HIGH for high-volume repetitive work. The autonomy variable permeates every aspect of the crew-sop.mdc — from notification frequency to escalation triggers to independent execution scope.

---

## Context Engineering Best Practices Embedded

| Practice | Where Implemented |
|----------|-------------------|
| **Smart Zone (<40% context)** | crew-sop.mdc §1.1 |
| **External memory / note-taking** | AGENTS.md + STATUS.md pattern |
| **Structured note-taking** | STATUS.md with standardized tables |
| **Compaction awareness** | Session management rules in crew-sop.mdc §6 |
| **Progressive disclosure** | Agents read only relevant files per task |
| **Role-based context filtering** | Each agent reads only its scope |
| **Sub-agent architecture** | Each agent has a clean context per session |
| **Graceful degradation** | Context recovery protocol in crew-sop.mdc §6.3 |
| **Notification system** | STATUS.md notification board with emoji types |
| **Human-in-the-loop** | Autonomy levels with escalation triggers |
