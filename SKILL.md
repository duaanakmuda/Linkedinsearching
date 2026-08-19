---
name: linkedin-job-hunter
description: Search and rank job opportunities on LinkedIn and public company career pages using the user's CV/profile as the matching source. Search only; never auto-apply, message recruiters, or submit applications.
version: 1.0.0
author: Custom for user
license: MIT
platforms: [windows, linux, macos]
metadata:
  hermes:
    tags: [linkedin, jobs, job-search, recruitment, career, cv]
    category: productivity
---

# LinkedIn Job Hunter

## Purpose

Use this skill when the user wants to find job vacancies, especially on LinkedIn, based on their CV, experience, skills, target role, location, work arrangement, salary expectations, or other job preferences.

This skill is strictly for **job discovery and ranking**.

Never:
- automatically apply to a job;
- submit an application;
- send a recruiter message;
- connect with a recruiter;
- fabricate experience, qualifications, salary history, or application answers;
- claim a job is still open unless the current search provides evidence.

## Core Workflow

### 1. Establish the candidate profile

Use the user's CV/resume if available.

If a CV file is available through the file tools, read it before searching. Extract only information actually present in the CV:
- current/recent job titles;
- years of experience;
- industries;
- responsibilities;
- measurable achievements;
- project-management experience;
- tools/software;
- technical skills;
- certifications;
- education;
- languages;
- location;
- leadership/management scope.

Do not invent missing information.

If no CV is available, use the user's stated profile from the current conversation. If important search constraints are missing, make a reasonable broad search rather than stopping unnecessarily.

### 2. Build search queries and keyword sets

Generate multiple targeted searches rather than one broad query.

The search strategy MUST cover both:
1. **LinkedIn Jobs** — structured job listings.
2. **LinkedIn Posts** — recruiter, HR, hiring manager, company, employee, referral, and hiring-announcement posts.

Build a keyword set from the CV and the user's stated target:
- exact target job title;
- close title variants;
- abbreviations;
- seniority variants;
- role/function keywords;
- industry/domain keywords;
- important skills;
- tools/software;
- location;
- work arrangement;
- hiring phrases;
- recruiter phrases;
- Indonesian and English variants.

Examples of job-title variants:
- `Project Management Officer`
- `PMO`
- `Project Management`
- `Project Coordinator`
- `Project Control`
- `Project Planner`
- `Project Management Specialist`

Examples of hiring/post keywords:
- `we are hiring`
- `we're hiring`
- `hiring`
- `open position`
- `job opening`
- `job opportunity`
- `career opportunity`
- `vacancy`
- `lowongan`
- `loker`
- `dibutuhkan`
- `rekrutmen`
- `join our team`
- `looking for`
- `seeking`
- `talent`
- `urgent hiring`
- `referral`
- `employee referral`

For LinkedIn Jobs, prefer queries that expose current job pages or LinkedIn Jobs URLs.

For LinkedIn Posts, generate searches combining:
- role + hiring phrase;
- role + location;
- role + `hiring`;
- role + `lowongan`;
- role + `loker`;
- role + recruiter/HR terms;
- company + role + hiring;
- skill + hiring;
- industry + role + hiring.

Example queries:
- `site:linkedin.com/jobs "Project Management Officer" Bandung`
- `site:linkedin.com/jobs "PMO" Indonesia`
- `site:linkedin.com/jobs "Project Manager" manufacturing Indonesia`
- `site:linkedin.com/posts "Project Management Officer" hiring`
- `site:linkedin.com/posts "PMO" "we are hiring"`
- `site:linkedin.com/posts "Project Manager" Bandung`
- `site:linkedin.com/posts "Project Management" lowongan Indonesia`
- `site:linkedin.com/posts "PMO" loker`
- `site:linkedin.com/posts "Project Management Officer" recruiter`
- `site:linkedin.com/posts "Project Manager" "join our team"`

Also search public company career pages and major ATS pages when LinkedIn results are incomplete:
- Greenhouse
- Lever
- Ashby
- company career pages

Do not treat a non-LinkedIn result as a LinkedIn listing. Label its source accurately.

### 2A. Return the search keyword pack

When the user asks to search for jobs, also produce a compact **Search Keyword Pack** that can be reused manually in LinkedIn search.

Include:
- **Exact titles**
- **Alternative titles**
- **Skill keywords**
- **Industry keywords**
- **Hiring keywords**
- **Location keywords**
- **Boolean/search combinations**

Example:

**Exact titles**
`"Project Management Officer"`, `"PMO"`

**Alternative titles**
`"Project Coordinator"`, `"Project Control"`, `"Project Planner"`

**Hiring keywords**
`"we are hiring"`, `"open position"`, `"lowongan"`, `"loker"`

**Search combinations**
`"PMO" AND hiring`
`"Project Management Officer" AND Bandung`
`"Project Manager" AND manufacturing`
`"PMO" AND ("lowongan" OR "loker")`

The keyword pack should be derived from the candidate's actual profile and target role, not generic keywords alone.

### 2B. Search LinkedIn Posts as first-class job sources

Treat a relevant LinkedIn post as a potential job lead even when there is no LinkedIn Jobs listing.

For each post lead, extract when available:
- poster name;
- poster role/company;
- company hiring;
- job title;
- location;
- work arrangement;
- posting date;
- application instructions;
- application URL/email;
- whether the post appears to be an original hiring post or a repost;
- source URL.

Classify post leads:
- `DIRECT HIRING POST` — posted by recruiter/HR/hiring manager/company;
- `REFERRAL POST` — employee/referral opportunity;
- `REPOST` — someone sharing another person's/company's opening;
- `UNCLEAR` — source cannot be verified.

Prefer `DIRECT HIRING POST` over reposts when ranking equivalent opportunities.

Never assume a post is an active vacancy just because it contains hiring keywords. Look for evidence such as an application link, explicit vacancy wording, role details, or a recent posting date.

### 2C. Search beyond obvious job titles

Do not search only for the user's preferred title.

Generate adjacent titles that represent substantially similar work. For example, a PMO candidate may also match:
- Project Coordinator
- Project Control
- Project Planner
- Project Management Specialist
- Project Management Analyst
- Project Officer
- PMO Analyst
- PMO Specialist
- Project Operations
- Program Coordinator

Only include adjacent roles when the CV provides a reasonable basis for the match.

### 2D. Keyword discovery from successful results

When a strong job match is found, inspect its job description and extract recurring employer terminology.

Use those terms for additional searches, but do not add them to the candidate profile unless the CV supports them.

Example:
If several strong matches repeatedly use:
`project controls`, `progress monitoring`, `cost tracking`, `schedule management`

then run additional searches using those terms.

This creates an iterative search loop:

CV → initial keywords → search → strong matches → extract employer terminology → expanded search → deduplicate → rank.

Examples:
- `site:linkedin.com/jobs "Project Management Officer" Bandung`
- `site:linkedin.com/jobs "PMO" Indonesia`
- `site:linkedin.com/jobs "Project Manager" manufacturing Indonesia`
- `site:linkedin.com/jobs "Project Management" precast`
- `site:linkedin.com/jobs "PDCA" "Project Management"`

Also search public company career pages and major ATS pages when LinkedIn results are incomplete:
- Greenhouse
- Lever
- Ashby
- company career pages

Do not treat a non-LinkedIn result as a LinkedIn listing. Label its source accurately.

### 3. Search broadly, then deduplicate

Run multiple searches with different title variants.

Deduplicate by:
- company;
- normalized job title;
- location;
- job URL.

If the same job appears on LinkedIn and a company career page, keep one result and record both sources when useful.

### 4. Validate freshness

Prefer listings and posts with:
- a visible posting date;
- recent search-index evidence;
- an accessible job/post page;
- a current application page or clear application instruction.

For LinkedIn Posts, treat recency as especially important because posts can become stale quickly.

Prefer:
- posts within 7 days;
- then posts within 30 days;
- older posts only when the hiring opportunity still has explicit current evidence.

If a post says "we are hiring" but is old and has no current application evidence, mark it `STALE/UNVERIFIED` rather than presenting it as an active opening.

Classify freshness:
- `NEW`: posted within 7 days when a date is available;
- `RECENT`: 8–30 days;
- `OLDER`: more than 30 days;
- `UNKNOWN`: no reliable date.

Never reject an `UNKNOWN` listing solely because its date is unavailable, but flag it.

### 5. Match jobs to the CV

Score every serious candidate on a 0–100 scale.

Use this default weighting:

- 30 points — core role/function match
- 20 points — required experience match
- 15 points — industry/domain match
- 15 points — skills/tools match
- 10 points — seniority match
- 5 points — location/work arrangement match
- 5 points — education/certification/language match

Adjust the weighting when the job description makes one criterion clearly mandatory.

Do not give credit for a requirement merely because it is plausible. Credit it only when supported by the CV or user-provided information.

### 6. Identify gaps

For each high-ranked job, separate:

**MATCHES**
- requirements clearly supported by the CV.

**GAPS**
- requirements explicitly requested by the employer but not demonstrated in the CV.

**UNCERTAIN**
- requirements that cannot be verified from available information.

Do not automatically treat a missing CV item as a lack of ability.

### 7. Rank results

Default ranking:

1. 85–100: Strong match — APPLY
2. 75–84: Good match — CONSIDER
3. 65–74: Possible match — REVIEW
4. below 65: Weak match — SKIP unless the user asks for broader results

These are recommendations, not automatic decisions. The user always decides whether to apply.

### 8. Present concise results

Use this format:

## Top Matches

### 1. [Job Title] — [Company]
- Match: 91/100
- Location: [location]
- Work mode: [remote/hybrid/WFO/unknown]
- Freshness: [NEW/RECENT/OLDER/UNKNOWN]
- Source: [LinkedIn Jobs / LinkedIn Post / Company Career / ATS]
- Link: [job or post URL]
- Post type (if applicable): [DIRECT HIRING POST / REFERRAL POST / REPOST / UNCLEAR]
- Why it matches:
  - ...
  - ...
  - ...
- Gaps:
  - ...
- Recommendation: APPLY

Repeat for the strongest results.

Then provide:

## Search Summary
- Searches performed: [number]
- Strong matches: [number]
- Good matches: [number]
- Review: [number]
- Weak matches: [number]
- Duplicate listings removed: [number]

### 9. Search constraints

Respect explicit user filters:
- location;
- remote/hybrid/WFO;
- minimum salary;
- seniority;
- employment type;
- industry;
- company;
- job title;
- posting recency.

If the user does not specify a constraint, do not invent one.

If the user asks for "jobs for me", infer candidate fit from the CV and current conversation, but keep the search broad enough to surface useful alternatives.

### 10. LinkedIn limitations

LinkedIn may require login or restrict direct access to job pages. If direct LinkedIn access is blocked:
- use search-engine results that point to LinkedIn Jobs;
- use public company career pages as secondary sources;
- clearly state when a listing could not be independently opened;
- never claim successful access to a private/login-only page.

Do not attempt to bypass authentication, CAPTCHA, rate limits, or access controls.

### 11. Application boundary

This skill ends at:
- finding;
- validating;
- comparing;
- ranking;
- linking;
- summarizing job opportunities.

It must not:
- fill application forms;
- click Apply;
- upload the CV;
- send messages;
- contact recruiters;
- submit personal information.

If the user asks to apply, stop the job-search workflow and ask them to review/approve the specific job first.

## Recommended user commands

Examples:

- "Cari lowongan LinkedIn yang cocok dengan CV saya."
- "Cari PMO di Bandung."
- "Cari Project Management Officer di Indonesia, hybrid/remote."
- "Cari 20 lowongan terbaru yang match CV saya."
- "Cari kerja yang cocok dengan pengalaman saya di manufacturing."
- "Cari lowongan dengan match minimal 80%."
- "Cari yang posting maksimal 7 hari terakhir."

## Output quality rules

- Prefer fewer high-quality matches over a long noisy list.
- Always show the actual job URL when available.
- Never fabricate a URL.
- Never fabricate a posting date, salary, location, or requirement.
- Clearly distinguish LinkedIn from company career pages and ATS sources.
- When salary is absent, write `Not stated` rather than estimating.
- When location is absent, write `Unknown`.
- If a job is obviously expired or closed, exclude it unless the user explicitly asks for historical listings.
