# Templates

Templates for all content types in this repository.

Use the appropriate template when creating new content. Templates enforce consistency and ensure all required sections are present.

---

## Available Templates

| Template | Use For | Section |
|---|---|---|
| [topic.md](topic.md) | Technical concepts, tools, protocols | `technical/` |
| [awareness-article.md](awareness-article.md) | Broader security and privacy topics | `explore/` |
| [case-study.md](case-study.md) | Real-world incident analysis | `case-studies/` |
| [law-regulation.md](law-regulation.md) | Legal frameworks and compliance | `laws-and-privacy/` |

---

## How to Use a Template

1. Copy the relevant template file to the appropriate section directory
2. Rename it using `kebab-case.md` naming convention
3. Fill in the frontmatter fields
4. Replace all placeholder text with actual content
5. Delete sections that are genuinely not applicable
6. Add the file to the parent directory's `README.md` index
7. Update `CHANGELOG.md`

---

## Template Conventions

- Sections marked with *(optional)* or instructions like "optional section" can be removed
- Do not leave placeholder text (like `[Description here]`) in published files
- The `status` frontmatter field must be changed from `draft` before a file is considered published
- All code blocks must have a language identifier

---

→ [Back to Main Index](../README.md) · [Style Guide](../docs/style-guide.md)
