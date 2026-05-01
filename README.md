# 1stStep.ai Growth Finder

Static founder partner page and prospect-finder helper for manual LinkedIn, Reddit, and X outreach.

It includes a local growth-partner console:

- referral code and referral link generator
- DM queue with copy/open workflow
- CSV export for proof/payout review

## Growth Partner Referral System

### Referral URL format

Generated partner links point to the main app, not the public resume landing page:

```text
https://app.1ststep.ai/?ref=partner-code&utm_source=partner&utm_medium=referral&utm_campaign=growth_finder
```

### Partner code generation

Partner codes are normalized before a link is generated:

- Trim whitespace
- Lowercase
- Replace spaces and underscores with hyphens
- Remove unsafe characters
- Collapse repeated hyphens
- Remove leading and trailing hyphens
- Limit to 40 characters

Valid examples:

- `career-coach-sarah`
- `resumehelp101`
- `jobsearchclub`

### Referral capture

When someone lands on `https://app.1ststep.ai` with `?ref=partner-code`, the app normalizes the referral code and stores it in browser local storage so attribution can survive normal navigation before profile save or signup.

The app stores the source referral code in:

```text
firststep_referral_code
```

It also stores the full referral attribution object, including supported UTM fields, in:

```text
1ststep_referral_attribution
```

The referral code is the source of truth.

### Signup notification

When the user saves their profile for the first time, the app sends the normalized referral code to:

```text
/api/notify-signup
```

The API defensively normalizes the referral code again before using it in email or GHL tags.

### GHL tags

When a referral code exists, the GHL contact receives:

```text
partner_referral
ref_partner-code
```

Example:

```text
partner_referral
ref_career-coach-sarah
```

### Admin email

Admin signup emails show:

```text
Referral: partner-code
```

If there is no referral code, the email shows:

```text
Referral: none
```

### Internal verification

- Check the admin signup email for `Referral: partner-code`
- Check the GHL contact tags for `partner_referral` and `ref_partner-code`
- Search GHL for the tag `ref_partner-code`

### Founder partner offer

Current founder partner offer:

```text
$10/month per active referred Job Hunt Pass subscriber for the first 500 eligible partner-referred paid users, for up to 12 months per subscriber
```

Standard rate after the first 500 eligible referred paid users:

```text
20% recurring for 12 months
```

Job Hunt Pass price:

```text
$24.99/month
```

Payouts are reviewed monthly after payments clear. Minimum payout threshold is $50.

### End-to-end test

1. Open an incognito window.
2. Visit:

```text
https://app.1ststep.ai/?ref=testpartner&utm_source=partner&utm_medium=referral&utm_campaign=growth_finder
```

3. Complete profile/signup using a test email.
4. Confirm the admin email says `Referral: testpartner`.
5. Confirm the GHL contact has `partner_referral` and `ref_testpartner`.
6. Visit the app without `?ref=` and complete another test signup.
7. Confirm the admin email says `Referral: none`.
8. Confirm no `partner_referral` tag is added without a referral code.
9. Test invalid partner code input `Sarah Smith!!` and confirm the generated code is `sarah-smith`.
10. Confirm the generated referral link points to `https://app.1ststep.ai`.

## Deploy To Vercel

1. Push this repo to GitHub.
2. In Vercel, create a new project from the repo.
3. Set **Root Directory** to:

```text
growth-finder-public
```

4. Use these settings:

```text
Framework Preset: Other
Build Command: None
Output Directory: .
Install Command: None
```

5. Deploy.

## Notes

- This is a static HTML page.
- It does not scrape LinkedIn, Reddit, or X.
- It does not send DMs or posts.
- Saved prospects live in each user's browser local storage.
- Finder fees are estimated locally. Confirm payout terms separately before recruiting partners.
- For shared team tracking, use the full Streamlit dashboard or add a shared database later.
