# Claude Code Harness

## Prime Directive
Use the least context necessary. Do not scan the whole repo unless explicitly asked.

## Token Discipline
1. Read this file and `docs/AI_MEMORY.md` first.
2. Use search/grep before opening large files.
3. Identify the smallest relevant files before editing.
4. Prefer surgical patches over rewrites.
5. Do not paste full files back unless requested.
6. Stop after one logical fix and report exactly what changed.

## Required Workflow
1. Restate the task in one sentence.
2. Locate only relevant files.
3. Explain the smallest safe change.
4. Patch only those files.
5. Run relevant verification.
6. Add a short session retro for non-trivial work.

## Verification
Inspect available scripts before choosing commands. Common checks:

```bash
npm run lint
npm run test
npm run build
```

## Safety
Never expose or commit secrets. Do not read or print `.env*` files. Do not run destructive git commands. Do not deploy unless explicitly asked.

## Repo Context
This repo belongs to Evan Pancis and supports the 1stStep.ai Growth Finder / partner funnel. Preserve clear partner-program positioning, referral tracking context, and conversion-focused copy.

Important URLs:
- Partner funnel: https://1ststep-growth-finder.vercel.app/
- Partner landing: https://partners.1ststep.ai/
- Resume landing page: https://resume.1ststep.ai/
- App: https://app.1ststep.ai/

## Communication Style
Assume the owner is a novice coder. Give copy/paste-ready instructions, clear risk flags, and concrete next steps.
