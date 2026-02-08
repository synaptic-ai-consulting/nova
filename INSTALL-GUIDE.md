# 📦 Work Crew Builder — Installation Guide

> **No coding experience needed!** Follow these simple steps to set up your AI work crew.

---

## What You'll Need

1. **Cursor IDE** installed on your computer
   - Download from [cursor.com](https://cursor.com) if you don't have it
   - It's free to start (Pro plan recommended for heavy use)

2. **The Work Crew Builder files** (the folder you downloaded)

---

## Installation Steps

### Step 1: Open Cursor

Launch the Cursor application on your computer.

### Step 2: Create or Open a Workspace

- Click **File → Open Folder**
- Create a new empty folder anywhere on your computer (e.g., `My-Work-Crew`)
- Select that folder — this becomes your **workspace**

### Step 3: Add the WCB Files

**Option A — Drag and Drop (Easiest):**
1. Open the WCB download folder in your file explorer
2. You'll see a `.cursor` folder and some files
3. **Drag the entire `.cursor` folder** into your workspace in Cursor's sidebar
4. That's it! The files are in the right place.

**Option B — Manual Copy:**
1. Copy the `.cursor` folder from the download into your workspace folder
2. Make sure the structure looks like this:

```
My-Work-Crew/
├── .cursor/
│   └── rules/
│       ├── wcb-agent.md
│       ├── crew-builder.mdc
│       └── crew-sop.mdc
```

### Step 4: Start Building Your Crew!

1. In Cursor, open the **Chat panel** (click the chat icon on the right sidebar, or press `Cmd+L` / `Ctrl+L`)
2. In the chat input, type:

```
@wcb-agent.md Hi! I'd like to build a work crew for my role.
```

3. Nova (your Work Crew Builder) will greet you and ask about your job
4. Follow the conversation — Nova will guide you through everything!

---

## What Happens Next

Nova will:
1. 🔍 Ask about your role and work context
2. 📋 Research and present tasks specific to your job
3. 🎚️ Ask how much freedom you want your crew to have
4. 🏗️ Build your custom crew of AI agents
5. 📄 Create all the files and give you a summary

After setup, you'll have a team of specialized AI agents you can chat with anytime!

---

## Troubleshooting

**"I don't see the chat panel"**
→ Press `Cmd+L` (Mac) or `Ctrl+L` (Windows) to open it

**"The agent doesn't respond"**
→ Make sure you typed `@wcb-agent.md` (with the @ symbol and the file extension)
→ The file must be in `.cursor/rules/` folder

**"I want to start over"**
→ Delete the generated agent files and STATUS.md, AGENTS.md, MYCREW.md
→ Start a new chat with `@wcb-agent.md *rebuild`

---

## File Reference

| File | What It Does |
|------|-------------|
| `wcb-agent.md` | The crew builder agent — your setup assistant |
| `crew-builder.mdc` | Rules for how crews are built (you don't need to edit this) |
| `crew-sop.mdc` | Rules your crew follows (you don't need to edit this) |
| `AGENTS.md` | Your crew's shared knowledge — **edit this to update priorities** |
| `STATUS.md` | Task status board — **check this for updates from your crew** |
| `MYCREW.md` | Your crew summary — **your reference guide** |

---

*Questions? Start a chat with `@wcb-agent.md *help`*
