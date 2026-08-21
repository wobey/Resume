# Project Status

## Last Updated
2026-08-20

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
- Once a real domain is purchased: add a `Sitemap:` line to `robots.txt`, and double-check the JSON-LD `url` field (already computed dynamically from the request host, so no code change needed, just verification).
- GoatCounter: user's `wobey@uw.edu` account email is still unverified as of 2026-08-20 — worth confirming/verifying once convenient.

## Recently Completed
- JSON-LD `Person` schema added to `_Layout.cshtml` (dynamic `baseUrl`, no hardcoded domain).
- GoatCounter analytics script added to `_Layout.cshtml` (site code `wobey`). Confirmed via direct testing that GoatCounter's own client-side script deliberately filters out `localhost`/private-IP hits (e.g. `192.168.x.x`) by design — this is why dev/LAN testing showed "no data," not a misconfiguration. Will track normally once deployed to a real public domain.
- `robots.txt` added (`wwwroot/robots.txt`) — allows all crawling; no `Sitemap:` line yet since there's no domain to point it at.
- `@media print` stylesheet added for the Resume page (hides nav bar and PDF button, removes card shadow/max-width, for a clean printout).
- Accessibility fixes (Lighthouse Resume-page score 95→100): plain-text LinkedIn/GitHub links on Resume.cshtml given `target="_blank" rel="noopener noreferrer"`; `.entry-dates` color contrast fixed (`#999`→`#666`, was 2.66:1, now passes 4.5:1); LinkedIn/GitHub SVG icons marked `aria-hidden="true"` since their parent `<a>` already carries `aria-label`.
- Responsive fix: `.skill` row side margins reduced under a 480px viewport — was fixed at 50px each side, squeezing the Skills bars unreadably narrow on phone-width screens.
- Nav bar layout-shift bug fixed (two contributing causes, confirmed via pixel-level measurement): removed the `font-weight: 600` bump on the active nav link (was widening that link's text and shifting siblings); added `overflow-y: scroll` to `html` so the vertical scrollbar's presence/absence (varies by page content height) no longer shifts the centered `.container` left/right between pages.
- Resume.cshtml wording: GlobalLogic (2025–Present) entry changed from "saved team members roughly one hour per day" to "saved team members roughly 5+ hours per week."
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
- Next side project (planned, separate repo, after this site is done): a "Job Market Pulse" job-postings data pipeline + dashboard (Python ingestion from the Adzuna API → Postgres → ASP.NET Core aggregation API → Tableau Public dashboard, scheduled via GitHub Actions cron). Full architecture and reasoning recorded in Claude's auto-memory for this project (not in this repo) — ask Claude to recall it, or see the 2026-08-20 conversation.
