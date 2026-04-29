# Copilot Instructions — lucamilan.eu

## Project Overview

This is a static GitHub Pages site — Luca Milan's professional landing page and CV. No build system, framework, or CI pipeline exists. All content is hand-authored HTML with inline CSS, deployed directly from the repository root (via `CNAME`).

## Architecture & File Structure

**Entry points:**
- `index.html` — English version (dark theme, navy/cyan palette)
- ~~`index_.html`~~ — Archived to `.old/` (was Italian version; no longer maintained)

**Assets (relative paths required for GitHub Pages):**
- `icons/` — favicons and site manifest
- `cv/` — CV or resume documents
- `md/` — markdown reference materials (e.g., `luca-milan-cv.md`); not actively synced to HTML
- `bg.jpeg`, `lm.jpg` — profile images
- `*.pdf` — CV PDFs (linked from HTML)

**Structure notes:**
- No `package.json`, no `Gemfile`, no build configuration
- Each HTML file is self-contained with inline `<style>` blocks
- Styles use CSS custom properties (variables) defined in `:root`
- All links must use relative paths (`icons/`, `cv/`, etc.) — no domain-relative paths

## Key Conventions

**HTML:**
- Semantic markup (proper heading hierarchy, sectioning elements, ARIA where needed)
- Inline CSS only — no external stylesheets
- Favicon links point to `icons/` with multiple sizes
- Language attribute on `<html>` tag (`lang="en"` or `lang="it"`)

**CSS:**
- Define color palette in `:root` at the top of `<style>`
- Use CSS custom properties throughout (e.g., `color: var(--navy)`)
- Relative units (em, rem) preferred for responsive scaling
- Flexbox and Grid for layout
- Mobile-first: media queries for larger breakpoints

**Assets:**
- All asset references use relative paths: `icons/filename.png`, `bg.jpeg`, `lm.jpg`, `luca-milan-cv-latest.pdf`
- Verify assets exist in the repository before adding references
- Note: only `index.html` is currently maintained; the Italian variant (archived) is in `.old/`

## Playwright MCP for Browser Checks

Copilot can use Playwright MCP to automate browser verification — clicking links, scrolling, and verifying asset paths. This is useful for validating responsive layout changes and link functionality before manual review.

## Manual Verification (No Automated Tests)

Before committing changes:

1. **Links & Anchors:** Click internal anchors (nav links) and verify smooth scrolling; test external links if present
2. **Asset Paths:** Verify all `href` and `src` paths resolve correctly
3. **PDFs:** Test download links for CV and document files
4. **Icons:** Confirm favicon and favicon variants load (browser tab, bookmarks)
5. **Responsive Layout:** Test on mobile (< 768px), tablet (768px–1024px), and desktop (> 1024px)
6. **CSS Variables:** Ensure all color properties reference defined variables; test light/dark contrast ratios
7. 

## Common Edits

**Adding a new section:**
- Add HTML with semantic tags (`<section>`, `<article>`, etc.)
- Add CSS to the `<style>` block (use existing variables)
- Test responsiveness on mobile and desktop

**Updating colors or styling:**
- Edit the `:root` CSS variables
- Changes apply site-wide (both files if using the same palette)
- Test contrast ratios for accessibility

**Linking new assets:**
- Place file in appropriate folder (`icons/`, `cv/`, `md/`, or root for images)
- Reference with relative path only (no leading `/` or domain)
- Test the link in a browser

## Deployment

- Pushed to `main` branch automatically deployed via GitHub Pages
- `CNAME` file configures root domain (`lucamilan.eu`)
- Site serves from repository root (`/index.html` is the home page)

## Team Structure

This repository uses a **squad model** (`.squad/` directory). Future Copilot sessions should:
- Respect team routing (see `.squad/routing.md` for who handles what type of work)
- Check `.squad/decisions.md` before making architectural changes
- Document decisions that affect multiple areas in `.squad/decisions/inbox/`

Key team members: **Ripley** (Lead), **Hicks** (Frontend), **Bishop** (Content/UX), **Vasquez** (QA).

---

**Last updated:** 2026-04-29T10:42:20.226+02:00
