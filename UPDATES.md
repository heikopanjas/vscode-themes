# Recent Updates & Decisions

This file is the append-only log of project decisions and notable changes, maintained by coding agents following the `recent-updates` skill. Everything below the marker line is user-owned history: slopctl never overwrites it during init or merge.

<!-- {changelog} -->

### 2026-09-04 (v3.1.0, 41 steglitz theme)

- added 41 (Berlin 41 - Steglitz) as sixth theme variant in `themes/41-color-theme.json`
- registered 41 as a `vs-dark` uiTheme and added steglitz, bierpinsel and 41 keywords
- palette taken from the Bierpinsel on Schloßstraße: graphite louvre background (#2e3133), salmon facade foreground (#e89279), signal-red window frames (#e8402c) as accent and title bar
- rationale: the collection had no warm dark variant; W30, SW61 and SO36 are all black or blue, so a low-blue graphite-and-orange theme fills a real gap
- naming: the 1962 postal system uses numeric codes, so the district code is simply 41 and the file follows the existing `[district-code]-color-theme.json` convention as `41`
- packaging: excluded `UPDATES.md` and `.agents/**` from the VSIX, they are development-only files that were shipping to users
- accessibility: made the 41 palette colorblind-friendly - git and diff signal added/removed as cyan vs red rather than green vs red, ANSI green is an aqua, and every syntax token clears WCAG AA (4.5:1) on the editor background
- accessibility: keywords use a lightened signal red (#ff6e4a) plus bold, since bold is a non-color cue and the original #e8402c only reached 3.2:1 contrast; the pure signal red is retained for the title bar and borders
- flattened the chrome: sidebar, activity bar and panel backgrounds now match the editor background (#2e3133) instead of being progressively darker, matching the flat-surface convention already used by W30 and SW11
- sidebar section headers keep a subtle step (#272a2b) so sections stay readable on the flat sidebar, mirroring how SW11 handles the same problem
- version bump: 3.0.0 to 3.1.0 (MINOR - new theme added, no breaking changes to existing themes)

### 2025-10-05 (v0.1.0, initial setup)

- initial AGENTS.md setup
- established core coding standards and conventions
- defined repository structure and governance principles
