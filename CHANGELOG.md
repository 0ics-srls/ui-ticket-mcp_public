# Changelog

All notable changes to this project are documented here.

## [1.1.2] - 2026-02-25

### Added
- README for ui-ticket-core and ui-ticket-panel npm packages
- Website and GitHub links across all package READMEs

### Fixed
- PyPI project URLs now point to public repo and landing page

## [1.1.1] - 2026-02-25

### Added
- Version badge in review panel header showing current library version

## [1.1.0] - 2026-02-25

### Added
- Version check with auto-update notification toast in UI
- `GET /api/version` endpoint for runtime version queries
- Deploy protocol with version checklist

### Changed
- Batch marker positioning with GPU-accelerated transforms
- Surgical render, tag borders, default "general" filter, better selectors
- Tarball packaging to avoid Vite cache issues

### Fixed
- Widget blink: debounced render, parallel refresh, atomic DOM swap
- Clamp badge position to visible portion of element in viewport
- Live rect X-fix for marker positioning

### Packages
- `ui-ticket-mcp` 1.1.0 on [PyPI](https://pypi.org/project/ui-ticket-mcp/)
- `ui-ticket-panel` 1.1.0 on [npm](https://www.npmjs.com/package/ui-ticket-panel)
- `ui-ticket-core` 1.1.0 on [npm](https://www.npmjs.com/package/ui-ticket-core)

## [1.0.1] - 2026-02-24

### Added
- Standalone CDN bundle (`dist/bundle.js`, 77KB) for plain HTML projects - no npm or bundler needed
- CDN usage instructions in `get_setup_guide()` MCP tool
- Landing page at [0ics-srls.github.io/ui-ticket-mcp](https://0ics-srls.github.io/ui-ticket-mcp)

### Usage (CDN - no bundler)

```html
<script type="module" src="https://unpkg.com/ui-ticket-panel/dist/bundle.js"></script>
<review-panel api-url="http://localhost:3200/api"></review-panel>
```

### Packages
- `ui-ticket-mcp` 1.0.1 on [PyPI](https://pypi.org/project/ui-ticket-mcp/)
- `ui-ticket-panel` 1.0.1 on [npm](https://www.npmjs.com/package/ui-ticket-panel)
- `ui-ticket-core` 1.0.1 on [npm](https://www.npmjs.com/package/ui-ticket-core)

## [1.0.0] - 2026-02-24

### Highlights
- First stable release
- Universal Web Component (`<review-panel>`) - works in any framework or plain HTML
- 10 MCP tools for AI agents to read, resolve, and manage UI reviews
- Rich annotation system with element metadata capture
- SQLite database with WAL mode for concurrent access

### Features

**Browser UI**
- Floating review panel with Open / Resolved / All tabs
- Click-to-annotate: press Alt+A, click any element, attach a review
- Multi-select drag to annotate regions
- Numbered badge markers on annotated elements (colored by status)
- Stacked badges for 3+ reviews on same element (gradient shows open/resolved ratio)
- Tag system: general, bug, suggestion, question
- Full-text search and tag filtering
- Threaded replies
- Keyboard shortcuts: Alt+A (annotate), Ctrl+Enter (submit), Escape (close)

**Annotation Metadata**
- Element name, CSS selector, full DOM path
- Bounding box, computed styles, CSS classes
- Nearby text, sibling context, accessibility info
- Gives AI agents precise context about what you pointed at

**MCP Tools (10)**
- `get_pending_work()` - agent's todo list
- `get_annotated_reviews()` - reviews with full element metadata
- `get_review_summary()` - per-page overview
- `get_reviews()` - list with status, tags, context
- `find_source_file_tool()` - locate source files by page ID
- `resolve_review()` / `reopen_review()` - manage review status
- `batch_resolve()` - resolve all on a page
- `add_review()` - create reviews programmatically
- `get_setup_guide()` - full setup instructions

**REST API**
- CRUD endpoints for reviews under `/api`
- Threaded replies support
- Status and tag filtering
- CORS enabled for all origins

**Architecture**
- Single Python process: MCP (stdio) + REST API (HTTP)
- SQLite with WAL mode, auto-created at `{PROJECT_ROOT}/.reviews/`
- Zero-install via `uvx ui-ticket-mcp`

### Packages
- `ui-ticket-mcp` 1.0.0 on [PyPI](https://pypi.org/project/ui-ticket-mcp/)
- `ui-ticket-panel` 1.0.0 on [npm](https://www.npmjs.com/package/ui-ticket-panel)
- `ui-ticket-core` 1.0.0 on [npm](https://www.npmjs.com/package/ui-ticket-core)
