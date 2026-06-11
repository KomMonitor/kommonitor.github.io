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
    * Translate technical terms to German (e.g., "Feature" -> "Funktion", "Fix" -> "Fehlerbehebung").
    * Summarize minor commits; highlight new features and architectural changes.
    * Release infos should be written for a end user audience, not developers. Focus on what has changed and why it matters, not on the technical details of how it was implemented.
5.  **Format Content**: Ensure the new release notes follow the Jekyll formatting and structure as shown in the [release-template.md](assets/release-template.md) and described in the Formatting Rules below. This includes proper headers, TOC, and grouping of changes under topics.
5.  **Apply Changes**:
    *   For existing files, use `replace` for surgical updates.
    *   For new files, use [release-template.md](assets/release-template.md) as a starting point.
6.  **Update Index**: Ensure `docs/releases/index.md` is updated if a new component is added.

## Formatting Rules
- Use the provided [release-template.md](assets/release-template.md) as a reference for formatting.
- List all `## Version {{MAJOR.MINOR.x}}` sections in descending order, starting with the most recent release. 
- Include all minor versions as seperate section. Also older versions. If they are not yet documented, add them with the available information. This ensures a complete release history.
- `### {{MAJOR.MINOR.PATCH}} ({{DATE}})` can include multiple versions (e.g. ### 3.4.0 - 3.4.3 (Juli 2025 - März 2026)), if they relate to the same features or fixes and were released in a close timeframe. Otherwise, create separate sections for each version.
- Add `#### Neue Features`, `#### Fehlerbehebungen`, `#### Änderungen` only if applicable.
- Under `##### {{TOPIC}}` describe features, fixes and changes in full sentences.
- `{{TOPIC}}` is a concise label for features, fixes and changes, which can be grouped under these topics for better readability if they relate to the same topic..
- Use `---` as separator between major version sections.


## Component Map

Refer to [component-sources.md](references/component-sources.md) for all mapping details.
