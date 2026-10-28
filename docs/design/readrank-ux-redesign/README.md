# Read & Rank UX redesign — clickable prototype

**Status:** Proposal for review. Design reference only — nothing in `src/` changes, and nothing here is part of the app build.

This folder holds a clickable HTML prototype of a visual/UX refresh of the Read & Rank flow, from the landing page through the full ballot and the Compass steps. It is meant as a reference for implementing the screens in the React app, not as code to ship.

## How to view it

- Open `prototype/index.html` in a browser. It is a single self-contained page; the screens are linked, so you can click through the whole flow.
- Or browse the PNGs in `screenshots/`.

## Screens

| # | Screen | Screenshot |
|---|---|---|
| 1 | Landing: hero, how it works, choose an election (Upcoming / Past) — only races on the user's own ballot (US House, Senate, governor); a different place is picked with **Change** | `01-landing.png`, `02-landing-past-races.png` |
| 2 | Choose your issues (in-progress race) | `04-choose-issues.png` |
| 3 | Read a quote: agree / disagree, arrow-key shortcuts | `05-read-quote.png` |
| 4 | After answering: ranking panel (reorderable), disagreed tray, topic complete | `06-topic-complete-ranking.png` |
| 5 | Your rankings (full ballot): loading step, then staged reveal | `07-ballot-loading.png`, `08-full-ballot.png` |
| 6 | Compass step 1: choose topics (3–8) | `09-compass-choose-topics.png` |
| 7 | Compass step 2: your stances, with a 2-step guide pop-up | `10-stances-guide.png`, `11-stances.png` |
| 8 | Compass step 3: compass ready, compare animation | `12-compass-ready-compared.png` |

## Layout consistency with Treasury Tracker

Margins, borders and spacing follow the ev-ui values Treasury Tracker uses: header up to 1512px wide with 16px/24px padding and 43px logos; landing hero with 48/64/96px side margins and 64px vertical padding beside a 380px step column; every screen uses the landing hero's side margins (96px on wide screens, 64px tablet, 48px small laptop, 16px phone); 1px `#D3D7DE` borders; 16px corners on step cards and large panels, 12px on content cards, inputs and buttons; footer up to 1280px wide with 32px/40px vertical padding.

## Placeholder content (must be replaced with real data)

- The second Housing quote ("Local zoning should allow more homes near jobs and transit…").
- Border Security and Civil Rights stances on the stances screen; any other Compass topic shows `[Stance n for …]`.
- On Compass step 1, the category name "Economy and housing" and the questions for Housing, Childcare and Data Centers (these were hidden in the reference screenshot).
- Immigration quotes on the full ballot ("See what they said") show `[Immigration quote from the ballot]`.
- The Candidate A / Candidate B outlines in the compare animation are illustrative only.
- Reading-time estimates (about 15 seconds per quote).
- Past races (US Senator, Governor and US Representative District 7, Nov 5, 2024) show `[#] candidates · [#] topics` and aren't clickable in the prototype. Indiana has no U.S. Senate or governor race on the Nov 3, 2026 ballot, so Upcoming shows District 7 only.
- The broad area shown is "Indianapolis, Indiana" (District 7). The **Change** button is not wired up in the prototype.

## Open questions for the team

1. **Palette.** The prototype uses teal `#0E6A80`, coral `#EF5B3E`, yellow `#F6C343` and navy text `#1B1E3B`. `REDESIGN_SPEC.md` specifies ev-ui tokens (ev-teal `#00657c`, ev-coral `#ff5740`, ev-yellow `#fed12e`, ev-black `#1c1c1c`) and uses coral for Agree. Implementation should use the ev-ui tokens; the Agree/Disagree color roles need a decision.
2. **Reveal model.** The prototype reveals candidates on one full-ballot screen. `CLAUDE.md` / `REDESIGN_SPEC.md` describe a per-topic reveal where the ballot grows as each topic is ranked.
3. **Dark mode logos.** The official logos (used unchanged) have dark teal text that is hard to read on the dark header. Options: keep the header white in dark mode, or add light logo variants.
4. **"Place the rest as agreed"** from the current ranking panel is not in the prototype; its intended behavior should be confirmed.
5. **Your own stance** is placed on the middle ring for now (the placement slider was removed on request).

## Files

- `prototype/index.html` — the combined, clickable prototype (open this).
- `prototype/*.html` — one file per screen (landing, issues, read, ballot, compass, stances, ready).
- `prototype/build_flow.py` — combines the screen files into `index.html` (`python3 build_flow.py`). Its output omits the `<!doctype html>` / `<head>` wrapper, which was added to the checked-in `index.html` so it opens directly in a browser.
- `prototype/assets/` — the official Empowered Vote and Read & Rank logos, unchanged, and `ballot-figure.png`, the ballot-casting figure from the empowered.vote homepage (`ev-landing/icons/Sticks/noun_ballot_3139174.png`, a Noun Project icon — confirm the team's license covers reuse here). It is recolored with a CSS mask on the ballot loading step, the Topic complete card and the full-ballot banner.
- `screenshots/` — desktop captures at 1280px wide. They were captured without network access, so text renders in a fallback font instead of Manrope.
