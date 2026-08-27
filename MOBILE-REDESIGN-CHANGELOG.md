# Maitra Solar Solutions — Mobile Redesign

## Scope

This release changes the mobile experience only. The desktop/computer presentation layer remains frozen and the existing desktop CSS files were not modified.

## Mobile changes

- Reworked the mobile hero into a cleaner editorial composition.
- Moved the hero logo visually to the upper-left while retaining the existing brand asset.
- Moved the mobile menu control to the upper-right.
- Replaced the ambiguous Project Assist floating card with an explicit **Talk to an Engineer** hero action.
- Added a secondary hero service shortcut.
- Added a subtle mobile scroll cue.
- Reduced the bottom navigation to a compact floating dock with five primary destinations.
- Removed the false Services active state from the landing screen.
- Hid the duplicate persistent Project Assist launcher on mobile.
- Added a mobile engineering philosophy statement after the hero.
- Reworked capabilities into a numbered vertical engineering index.
- Reworked the engineering workflow into a vertical sequence.
- Reworked Solar Asset Intelligence into a mobile system map.
- Reworked Inspection Lab controls and content for touch-first use.
- Stacked and simplified the performance console for mobile.
- Reworked technical insights into an editorial list.
- Reordered O&M storytelling so the field media leads the mobile section.
- Reworked projects into large editorial gallery cards with horizontal filters.
- Reworked the team presentation around a large feature portrait and horizontal selector.
- Added explicit mobile contact actions for the consultation flow and direct WhatsApp.
- Reworked the mobile menu into a full-screen command-center style experience.
- Reworked panels, modals and consultation flows as full-screen phone experiences.
- Preserved reduced-motion behavior and touch target sizing.
- Added mobile-only responsive WebP versions of the large transparent team cutouts.
- Deferred the O&M maintenance video on mobile until it is near the viewport.
- Bumped the service-worker cache to `maitra-shell-v24` and included the new mobile stylesheet.

## Desktop protection

The following existing desktop CSS files were left unchanged:

- `css/style.css`
- `css/style-base.css`
- `css/refinement.css`
- `css/internal-experience.css`
- `css/menu-experience.css`
- `css/mobile-composition.css`
- `css/mobile-composition-final.css`
- `css/client-polish.css`
- `css/mobile-optimization-final.css`
- `css/mobile-client-experience.css`

The new `css/mobile-redesign.css` is scoped to `max-width: 700px`.
