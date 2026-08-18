# Project Status

## Last Updated
2026-08-17

## In Progress (uncommitted)
- (none — everything below is being committed this session)

## Note
- Git-on-PATH issue: Visual Studio 2022 Community's bundled Git (`...Common7\IDE\CommonExtensions\Microsoft\TeamFoundation\Team Explorer\Git\cmd\git.exe`) is on the **User** PATH permanently, but each Claude Code PowerShell tool call is a separate process that doesn't inherit that PATH update automatically — prepend the git cmd folder to `$env:PATH` at the start of any command that needs `git`.
- CLAUDE.md now instructs reading this file (PROJECT_STATUS.md) at the start of every session, in addition to CLAUDE.md itself.
- CLAUDE.md now also instructs: (1) before any commit, check this file for staleness and fold updates into the same commit; (2) after any page change, restart the app and show it in Chrome without being asked.

## Open Decision
- Skill-bar background colors (`.backend`, `.sql`, `.python`, `.automation`, `.csharp`, `.frontend`) are commented out in site.css, not removed — need to decide whether to restyle, restore, or drop the skill bars entirely.

## Next Up
- Finish reviewing/polishing Experience and Education sections.
- Skills section.
- Projects section.
- Contact section.
- Dark mode (optional, future).
- Homepage: still uses a plain "GitHub" text link, no icon (Resume page has both icon + text) — consider matching, or leave homepage intentionally minimal.

## Recently Completed
- Resume.cshtml: "Github" → "GitHub" capitalization fix in link text.
- site.css: `.entry-summary` font-size finalized at `0.75rem`.
- "Full Resume (PDF)" turned into a standout button (`.btn-cta`): gradient pill matching the site's accent color (`#667eea` → `#764ba2`), hover lift.
- Homepage (Index.cshtml) redesigned per user mockup: name/title/tagline/statement matching the Resume page's style, `.btn-cta` buttons linking to Resume and Projects, simple LinkedIn/GitHub/Email contact line. Wrapped in a new `.home` card to match the site's existing white-card-on-gradient look.
- `.resume-pdf-btn` generalized to reusable `.btn-cta` class (used by both Home and Resume pages).
- About.cshtml redesigned to match the layout pattern of a reference site (davidmalloryhays.com/about): centered "About Me" heading, five icon + bold-lead-line card sections (`.about-section`), styled with the site's existing light/purple theme instead of the reference's dark theme. Closing career statement folded into the last card as a plain paragraph (not a separate highlighted box, per feedback).

## Deferred (not in current scope)
- Broader site architecture: single-page vs. multi-page nav, consolidating About/Projects/Privacy, headshot removal.
