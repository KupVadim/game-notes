# AI Coding Agent Instructions for game-notes

## Project Overview

**game-notes** is a MkDocs-based documentation website for gaming knowledge and guides, primarily focused on Assetto Corsa Rally. The project is deployed as a static site and uses Material theme for documentation.

- **Language**: Russian (Russian UI and content)
- **Stack**: MkDocs + Material Theme + Python markdown extensions
- **Content Structure**: `docs/Games/{GameName}/{topical-files}.md`
- **Build Tool**: MkDocs CLI

## Architecture & Content Organization

### Directory Structure
```
docs/
├── index.md              # (Empty) homepage
├── Games/
│   ├── .pages            # Navigation order config
│   └── Assetto Corsa Rally/
│       ├── Assetto_Corsa_Rally_Community_QA.md
│       ├── Assetto_Corsa_Rally_VR_UEVR_Problems_and_Solutions.md
│       └── VR Settings.md
mkdocs.yml               # Site config (theme, extensions, plugins)
```

### Key Configuration: `mkdocs.yml`

The site uses:
- **Theme**: `material` with Russian language (`language: ru`)
- **Dark/Light Mode**: User-selectable via toggle
- **Markdown Extensions**: 
  - `pymdownx.superfences`, `pymdownx.highlight` (code blocks with line numbers)
  - `pymdownx.emoji` (icon support via Twemoji)
  - `admonition`, `pymdownx.details` (collapsible sections)
  - `attr_list` (CSS class assignment)
  - `md_in_html` (mixed markdown/HTML)
- **Plugins**: `glightbox` (image lightbox), `awesome-pages` (nav ordering via `.pages` files), `search`

## Content Patterns & Conventions

### Markdown Structure

1. **Video Embeds**: Use full HTML iframe blocks with custom styling:
   ```html
   <div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;border-radius:8px;">
     <iframe src="https://www.youtube.com/embed/{VIDEO_ID}" ...>
     </iframe>
   </div>
   ```

2. **Admonitions** (callout boxes):
   ```markdown
   !!! note
       Text here
   
   !!! warning
       Critical warning
   
   !!! tip
       Helpful hint
   
   !!! info "Источник"
       Source attribution
   ```

3. **Formatting**: Use inline formatting (`**bold**`, `_italic_`) and code fences with language highlighting.

### Language & Localization

- **All content is in Russian** (UI + documentation text)
- Video titles, links, and external references use English URLs as needed
- Use term consistency (e.g., "Early Access" vs локalization)

## INBOX Processing Workflow (Agent-Automated)

Files placed in `docs/INBOX/` are automatically processed after each commit. **Agent Processing Checklist:**

1. **Validate Format**: Check for proper MkDocs compliance:
   - Headers use `##` or `###` (not `#` at top)
   - Video embeds use responsive HTML iframe format (see Content Patterns)
   - Admonitions properly formatted with `!!!` syntax
   - Russian language throughout (if content is Russian)
   - Code blocks have language tags

2. **Enhance with MkDocs Features**:
   - Add `!!! info "Источник"` for source attribution
   - Use `!!! note`, `!!! warning`, `!!! tip` for important sections
   - Add line numbers to code blocks: ` ```python linenums="1" `
   - Use collapsible sections with `??? note "Title"`

3. **Determine Destination**:
   - Files about Assetto Corsa Rally → `docs/Games/Assetto Corsa Rally/{FileName}.md`
   - Use filename pattern: `Game_Topic_Description.md` (CamelCase_with_underscores)

4. **Commit & Move**:
   - Move file to correct location
   - Commit with message: `Process INBOX: Move {file} → Games/{GameName}/{file}`
   - Delete from INBOX

5. **Validation Before Commit**:
   - Run: `mkdocs build --strict` (must pass with no errors)
   - Check rendered output at `site/` folder

### Adding New Game Section

1. Create folder: `docs/Games/{GameName}/`
2. Add `.pages` file for navigation order (optional):
   ```yaml
   nav:
     - Overview: overview.md
     - Guides: guides.md
   ```
3. Create `.md` files following existing patterns (headers, admonitions, embeds)

### Local Preview

```bash
mkdocs serve
# Opens http://127.0.0.1:8000/
```

### Build Static Site

```bash
mkdocs build
# Output: site/
```

## File Naming & Conventions

- **CamelCase_with_underscores** for file names (e.g., `Assetto_Corsa_Rally_Community_QA.md`)
- **Start with game/section name** to organize content naturally
- **No spaces in filenames** (use underscores)

## External Integrations

- **YouTube**: Full HTML embeds with official video IDs (no short URLs)
- **Search**: Built-in Material theme search (indexes all markdown)
- **Theming**: Material palette supports user OS preference detection

## Important Notes for Contributors

- Avoid modifying `mkdocs.yml` unless adding plugins or theme features
- Use `.pages` files instead of manually editing nav in `mkdocs.yml`
- Test locally with `mkdocs serve` before committing
- Keep markdown files under 500 lines for readability (split into multiple files if needed)
- Preserve Russian language in all UI and main content
- Use emoji sparingly; prefer Material icons via `material/icon-name` syntax where supported

## INBOX Processing Workflow (Copilot Agent-Driven)

The `.github/workflows/process-inbox.yml` workflow automatically triggers when:
- Files are added/modified in `docs/INBOX/`
- The workflow file itself is modified

**Workflow actions:**
1. Detects files in `docs/INBOX/`
2. Creates a GitHub Issue labeled `agent-task` with processing checklist
3. **Copilot Coding Agent can be invoked on the issue** to process files

### How to Use (Option A - Manual Agent Invocation)

1. **Push file to INBOX**: Commit markdown file to `docs/INBOX/`
2. **Workflow creates Issue**: GitHub Actions creates an issue with file list and checklist
3. **Invoke Copilot Agent**: Open GitHub Issue and ask Copilot agent to process it
   - In VS Code with GitHub Copilot, you can reference the issue or use the Copilot Chat
   - Agent will have complete context from `.github/copilot-instructions.md`

**Agent responsibility when processing INBOX files:**
1. Enhance markdown with MkDocs features (admonitions, collapsible sections, etc.)
2. Validate with `mkdocs build --strict`
3. Move formatted file to correct destination (`docs/Games/{GameName}/`)
4. Delete from INBOX
5. Commit with clear message: `Process INBOX: Move {file} → Games/{GameName}/{file}`
6. Close the issue once processing is complete

## Quick Reference: Useful mkdocs Commands

```bash
mkdocs new {site_name}           # Create new site
mkdocs build                     # Build to site/
mkdocs serve                     # Local dev server
mkdocs build --strict            # Catch all errors
```
