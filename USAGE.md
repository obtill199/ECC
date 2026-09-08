# How to use this harness without burning usage

Goal: make Claude Code and ChatGPT follow a tight loop on *your* projects, without loading a 20k-token toolbox every session.

## Cost rules (non-negotiable)

1. Default model: **Sonnet**. Not Opus. Opus only for a one-shot architecture decision you cannot get from Sonnet.
2. Grunt work (renames, CSS tweaks, list formatting, commit messages): **Haiku** or ChatGPT-4.1-mini / GPT-5 Instant if that is what your plan offers.
3. One task per session. When the task is done, start a new chat. Long chats are what explode bills.
4. Do not enable MCP servers unless you need a browser or GitHub for that exact task.
5. Do not install official ECC (`ecc@ecc`) and this lite pack at the same time.
6. Do not turn hooks on. Hooks spend tokens you never see in the chat.
7. Ask for a short plan first. Approve it. Then implement. Do not let the model roam.

## Claude Code — first-time setup

### 1. Prerequisites

- Claude Code CLI 2.1+
- Node 18+ only if you already have it; you do not need npm for this lite pack
- Git

### 2. Add this repo as a marketplace and install only the lite plugin

Inside Claude Code:

```text
/plugin marketplace add https://github.com/obtill199/ECC
/plugin install lite@tilly-ecc
```

If Claude asks about hooks, choose **disabled** / **minimal**. The plugin default is hooks off.

### 3. Install the one always-on rule

Claude plugins do not always distribute rules. Do this once:

```bash
mkdir -p ~/.claude/rules
curl -fsSL https://raw.githubusercontent.com/obtill199/ECC/main/lite/rules/lean.md -o ~/.claude/rules/tilly-lean.md
```

### 4. Pin cheap models in Claude Code settings

In `~/.claude/settings.json` (create the file if needed):

```json
{
  "model": "sonnet",
  "env": {
    "CLAUDE_CODE_SUBAGENT_MODEL": "haiku"
  }
}
```

If you already have settings, merge those two keys. Do not paste a giant official ECC settings block.

### 5. Per-project boot (do this in each repo you care about)

From the project root (`chad-chimney`, `speaker_aggregator`, etc.):

```bash
curl -fsSL https://raw.githubusercontent.com/obtill199/ECC/main/lite/AGENTS.md -o AGENTS.md
curl -fsSL https://raw.githubusercontent.com/obtill199/ECC/main/lite/CLAUDE.md -o CLAUDE.md
```

Only those two files. Do not copy `skills/`, `agents/`, or `hooks/` from the repo root into your projects.

## Claude Code — daily usage

Open the project, then use one of three commands. That is the whole system.

### `/lite:plan` — before you write code

Use when the change is more than a one-file tweak.

Say:

> /lite:plan Add a sweeping specials block to the Chad Chimney homepage and a matching contact CTA.

You should get:

- 3–7 steps
- files that will change
- what will *not* be touched
- a usage note (Sonnet vs Haiku)

If the plan is wrong, correct it in one sentence. Do not let it start coding yet.

### `/lite:ship` — implement the approved plan

> /lite:ship Do steps 1–4 only. Stop when the homepage and services page match.

Keep the scope in the prompt. "Only" and "stop when" save money.

### `/lite:review` — after it writes

> /lite:review Check the diff for broken links, mobile CSS, and anything that would confuse a Wichita homeowner.

Do not request a security audit, TDD cycle, and architecture review on a five-file HTML site.

### Manual prompts that work if you skip slash commands

```text
Follow AGENTS.md. Plan only. No code.
```

```text
Follow AGENTS.md. Implement the plan we just agreed. Do not expand scope.
```

```text
Follow AGENTS.md. Review the diff. Critical issues only.
```

## Which skill fires for which repo

| You are in | Skill Claude should use |
| --- | --- |
| `chad-chimney` | `html-local-service` |
| `speaker_aggregator` | `ts-webapp` |
| Fantasy / props / slates | `sports-research` |
| Resume / ClearanceJobs / applications | `job-search` |
| A furniture photo or Marketplace listing | `furniture-flip` |
| Any of the above when the session is getting long | `usage-guard` |

You can name the skill in the prompt:

> Use skill html-local-service. Rewrite the inspections page H1 and the phone CTA only.

## ChatGPT — setup and usage

ChatGPT does not load Claude plugins. Give it the short instruction file.

### Custom GPT or Project instructions

1. Create a Project (or Custom GPT) called **Tilly Lite**.
2. Paste the contents of `lite/CHATGPT.md` into Project instructions / GPT instructions.
3. Upload `lite/AGENTS.md` as a project file.
4. Upload only the files for the *current* task (one HTML page, one resume, one listing). Not the whole repo.
5. Model: GPT-5 Instant / 4.1 / mini for drafts. Use the stronger thinking model only for a plan you will reuse.

### ChatGPT daily loop

Same three moves as Claude:

1. "Plan only. Max 8 bullets. Files + risks."
2. "Implement that plan. No extra files."
3. "Review. Critical only."

Start a new chat per job. Paste AGENTS.md once if the Project does not already include it.

### Codex / ChatGPT coding agent

If you use Codex in a checkout, the `AGENTS.md` copied into that repo is enough. Do not add MCP. Do not add hooks.

## Session recipes (copy/paste)

### Local service site

```text
Use skill html-local-service.
Plan a change to contact.html so the form and phone number are impossible to miss on mobile.
Do not restyle the whole site.
```

### Speaker aggregator

```text
Use skill ts-webapp.
Plan a collector fix for duplicate listings. Show the files and the test you would add.
No code until I say ship.
```

### Fantasy / sports

```text
Use skill sports-research.
Build a short draft board note for pick 11, 2026 Premiership. Evidence first. No guaranteed-win language.
```

### Job packet

```text
Use skill job-search.
Score this JD against my evidence bank. If fit >= 70, draft a truthful resume rewrite. Flag gaps. Do not invent clearance or tools.
```

### Furniture

```text
Use skill furniture-flip.
Here is the photo. Assess construction, recommend one profit-max finish, give steps and a listing title.
```

## When to start a new chat

Start a new session when any of these is true:

- the current task shipped
- you switched repos
- the model is repeating itself or rereading the same files
- you already had two review passes

A new chat plus `AGENTS.md` is cheaper than a 200-message thread.

## What not to do

- Do not run `npx ecc-universal` against this repo.
- Do not `/plugin install ecc@ecc` from affaan-m and this lite plugin together.
- Do not copy `rules/typescript` or other upstream rule packs into `~/.claude/rules`.
- Do not ask for 80% coverage on a static chimney site.
- Do not leave the official 68-agent catalog enabled. If Claude lists dozens of agents at session start, the wrong plugin is installed.
