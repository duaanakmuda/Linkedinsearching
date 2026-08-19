# LinkedIn Job Hunter

Custom Hermes Agent skill for searching and ranking job opportunities.

## What it does

- Searches LinkedIn Jobs
- Searches LinkedIn Posts from recruiters, HR, hiring managers, companies, and referrals
- Generates search keywords from the candidate CV/profile
- Expands searches using alternative job titles and employer terminology
- Deduplicates results
- Checks freshness
- Matches jobs against the CV
- Produces a 0–100 match score
- Identifies matches, gaps, and uncertainties
- Ranks opportunities for review

## Scope

Search and ranking only.

This skill does **not**:
- automatically apply to jobs
- submit applications
- message recruiters
- connect with recruiters
- bypass LinkedIn authentication, CAPTCHA, or rate limits

## Hermes installation

Clone this repository into the Hermes skills directory:

```bash
git clone https://github.com/USERNAME/linkedin-job-hunter.git ~/.hermes/skills/productivity/linkedin-job-hunter
```

Then verify:

```bash
hermes skills list
```

## Files

- `SKILL.md` — Hermes skill definition and workflow
