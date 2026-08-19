# Project Status

## Last Updated
2026-08-18

## In Progress (uncommitted)
- (none — everything below is being committed this session)

## Note
- Git-on-PATH issue: Visual Studio 2022 Community's bundled Git (`...Common7\IDE\CommonExtensions\Microsoft\TeamFoundation\Team Explorer\Git\cmd\git.exe`) is on the **User** PATH permanently, but each Claude Code PowerShell tool call is a separate process that doesn't inherit that PATH update automatically — prepend the git cmd folder to `$env:PATH` at the start of any command that needs `git`.
- CLAUDE.md now instructs reading this file (PROJECT_STATUS.md) at the start of every session, in addition to CLAUDE.md itself.
- CLAUDE.md now also instructs: (1) before any commit, check this file for staleness and fold updates into the same commit; (2) after any page change, restart the app and show it in Chrome without being asked.

## Next Up
- Projects page: user plans to trim/edit the drafted project list down to favorites, adding context where helpful.
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
- Removed the Privacy page entirely (deemed unnecessary): deleted `Privacy.cshtml`/`Privacy.cshtml.cs`, removed its nav-bar link, and removed the reference to it in the (already commented-out) footer.
- Homepage redesigned again: replaced the white `.home` card with a full-bleed `.home-hero` (`headshot.png` background + the site's existing `#667eea`→`#764ba2` gradient overlay at 85% opacity), matching a reference site's (davidmalloryhays.com) hero technique. Iterated with the user on crop position, text size/placement, and a full-bleed vs. bordered-card comparison — user chose full-bleed, text scaled up (~3rem name) and shifted down ~20% from center.
- Nav bar (`_Layout.cshtml`/site.css): added active-page highlighting (bold + accent-colored underline via `ViewContext.RouteData`); made the nav bar itself full-bleed (flush to viewport top/left/right on every page) and pulled the homepage hero flush against it. Added `overflow-x: hidden` on `html` to fix a ~7px horizontal-scrollbar bug caused by the `100vw` full-bleed technique.
- Projects.cshtml fully drafted from Resume.cshtml + the PDF resume + the user's public GitHub repos: a "Professional Work" section (9 entries derived from each job in the work history) and a "Personal & Academic Projects" section (8 entries, with GitHub links where a matching public repo exists). Dates removed from all project entries per user feedback.
- Code review pass and fixes: per-page browser tab titles ("John Fitzgerald: {Page}", home page stays name-only) via `ViewData["Title"]`; fixed malformed `</>` tag and a hover-underline bug on the Resume page's LinkedIn/GitHub icon links (stray whitespace inside the `<a>` was extending the underline past the icon); added `rel="noopener noreferrer"` to all `target="_blank"` links; replaced the hardcoded `-20px`/`-16px` nav/hero flush-offset magic numbers with `--page-edge-gap`/`--navbar-gap` CSS variables (single source of truth, and removed Bootstrap's competing `mb-3` from the nav so our own margin isn't fighting an `!important` utility); merged a duplicated `.home-hero-content .btn-cta` CSS rule; improved headshot alt text. Removed the now-fully-dead commented-out skill-bar background colors in site.css (open decision resolved: bars stay solid `#667eea`).
- Meta description + Open Graph/Twitter card tags added to `_Layout.cshtml`, computed per-page from `ViewData["Title"]`/`ViewData["Description"]` and the live request host (no hardcoded domain, so it works pre- and post-deploy). `wwwroot/images/og-preview.png` (1200×630, standard OG size) generated from a user-provided screenshot of the homepage hero, center-cropped to size. "(Google)" removed from the Resume page's description per feedback.
- About and Projects page cards (`.about`, `.projects`) given the same hover "lift" (`translateY(-4px)` + deeper shadow) the Resume page card already had, for consistency across all three.

## Deferred (not in current scope)
- Broader site architecture: single-page vs. multi-page nav, consolidating About/Projects, headshot removal.
