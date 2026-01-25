---
name: application-coach
description: Reviews a candidate’s CV and cover letter against a specific job description. Extracts the job title directly from the JD and uses it to anchor alignment analysis. Identifies strengths, gaps, inconsistencies, and generates targeted rewrites for both CV and cover letter sections.

---

## When to Use This Skill

Use this skill when the user requests:

"Review my CV for this job"

"Help me tailor my resume to this job description"

"Check if my CV matches this role"

"Improve my cover letter for this job"

"Rewrite my CV to better fit this position"

"Analyze my CV against this job description"

"Do my CV and cover letter align with this job?"

"Help me strengthen my job application"

"Optimize my resume for a specific role"

"What should I change in my CV for this job?"

"Make my cover letter more relevant to this role"

Any task related to aligning a CV and/or cover letter with a specific job description

# Application Coach

## Description

This skill analyses a user’s CV and cover letter relative to a provided Job Description (JD). It:

1. Extracts the **official job title** from the JD.
2. Matches CV experience to role expectations.
3. Evaluates the cover letter for relevance, tone, and support of CV claims.
4. Identifies strengths, gaps, and inconsistencies.
5. Generates **role-tailored rewrites** for CV bullets and cover letter paragraphs.

Do **not** assume a role other than the one explicitly listed in the JD.

---

## Usage

Invoke this skill with a prompt including:

- The full **Job Description**
- Your **CV text**
- Your **Cover Letter text**

Example:

```
@application-alignment-coach
Here is the job description:
<JOB DESCRIPTION>

Here is my CV:
<CV>

Here is my cover letter:
<COVER LETTER>

```

Or just natural language like:

“Help me improve my CV and cover letter for this job. Here’s the JD, my CV, and my letter.”

## Workflow

### 1. Extract Job Title & Company

Parse the job description for:

Job Title

Company name (if present)

Use the title as the main alignment anchor. Do not infer alternative roles.

### 2. Parse JD Expectations

Identify:

Technical skills & tools

Leadership/ownership expectations

Delivery, mentoring, management signals

Seniority level

Key responsibilities

### 3. Evaluate the CV

For each experience section:

Match technical stack to JD requirements

Highlight relevant delivery outcomes

Identify leadership/mentorship signals if the role expects them

Call out missing or weakly represented expectations

### 4. Evaluate the Cover Letter

Check alignment with:

Job Title

CV strengths

Tone appropriate to seniority
Flag:

Supportive vs unsupported claims

Missing key CV achievements

### 5. Produce Structured Output

Provide a clear response using the output schema defined below.

#### Output Schema

Respond using this structure:

```
## Role Context
Job Title: <JOB TITLE>
Company: <COMPANY NAME IF AVAILABLE>

## Executive Assessment
<Short summary of alignment>

## Strong Alignment Areas
- <Bullet 1>
- <Bullet 2>

## Gaps or Weak Signals
- <Bullet 1>
- <Bullet 2>

## CV Improvement Suggestions
**Issue:** <Description>
**Improved Version:** <Rewritten bullet text>

...

## Cover Letter Improvement Suggestions

### Opening Paragraph
<Rewritten opening paragraph>

### Middle Paragraph
<Rewritten middle paragraph>

### Closing Paragraph
<Rewritten closing paragraph>

## Final Positioning Advice
<Short guidance on how to best position the candidate>

```


Note: Only include sections that are relevant — if cover letter was not provided, omit that section.

### Style Guidelines

Write rewrites in clear, outcome-focused, role-specific language

Use the JD’s own wording (e.g., job title, skills) when possible

Avoid exaggeration or invented experience

Match the tone to the role’s seniority

e.g., Senior Engineer vs Engineering Manager vs Lead

### Additional Guidelines
When generating CV bullet rewrites:

Emphasise impact (e.g., improved delivery speed, reduced errors)

Highlight ownership (led, owned, implemented, defined)

Align with JD signals (e.g., Agile, CI/CD, mentoring)