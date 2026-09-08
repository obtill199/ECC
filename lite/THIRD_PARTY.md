# Third-party skills

## taste

`lite/skills/taste/` is a shortened operator copy of the MIT-licensed
[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
(`design-taste-frontend`).

Copyright (c) 2026 Leonxlnx. License: MIT. See upstream LICENSE.

The full upstream SKILL.md is large. This repo keeps a directed version so Claude
loads taste on demand without a 87KB always-heavy body. To use the complete
upstream pack instead:

```text
npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"
```

Do not install that *and* every other taste-* variant at once if you care about usage.
