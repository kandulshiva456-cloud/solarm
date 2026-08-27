# Maitra Desktop Redesign — v2

## Scope
Desktop/computer presentation is redesigned for bright, light-first visual language. Mobile remains isolated to the existing mobile redesign layer.

## Major changes
- Added `css/desktop-redesign.css` as the final desktop presentation layer.
- Kept the cinematic hero/video and Maitra identity while improving container alignment, typography scale, hero contrast and CTA proportions.
- Reworked the desktop command dock into a bright, precise navigation rail matching the supplied reference.
- Kept Project Assist visible on desktop and aligned it above the navigation rail.
- Converted full-width dark content sections to light/white/pale-blue surfaces.
- Reworked Services cards into a bright engineering index presentation.
- Refined workflow, asset intelligence and inspection sections for light technical presentation.
- Reworked the performance prototype as a light console without implying live data.
- Converted Insights to a clean editorial index.
- Kept the O&M video cinematic while moving its surrounding section to a light canvas.
- Reworked Projects/Field Portfolio styling to match the supplied light reference.
- Reworked Team and Contact presentation for bright editorial consistency.
- Kept internal experience panels/modals on the supplied light reference language.
- Removed the stray delayed `openPanel('team')` script that could unexpectedly open Team on page load.
- Added the new desktop stylesheet to the service-worker precache.
- Bumped the service-worker shell cache to `maitra-shell-v25`.

## Desktop/mobile isolation
- Desktop layer is scoped to `@media (min-width: 701px)`.
- Mobile layer remains scoped to `@media (max-width: 700px)`.
