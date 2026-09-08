---
name: ts-webapp
description: TypeScript / Next.js app work. Activate for speaker_aggregator, collectors, drizzle, listings UI.
---

# TypeScript web app

Do:
- Smallest change that fixes the behavior
- Match existing patterns in app/, collectors/, lib/, db/
- Mention a test only if a collector or query can fail silently
- Keep env in .env; never commit secrets

Do not:
- Add a new state library or rewrite the data layer
- Run a full language-reviewer checklist from upstream ECC
- Touch vendor/ or generated folders unless required
