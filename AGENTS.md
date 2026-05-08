# AGENTS.md - 1stStep Growth Finder

## Project purpose
1stStep Growth Finder is a static founder partner/referral page and manual prospect helper. It generates partner referral links, stores a local DM/prospect queue, exports CSVs, and helps a human find/search public opportunities. It does not scrape, auto-DM, or auto-post.

## Production URLs
- Referral target: `https://app.1ststep.ai/`
- Public page production URL is not confirmed in this repo. Check Vercel before naming a live Growth Finder domain.

## Tech stack
- Single static `index.html` with inline CSS and JavaScript.
- Browser localStorage for partner/prospect state.
- CSV export generated in-browser.
- Static Vercel hosting with framework preset `Other` and no build command, per `README.md`.

## Important files/directories
- `index.html` - complete static app.
- `README.md` - referral system, deployment, and end-to-end test notes.
- `docs/AI_HANDOFF.md` - quick architecture/QA handoff.
- `docs/COST_CONTROL.md` - no-scraping/no-paid-tool guidance.

## Do not touch without explicit approval
- Referral URL format:

```text
https://app.1ststep.ai/?ref=partner-code&utm_source=partner&utm_medium=referral&utm_campaign=growth_finder
```

- Referral localStorage keys in the app:

```text
firststep_referral_code
1ststep_referral_attribution
```

- GHL tags created downstream:

```text
partner_referral
ref_<code>
```

- Founder payout terms, Job Hunt Pass price, payout threshold, or beta terms.
- Any rule preventing scraping, auto-DM, or auto-posting.

## Required commands before completion
No build command is required. For changes, open `index.html` locally or in a static preview and manually verify the checklist in `README.md`.

## Environment variable rules
This repo should not require secrets for the static page. Do not add real env vars or secrets to the frontend. If hosting config is added later, document variable names only.

## Safety/security rules
- Do not add scraping, auto-DM, auto-posting, hidden tracking, or credential collection.
- Keep outreach manual and human-reviewed.
- Preserve referral code normalization and URL encoding.
- Do not change payout/commission language without explicit approval.

## Handoff format
```text
Summary:
- What changed and why.

Files changed:
- path: short note

Validation:
- Static page checked: yes/no
- Referral link format checked: yes/no
- CSV export checked: yes/no

Risks / follow-ups:
- Note referral, payout-term, localStorage, or manual-outreach concerns.
```
