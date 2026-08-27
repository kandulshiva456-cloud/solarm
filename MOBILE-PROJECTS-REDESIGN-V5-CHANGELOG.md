# Maitra Solar — Mobile Projects Option Redesign

## Scope
Only the Projects / Project Gallery option was changed for the new mobile experience.

## Implementation
- Restored the mobile Projects command/panel entry that had been intentionally hidden.
- Kept the landing-page Projects section hidden on mobile so the mobile option remains a dedicated panel experience.
- Replaced the previous mobile Projects card treatment with a new editorial, image-first portfolio layout.
- Added a sticky, touch-friendly category filter rail.
- Preserved the existing GALLERY data and gallery grouping/filtering logic as the single source of truth.
- Added a project-specific mobile lightbox presentation without changing the shared lightbox styling used by Services/O&M.
- Preserved gallery ordering, captions, counters, Previous/Next controls and existing touch swipe handling.
- Preserved adjacent-image preloading.
- Added mobile safe-area and dynamic viewport handling.
- Preserved the existing Maitra navy/blue/yellow visual language.
- Kept the desktop Projects presentation and unrelated website panels outside the mobile Projects scope.

## Files changed
- `index.html` — cache-bust version for the Projects mobile stylesheet.
- `js/script.js` — allow the Projects panel on mobile and scope the project lightbox state.
- `css/mobile-projects-redesign.css` — replaced the previous mobile Projects design with the new implementation.

## Verification
- `node --check js/script.js` passes.
- Gallery data remains in the existing `GALLERY` constant; no duplicate mobile dataset was added.
