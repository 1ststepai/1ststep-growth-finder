# AI Handoff

## Future task start
Before making changes, read `AGENTS.md` first, then `docs/AI_HANDOFF.md`, then only the files directly relevant to the task. Do not scan the whole repo unless those docs are missing or the task genuinely requires broader investigation.

## Current project summary
1stStep Growth Finder is a static founder partner/referral page. It generates partner links to `app.1ststep.ai`, helps build manual search links, saves prospects in browser localStorage, creates a DM review queue, and exports CSVs.

## Architecture overview
- `index.html` contains all markup, styles, and JavaScript.
- Referral links are generated from a normalized partner code.
- Prospect and partner data live only in browser localStorage.
- Signup attribution is captured downstream in the main 1stStep app and `api/notify-signup.js`.

## Common tasks
- Referral change: verify URL params, localStorage handoff, and README end-to-end test.
- Copy/layout change: edit `index.html` only.
- Outreach workflow change: keep it manual and CSV-based.
- Deployment note change: preserve static Vercel settings.

## Common commands
No build command is required. Open `index.html` in a browser or static preview.

## QA checklist
- Partner code normalizes to lowercase URL-safe text.
- Generated URL matches `https://app.1ststep.ai/?ref=partner-code&utm_source=partner&utm_medium=referral&utm_campaign=growth_finder`.
- Test link points to the generated referral URL.
- Prospects save locally and export to CSV.
- No scraping, auto-DM, or auto-posting is introduced.

## Deployment checklist
- Static hosting uses no build command.
- Production domain/alias is confirmed in Vercel before publishing.
- Referral links target the main app, not the Growth Finder page.

## What not to change
- Referral URL format, downstream localStorage keys, GHL tags, payout terms, or manual-outreach-only behavior.
