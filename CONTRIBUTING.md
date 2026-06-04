# Contributing to CyberAtlas

Thank you for considering a contribution. This guide explains what belongs here, how content should be structured, and how to submit it.

---

## What This Repository Accepts

**Welcome contributions:**

- New technical topics following the existing topic format
- Case studies based on documented, publicly reported incidents
- Awareness articles grounded in verifiable facts
- Corrections to factual errors
- Updates to outdated information
- New resources (books, courses, tools) with annotations
- Improvements to existing explanations

**Not accepted:**

- Unverified claims or speculation presented as fact
- Content copied from other sources without attribution
- Malware samples, exploit code, or attack tooling
- Personally identifiable information of any kind
- Content that serves no educational purpose

---

## Before You Start

1. Check the [Roadmap](docs/roadmap.md): your topic may already be planned
2. Search existing content to avoid duplication
3. Read the [Style Guide](docs/style-guide.md): all content must conform to it
4. Choose the right [template](_templates/) for your content type

---

## Content Types and Templates

| Content Type | Template | Where It Goes |
|---|---|---|
| Technical topic | `_templates/topic.md` | `technical/<domain>/` |
| Awareness article | `_templates/awareness-article.md` | `explore/<topic>/` |
| Case study | `_templates/case-study.md` | `case-studies/<category>/` |
| Law / regulation overview | `_templates/law-regulation.md` | `laws-and-privacy/<category>/` |

---

## File Naming Conventions

All files use `kebab-case.md`.

**Pattern:** `descriptive-name.md`

**Examples:**
```
sql-injection-fundamentals.md
gdpr-overview.md
wannacry-2017.md
htb-lame-writeup.md
phishing-awareness.md
```

**Avoid:**
```
SQLinjection.md          ← wrong case format
notes.md                 ← not descriptive
topic1.md                ← meaningless name
MyWriteup_Final_v2.md    ← not kebab-case
```

---

## Required Frontmatter

Every content file must begin with YAML frontmatter:

```yaml
---
title: "Full descriptive title"
section: technical | explore | case-studies | laws-and-privacy | school-cybersecurity | resources
topic: the-parent-topic
date_created: YYYY-MM-DD
last_updated: YYYY-MM-DD
status: draft | review | published
tags: [tag1, tag2, tag3]
---
```

---

## Section Index Files

Each section and subsection has a `README.md` that serves as its index. When you add a new file to a directory, add an entry to that directory's `README.md` table.

---

## Quality Standards

**For all content:**
- Claims must be verifiable: include sources where appropriate
- Write in clear, direct sentences
- Explain *why*, not just *what*
- Do not pad length: shorter and accurate is better than long and vague

**For technical topics:**
- Include practical context, not just definitions
- Explain how the concept connects to real attacks or defenses
- Code blocks must be properly formatted with language identifiers

**For case studies:**
- Use only publicly reported information
- Follow the case study template structure exactly
- Include a "Lessons Learned" section

## Submitting a Contribution

1. Fork the repository
2. Create a branch: `git checkout -b add/topic-name` or `fix/issue-description`
3. Write content using the appropriate template
4. Update the parent directory's `README.md` index
5. Update `CHANGELOG.md` with a brief entry
6. Submit a pull request using the pull request template

---

## Corrections and Issues

To report an error or suggest a topic without writing the content yourself:

- Open an issue using the appropriate issue template
- Be specific: include the file path, the incorrect information, and the correction

---

## Code of Conduct

This repository is an educational resource. All contributions and discussions must remain respectful, factual, and constructive.

Content that promotes illegal activity, shares exploit code for malicious purposes, or targets individuals will not be accepted and will be removed.
