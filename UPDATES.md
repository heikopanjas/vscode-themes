# Recent Updates & Decisions

This file is the append-only log of project decisions and notable changes, maintained by coding agents following the `recent-updates` skill. Everything below the marker line is user-owned history: slopctl never overwrites it during init or merge.

<!-- {changelog} -->

### 2026-09-04 (v3.1.3, no italic type)

- removed every `"fontStyle": "italic"` from all six themes, 9 rules in total; uniform font slant is part of the brand, extending the no-bold rule from 3.1.2
- no combined values such as `bold italic` existed, so nothing needed partial rewriting
- only `underline` (11 rules) and `strikethrough` (4 rules) remain
- affected `markup.italic`, so Markdown `*emphasis*` no longer renders slanted in any theme; this follows from the rule rather than being an oversight
- NW21 `markup.quote` styled quotes with italic and nothing else, so removing it left an empty rule; gave it the NW21 string blue (#0a3069), matching how every other theme already colors that scope
- documented the rule in AGENTS.md, including that a rule losing its only `fontStyle` needs a `foreground` instead of an empty `settings` object
- version bump: 3.1.2 to 3.1.3 (PATCH - corrects styling in existing themes, no new features)

### 2026-09-04 (v3.1.2, no bold type)

- removed every `"fontStyle": "bold"` from all six themes, 27 rules in total; uniform font weight is part of the brand
- italic, underline and strikethrough are unaffected and still in use
- affected `markup.bold`, so Markdown `**bold**` no longer renders bold in any theme; this follows from the rule rather than being an oversight
- 41 used bold on keywords as a deliberate non-color cue for colorblind users; the cue is dropped, but the keyword red (#ff6e4a) still clears WCAG AA at 4.73:1 and sits 17.7 delta E from the base salmon under all three CVD simulations, so keywords stay distinguishable by color alone
- documented the rule in AGENTS.md next to the shared brand chrome table
- version bump: 3.1.1 to 3.1.2 (PATCH - corrects styling in existing themes, no new features)

### 2026-09-04 (v3.1.1, shared brand chrome)

- unified the tab strip and sidebar title bar across all six themes; these are brand furniture, not per-district colors, and had drifted apart
- NW21 was the reference: dark tab strip (#0d1117) with inactive tabs at #010409, #c9d1d9 active text, #777777 tab border and a black sidebar title bar
- W30, SW61, SO36 and 41 had tab strips that simply tracked their own editor background, and SW11 had tinted the strip warm; all now carry the identical 18-key brand block
- accents stay per-district: only `tab.activeBorderTop` and `panelTitle.activeBorder` vary
- lightened SW11 tab accent from #3c6070 to #7ba6bd, the original was picked against a light background and only reached 2.79:1 on the dark strip; #3c6070 is retained for its panel title where it still sits on limestone
- panel header foregrounds stay per-theme so they remain readable on each district's panel background, all verified at 5.7:1 or better
- documented the rule in AGENTS.md so the furniture does not drift again
- version bump: 3.1.0 to 3.1.1 (PATCH - corrects inconsistent chrome in existing themes, no new features)

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
