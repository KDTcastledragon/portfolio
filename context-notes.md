# Portfolio Context Notes

## 2026-07-14

- The portfolio will eventually contain multiple full-page project groups, so CastleChat must no longer define the global page background or header identity.
- The fixed header represents Lee Seong-ryong's whole portfolio. The user's pink overlay was a placement guide, not a requested color theme.
- The original dark-green CastleChat palette, typography, and headline scale must remain unchanged. Only box placement and dimensions follow the supplied overlay.
- The white-background requirement applies outside the fixed header and CastleChat project box. The header and project box retain the original dark-green style.
- Do not invent overview copy or project metadata. The project box contains only the existing headline, deployment actions, project number, and requested detail menu.
- Desktop widths above 820px keep the three-column project layout and fit it to the remaining viewport height without a document scrollbar. Smaller screens retain natural vertical scrolling to prevent clipped content.
- Existing architecture and technology-stack dialogs remain reusable. The old design-principle summary panel is removed from the CastleChat landing composition.
- Major skills, troubleshooting, and one undecided menu entry are visual placeholders only until their actual content is supplied.
- The CastleChat stage uses a three-column desktop composition and collapses to one column below 720px. The existing architecture and stack buttons retain their dialog behavior.
- The earlier light-and-pink interpretation was rejected and replaced with the original CastleChat visual theme.
- Static verification confirmed unique HTML IDs, valid inline JavaScript syntax, balanced CSS braces, and a clean `git diff --check` result.

## 2026-07-13

- Nginx is a directly managed Docker reverse-proxy container, not a Kubernetes Ingress controller.
- The architecture view uses data-flow direction for Kafka and request/dependency direction for service calls.
- Channel Engine does not call Event Persist Worker directly. The event path is Channel Engine to Kafka to Event Persist Worker to MariaDB.
- Redis is shared by sessions and read/member caches. AI rate limiting is not presented as active production behavior.
- AWS and Kubernetes deployment details are not represented as completed infrastructure in this logical architecture view.
- The desktop canvas height reserves space for the header, legend, and two architecture notes so the complete board fits in a typical laptop viewport.
- Static verification confirmed UTF-8 integrity, unique core view IDs, valid inline JavaScript syntax, and a clean `git diff --check` result.
- Direct `file://` visual inspection was unavailable because the in-app browser blocks local file URLs. GitHub Pages rendering remains the final visual check after push.

## 2026-07-14 visual polish

- User explicitly requested a lighter green palette, so this overrides the earlier note that the original dark CastleChat palette should remain.
- Keep the CastleChat box structure unchanged. Only color, radius, subtle motion, and a 7px upward optical shift are in scope.
- Visual verification used Chrome headless at 1038x510 after a 2s virtual-time budget. The CastleChat stage renders as a light green board with rounded corners, subtle motion-completed content, and no visible vertical scrollbar.