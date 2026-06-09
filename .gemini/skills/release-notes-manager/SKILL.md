---
name: release-notes-manager
description: Manages retrieval and creation of release notes for KomMonitor components. Use when asked to update release info files, fetch changelogs from KomMonitor GitHub repositories, or create new release documentation pages with specific Jekyll formatting.
---

# Release Notes Manager

This skill guides the process of maintaining release information for the KomMonitor ecosystem.

## Workflow

1.  **Identify Component**: Use [component-sources.md](references/component-sources.md) to find the remote CHANGELOG URL and other release version sources and the local file path to add release notes to.
2.  **Fetch Changelog**: Use `web_fetch` to retrieve the raw CHANGELOG.md and other sources from GitHub.
3.  **Read Local File**: Read the existing documentation to maintain style and identify missing versions.
4.  **Translate & Summarize**:
    *   Translate technical terms to German (e.g., "Feature" -> "Funktion", "Fix" -> "Fehlerbehebung").
    *   Summarize minor commits; highlight architectural changes.
5.  **Apply Changes**:
    *   For existing files, use `replace` for surgical updates.
    *   For new files, use [release-template.md](assets/release-template.md) as a starting point.
6.  **Update Index**: Ensure `docs/releases/index.md` is updated if a new component is added.

## Formatting Rules

- **Jekyll Frontmatter**: Must include `layout`, `title`, `parent: Release Info`, and `nav_order`.
- **Headers**:
    - Use `## Version X.Y.x` for major/minor branches.
    - Use `### X.Y.Z (Datum)` for specific versions.
    - Use `#### Neue Features`, `#### Fehlerbehebungen`, `#### Änderungen` if applicable.
    - Describe changes in bullet points in full sentences with the format: `*   **TOPIC:** Description...` where TOPIC is a concise label for the change.
    - Add `{: .no_toc }` below version headers.
- **TOC**: Always include the TOC block:
  ```markdown
  ## Inhalt
  {: .no_toc .text-delta }

  1. TOC
  {:toc}
  ```
- **Separators**: Use `---` between major version sections.

## Component Map

Refer to [component-sources.md](references/component-sources.md) for all mapping details.
