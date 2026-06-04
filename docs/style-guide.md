# Style Guide

This guide defines writing conventions, formatting rules, and quality standards for all content in this repository. All contributions must conform to these standards.

---

## Writing Principles

**Be direct.** Start with the point. Do not build up to it.

**Write for understanding, not coverage.** A reader should finish a topic understanding it: not just having encountered it.

**Cite claims.** If you state a fact that is not widely known, link to or name your source.

**Be specific.** Vague writing ("attackers can do many things") is not useful. Name the technique, explain the mechanism.

**Do not pad.** Length is not quality. A 300-word explanation that is clear is better than a 1000-word explanation that restates itself.

---

## Tone

- Professional and direct
- Not academic or jargon-heavy without reason
- Not casual or conversational
- Explain technical terms when first introduced, then use them freely
- Avoid: "basically," "simply," "just," "obviously," "of course"

---

## Frontmatter

Every content file (not README index files) must begin with YAML frontmatter:

```yaml
---
title: "Full descriptive title of the topic"
section: technical
topic: networking
date_created: 2026-01-15
last_updated: 2026-01-15
status: draft | review | published
tags: [dns, networking, protocol]
---
```

Status definitions:
- `draft`: incomplete, not ready for reading
- `review`: content complete, needs verification
- `published`: accurate and complete

---

## Headings

Use a single `#` heading only at the document top (it becomes the page title on GitHub).

Structure content with `##` and `###`. Rarely go deeper than `###`.

```markdown
# Topic Title                    ← document title, one per file
## Major Section                 ← main divisions of the topic
### Subsection                   ← detail within a section
```

Do not skip heading levels (no jumping from `##` to `####`).

Do not use headings to bold a sentence. Use bold for emphasis within paragraphs.

---

## Lists

Use bullet lists for unordered items where sequence does not matter.

Use numbered lists when sequence is meaningful (steps, procedures).

Do not use lists as a substitute for prose when explanation is needed. Three related points that connect to each other belong in a paragraph, not three bullets.

Keep list items parallel in grammatical structure.

---

## Code Blocks

Always specify the language:

````markdown
```bash
nmap -sV 10.0.0.1
```

```python
import socket
```

```text
192.168.1.1   gateway
```
````

Use inline code for:
- File paths: `etc/passwd`
- Commands: `sudo apt update`
- Tool names in context: `nmap`, `Wireshark`
- Values and flags: `--verbose`, `443`

---

## Tables

Use tables for structured comparisons, not for prose that happens to have two columns.

Always include a header row. Align pipes consistently.

```markdown
| Protocol | Port | Purpose |
|---|---|---|
| HTTP | 80 | Unencrypted web |
| HTTPS | 443 | Encrypted web |
```

---

## Links

Use descriptive link text: never "click here" or bare URLs in prose.

```markdown
✅ See the [OWASP Top 10](https://owasp.org/www-project-top-ten/) for the current list.
❌ See the list here: https://owasp.org/www-project-top-ten/
❌ Click [here](https://owasp.org/www-project-top-ten/) for more.
```

For internal links, use relative paths:

```markdown
[Case Studies](../case-studies/)
[Glossary](../docs/glossary.md)
```

---

## Callouts and Notes

Use blockquotes for important notes, warnings, or definitions:

```markdown
> **Note:** This technique requires elevated privileges on the target system.

> **Warning:** Running this command against systems you do not own is illegal.

> **Definition:** A *pivot* is the technique of using a compromised host to attack other systems on its network.
```

---

## Emojis

Emojis are allowed sparingly in README index files for navigation clarity.

Emojis are **not** used in content files.

Permitted in README files: 📚 🔍 🧪 ⚖️ 🏫 🔭 📖 ✅ ⚠️ 🎯 🔒

---

## File Naming

All files use `kebab-case.md`.

Names should describe the content specifically:

```
sql-injection-fundamentals.md        ✅
gdpr-article-17-right-to-erasure.md  ✅
topic.md                             ❌  (not descriptive)
SQLInjection_Notes.md                ❌  (wrong format)
```

---

## Images and Diagrams

Images go in an `assets/` subdirectory within their section.

Reference with a relative path:

```markdown
![Network diagram showing firewall placement](assets/network-diagram.png)
```

Always include descriptive alt text.

Do not embed screenshots of text: transcribe the relevant content as code blocks or prose.

---

## Sources and Attribution

Include a `## Sources` section at the bottom of any file that references external information:

```markdown
## Sources

- [Title of source](https://url.example.com): brief note on what it covers
- Author, *Book Title*, Year
```

For case studies, sources are required. For technical topics, sources are recommended.

---

## What to Avoid

- Pasting content from other sources without transformation and attribution
- Writing "this is important because it is important"
- Opening with "In this article, we will learn about..."
- Ending with "In conclusion, X is very important in cybersecurity"
- Listing tools without explaining what they do or why they matter
- Writing step-by-step instructions without explaining what each step accomplishes
