---
name: release-notes-manager
description: Manages retrieval and formatting of release notes for KomMonitor components. Use this skill whenever the user wants to update release info, add version history, fetch changelogs from a KomMonitor GitHub repository, document a new release, or keep the docs up to date with a new component version — even if they just say something like "update the data management docs" or "add the latest release" or "what's new in the importer". Always use this skill for any KomMonitor release documentation task.
---

# Release Notes Manager

This skill maintains the release documentation for the KomMonitor ecosystem on the GitHub Pages site.

## References

- **Component sources** (GitHub URLs + local file paths): `references/component-sources.md` — read this first to identify the right CHANGELOG URL and local docs file.
- **Jekyll page template** (for new release pages): `assets/release-template.md`
- **RSS feed data** (one entry per release): `docs/_data/releases.yml` — must be updated whenever a new version is documented.

## Workflow

1. **Identify the component** — read `references/component-sources.md` to find:
   - The raw CHANGELOG URL on GitHub
   - Any additional sources (e.g. version info templates)
   - The local file to update (`docs/releases/<component>.md`)

2. **Fetch the changelog** — retrieve the raw CHANGELOG.md from GitHub. Also fetch any "Other Sources" listed for the component.

3. **Read the local file** — understand which versions are already documented so you only add what's missing.

4. **Translate & summarize** — rewrite the changelog content for a German-speaking end-user audience:
   - Translate technical terms: "Feature" → "Funktion", "Fix" → "Fehlerbehebung", "Breaking change" → "Inkompatible Änderung", etc.
   - Summarize minor commits; give prominent treatment to new features and architectural changes.
   - Explain *what changed and why it matters*, not the implementation details of *how*.

5. **Format the content** — follow the Formatting Rules below and use `assets/release-template.md` as the reference structure.

6. **Apply changes** — for existing files, insert new version sections at the top (newest first) with surgical edits. For new components, start from the template.

7. **Update the RSS feed data** — prepend a new entry to `docs/_data/releases.yml` for each newly documented version:

   ```yaml
   - component: "Component Name"
     version: "MAJOR.MINOR.PATCH"
     date: YYYY-MM-DD
     page: "/releases/<slug>.html"
     anchor: "<computed-anchor>"
     summary: "One-sentence German summary of the most notable change"
   ```

   **Anchor computation:** take the heading text (e.g. `1.1.3 (Juli 2026)`), remove `.`, `(`, `)`, `&`, `,`, lowercase, replace spaces with hyphens → `113-juli-2026`. Hyphens already in the text stay (a range like `1.0 - 1.1` becomes `10---11`).

   **Date:** use the ISO date of the release. For month-only dates (e.g. "Juli 2026") use the 1st of that month. For date ranges, use the end date.

   **Also update** the `date:` frontmatter on the release page if the new version's date is more recent than the current value.

8. **Update the index** — if a new component page was created, add an entry to `docs/releases/index.md`.

## Formatting Rules

Structure of a release notes page:

```
## Version MAJOR.MINOR.x          ← one section per minor series
### MAJOR.MINOR.PATCH (DATE)      ← one subsection per patch
{: .no_toc }
#### Neue Features                 ← only if applicable
{: .no_toc }
##### TOPIC:                       ← concise label; group related items together
{: .no_toc }
Full sentence describing the feature and why it matters to users.

#### Fehlerbehebungen              ← only if applicable
{: .no_toc }
#### Änderungen                    ← only if applicable
{: .no_toc }

---                                ← separator between major version sections
```

- List `## Version` sections in **descending order** (most recent first).
- Document **all minor versions** — if a version is missing from the local file, add it with whatever information is available in the changelog.
- A `### PATCH` heading may **span a range** (e.g. `### 3.4.0 - 3.4.3 (Juli 2025 - März 2026)`) when the versions share the same features/fixes and were released close together. Otherwise use separate subsections.
- Add `{: .no_toc }` after **every heading** (required by the Just the Docs Jekyll theme to suppress TOC entries).
- Date format: German month names or day-first numeric (e.g. "01. Juni 2026" or "Juni 2026").
