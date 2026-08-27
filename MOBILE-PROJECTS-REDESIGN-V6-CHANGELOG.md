# Maitra Solar — Mobile Projects Image Browser (V6 patch)

## Scope
Mobile-only Projects image browser only. Nothing else was touched.

The V5 implementation already in the ZIP (`MOBILE-PROJECTS-REDESIGN-V5-CHANGELOG.md`)
covered most of the brief: a dedicated mobile Projects panel, one card per
existing gallery category, a full-screen mobile image viewer with
Previous/Next, dynamic counter, captions, swipe navigation, thumbnail strip,
scroll locking and safe-area handling — all driven by the existing `GALLERY`
/ `GALLERY_FILTERS` data with no duplicate dataset.

This patch closes the remaining gaps against the brief without altering that
existing design:

## What was added

1. **A real "All" browsing mode.** Tapping the "All" category chip on the
   mobile Projects panel now opens the full-screen viewer over the complete,
   existing `GALLERY` array in its existing order — not just a filtered list
   of category cards. (`openLightboxAll()` in `js/script.js`.)
2. **Every category chip now opens straight into that category's viewer**
   on mobile (in addition to filtering the card list as before), so a single
   tap gets to the images — matching "tap category → images appear."
   Desktop's `#galleryFilters` keeps its original filter-only behavior; the
   new behavior is scoped to `.panel-shell[data-panel="projects"]` and to
   the mobile breakpoint.
3. **Restored the missing "Solution Cleaning" category** to
   `GALLERY_FILTERS`. Its images (`module-surface-care/*`) already existed
   in `GALLERY` and were already reachable as their own card, but had no
   filter chip — every existing category is now represented consistently.
4. **Per-category image counts**, computed from the real `GALLERY` array
   length (never hardcoded), shown on each category card and as a running
   total in the panel summary.
5. **Graceful broken-image handling** for the Projects grid cards, the
   full-screen viewer image, and the thumbnail strip: a failed image no
   longer leaves a broken-image icon — it shows a small "Image unavailable"
   placeholder and browsing continues normally.

## Files modified
- `js/script.js` — `GALLERY_FILTERS` (added `solution`), `renderGallery()`
  (image count + alt fallback + broken-image handling), `showLightboxImage()`
  (broken-image handling), new `openLightboxAll()`, and the shared click
  handler for `.filter-btn` (mobile-panel-only direct-open behavior).
- `css/mobile-projects-redesign.css` — styling for the new per-card image
  count and the broken-image placeholders. All additions are inside the
  existing `@media (max-width: 700px)` block and scoped to
  `.panel-shell[data-panel="projects"]` / `.lightbox.is-project-gallery`.
- `index.html` — cache-bust bump (`mobile-projects-redesign.css?v=6`,
  `script.js?v=4`).

## Data
No new or duplicate gallery data was created. `GALLERY` and
`GALLERY_FILTERS` remain the single source of truth; the "All" viewer and
the per-category counts are both derived directly from `GALLERY` at
render/open time.

## Desktop
Not touched. The new direct-open behavior on `.filter-btn` clicks is gated
on `isMobileProjectsView()` (`max-width: 700px`) **and** the button being
inside `.panel-shell[data-panel="projects"]`, which only exists in the
mobile panel markup — the desktop `#galleryFilters` bar lives inside
`<section id="projects">` and is unaffected. The one shared-data change
(adding the `solution` filter chip) also appears on desktop, since the
same `GALLERY_FILTERS` array feeds both — this is a data-completeness fix
(a genuine existing category was missing its chip), not a redesign, and
the brief explicitly requires every existing category to remain accessible.
The broken-image CSS fallback for cards is scoped to
`.panel-shell[data-panel="projects"]`, so it has no visual effect on
desktop cards; the lightbox-image fallback CSS is scoped to
`.lightbox.is-project-gallery`, which only applies when a Projects (not
Services/O&M) gallery is open, on any screen size — desktop users opening a
broken Projects image now also see a graceful placeholder rather than a
broken-image icon.

## Testing
- `node --check js/script.js` passes.
- CSS brace balance verified.
- Not runnable in this environment: an actual browser/device pass. The
  following were **not interactively verified** because no browser is
  available here — please spot-check before shipping:
  - All 9 categories individually at 320×800, 375×812, 390×844, 430×932.
  - Swipe left/right, Previous/Next wrap-around, counter and caption
    updates for a full pass through the "All" mode (44 images).
  - Safe-area insets on an actual notch/Dynamic-Island device.
  - Desktop regression pass (Projects, other sections, console).

## Problems / honesty note
No broken image files were found in this ZIP to test the new fallback
against — the fallback logic is implemented and CSS-verified but not
exercised against an actual failing image load in this environment.
