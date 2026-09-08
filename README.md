# Tilly ECC Lite

Personal, low-token harness for Tilly (`obtill199`).

This repository started as a copy of [affaan-m/ECC](https://github.com/affaan-m/ECC) (MIT, Copyright 2026 Affaan Mustafa). The upstream tree is still in git history. **Do not install the full upstream plugin from this repo.** Use the lite pack only.

## What this is for

Directed at work you actually do:

- Local service sites (`chad-chimney`: HTML, CSS, JS, SEO, leads)
- TypeScript web apps (`speaker_aggregator`: Next.js, collectors, listings)
- Sports research and fantasy (`Fantasy-Football`, props, slates)
- Job search and resume tailoring (cleared / intel / data integrator lanes)
- Furniture flipping and Marketplace listings

Removed from the *active* load path:

- Go, Rust, Java, Kotlin, C++, F#, Perl, Django, PyTorch, RAG, enterprise orchestration
- 68-agent / 286-skill / 94-command discovery catalog
- Always-on hooks, MCP servers, GateGuard, continuous-learning daemons
- 80% coverage and mandatory TDD rules

Active surface (what Claude/ChatGPT should see):

| Kind | Count | Paths |
| --- | ---: | --- |
| Agents | 3 | `lite/agents/` |
| Skills | 7 | `lite/skills/` |
| Commands | 3 | `lite/commands/` |
| Rules | 1 | `lite/rules/lean.md` |
| Hooks | 0 | disabled |

## Install

Read [USAGE.md](USAGE.md). Short version:

```text
/plugin marketplace add https://github.com/obtill199/ECC
/plugin install lite@tilly-ecc
```

Then copy `lite/rules/lean.md` into `~/.claude/rules/tilly-lean.md` and use **Sonnet** for real work, **Haiku** for grunt.

Do not also run `npx ecc-universal` or install official `ecc@ecc` on top of this.
