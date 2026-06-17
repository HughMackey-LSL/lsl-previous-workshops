```md
# Project Summary

This project creates a static GitHub Pages-friendly replacement for the NYU Stern Learning Science Lab “Previous Workshops” page.

## Current Aim

Build a more navigable index of past Learning Science Lab workshops that preserves the original workshop content and resource links while adding functionality missing from the Stern CMS page.

The index should support:
- Searching workshop titles and descriptions
- Filtering by academic term
- Filtering by inferred topic/category
- Sorting by term or workshop name
- Preserving each workshop’s recording and slide links

## Source Content

Workshop content was extracted from:

https://www.stern.nyu.edu/portal-partners/faculty-staff/learning-science-lab/workshops/previous-workshops

The extracted dataset currently includes:
- 46 workshops
- 46 recording links
- 46 slide links
- Terms from Spring 2022 through Spring 2026
- Inferred topic categories based on workshop titles/descriptions

## Current Output

The main deliverable is:

`outputs/index.html`

This is a single static HTML page with embedded CSS, JavaScript, and workshop data. It is intended to be deployable directly as a GitHub Pages `index.html`.

## Generator

The generated page is produced by:

`work/build_workshop_index.py`

This script parses the saved source HTML and rebuilds `outputs/index.html`. Any structural/styling/content-generation changes should be made in this script first, then regenerated.

## Current Design Direction

The page mirrors the Stern source site broadly:
- Black top audience bar
- White institutional header
- Breadcrumb row
- Large page title
- Gray controls band
- Card-based workshop results
- Stern-like purple, black, gray, and accent styling
- Montserrat as the default font, loaded from Google Fonts

## Branding Status

The previous hand-built HTML approximation of the NYU Stern logo was removed because it would not conform to branding standards.

The header now contains a placeholder logo slot that expects a local file named:

`stern-logo.png`

Place that image next to `index.html` when deploying. If absent, the page shows a clean placeholder.

## Image Policy

Workshop thumbnail images were removed.

Reason: if this page replaces the source site, it should not depend on public image URLs from the Stern CMS. The generated page currently contains no workshop image URLs and no `<img>` tags.

## Verification Status

The page has been checked with Playwright:
- 46 workshops render
- 0 `<img>` tags remain
- Search works
- Term filtering works
- Topic filtering works
- Sorting works
- Reset works
- Desktop and mobile layouts render cleanly

## Known External Dependencies

The page currently loads Montserrat from Google Fonts. If a fully offline/self-contained deployment is required, Montserrat would need to be bundled locally or replaced with a system fallback.
```