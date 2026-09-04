# VS Code Theme Development - Copilot Instructions

## Project Overview

This is a VS Code theme development project for **Berlin Postal Themes**, a collection of themes inspired by historic Berlin postal districts (Postzustellbezirke). Each theme represents a different West Berlin postal district from the 1960s-1993 era, bringing Berlin's urban history to the coding experience.

### Theme Variants

- **NW21** (Nordwest 21 - Moabit) - Soft light theme with gentle blue-tinted backgrounds (#e8eefe) for comfortable extended coding
- **W30** (West 30 - Schöneberg) - Ultra-dark theme with deep black backgrounds (#010409) for low-light coding
- **SW61** (Südwest 61 - Kreuzberg) - Blue-tinted dark theme with blue backgrounds (#00205A) for a calming coding experience
- **SO36** (Südost 36 - Kreuzberg) - Medium-dark blue theme with cyan title bar (#204b81) for the punk heart of Kreuzberg
- **SW11** (Südwest 11 - Kreuzberg) - Warm limestone-white light theme (#f6f3ec) inspired by the Großbriefverteileramt SW 11
- **41** (Berlin 41 - Steglitz) - Warm graphite dark theme (#2e3133) with salmon facade text (#e89279), inspired by the Bierpinsel

### Current Status

All six theme variants are implemented and functional. The extension has been rebranded from "Super Theme Collection" to "Berlin Postal Themes" and is ready for testing, packaging, and marketplace publication at version 3.1.3.

## Project Structure

```
berlin-postal-themes/
├── package.json                          # Extension manifest (Complete)
├── README.md                            # Project documentation (Complete)
├── LICENSE                              # MIT License
├── AGENTS.md                            # AI assistant guidelines (this file)
├── .gitignore                           # Git ignore file with VSIX exclusions
├── themes/                              # Theme definition files
│   ├── nw21-color-theme.json         # Complete - NW21 Moabit light theme
│   ├── w30-color-theme.json          # Complete - W30 Schöneberg dark theme
│   ├── sw61-color-theme.json         # Complete - SW61 Kreuzberg blue theme
│   ├── so36-color-theme.json         # Complete - SO36 Kreuzberg medium-dark blue theme
│   ├── sw11-color-theme.json         # Complete - SW11 Kreuzberg limestone-white light theme
│   └── 41-color-theme.json           # Complete - 41 Steglitz graphite Bierpinsel theme
├── .github/                             # GitHub configuration
│   └── workflows/                       # GitHub Actions workflows
│       └── build-vsix.yml               # Automated VSIX build workflow
├── dist/                                # Build output directory (gitignored)
├── docs/                                # Documentation and assets
│   └── images/                          # Theme preview images
│       ├── super-themes-light.png       # NW21 screenshot
│       ├── super.themes-black.png       # W30 screenshot
│       └── super-themes-blue.png        # SW61 screenshot
├── super-themes.png                     # Extension icon
└── CHANGELOG.md                         # Version history (Optional)
```

## Development Guidelines

### Theme Development Best Practices

1. **Color Consistency**: Maintain consistent color relationships across all UI elements
2. **Accessibility**: Ensure sufficient contrast ratios for readability
3. **Language Support**: Test theme with multiple programming languages
4. **UI Coverage**: Theme all VS Code UI elements including editor, sidebar, panels, etc.
5. **Dark/Light Variants**: Consider providing both dark and light theme variants

### Key Theme Areas to Cover

- **Editor Colors**: Background, foreground, selection, line highlighting
- **Syntax Highlighting**: Keywords, strings, comments, functions, variables
- **UI Colors**: Sidebar, activity bar, status bar, tabs, panels
- **Terminal Colors**: ANSI color palette for integrated terminal
- **Diff Colors**: Git diff highlighting in editor and source control
- **Error/Warning Colors**: Diagnostic highlighting and problem indicators

### File Naming Conventions

- Theme files: `[district-code]-color-theme.json`
- District codes: `nw21`, `w30`, `sw61`, `so36`, `sw11`, `41`
- Use kebab-case and lowercase for file names
- Maintain consistent naming across all theme variants

### Theme Variant Guidelines

- **NW21 (Moabit)**: Soft light backgrounds (#e8eefe), gentle blue tint, comfortable extended coding
- **W30 (Schöneberg)**: Ultra-dark backgrounds (#010409), high contrast, minimal eye strain for low-light
- **SW61 (Kreuzberg)**: Blue-tinted backgrounds (#00205A), calming atmosphere, balanced contrast
- **SO36 (Kreuzberg)**: Medium-dark blue backgrounds (#204b81), cyan title bar (#00ccff), punk energy of SO36
- **SW11 (Kreuzberg)**: Warm limestone-white backgrounds (#f6f3ec), desaturated accents, calm daylight coding
- **41 (Steglitz)**: Graphite-grey backgrounds (#2e3133), salmon facade foreground (#e89279), signal-red accents (#e8402c)
- **Berlin Heritage**: Each theme reflects the character of its historic postal district
- **Consistency**: Maintain similar syntax highlighting patterns across variants
- **Accessibility**: Ensure all variants meet WCAG contrast requirements

### Shared Brand Chrome (all themes, identical values)

The tab strip and sidebar title bar are brand furniture, not per-district colors. These
keys must hold the same value in every theme file, light and dark alike:

| Key | Value |
| --- | --- |
| `editorGroupHeader.tabsBackground` / `noTabsBackground` / `border` / `tabsBorder` | `#0d1117` |
| `tab.activeBackground` / `tab.hoverBackground` / `tab.activeBorder` / `tab.unfocusedActiveBorder` | `#0d1117` |
| `tab.activeForeground` / `tab.hoverForeground` | `#c9d1d9` |
| `tab.inactiveBackground` | `#010409` |
| `tab.inactiveForeground` / `tab.unfocusedActiveForeground` | `#8b949e` |
| `tab.border` | `#777777` |
| `tab.unfocusedActiveBorderTop` | `#30363d` |
| `tab.unfocusedHoverBackground` | `#6e76811a` |
| `sideBarTitle.background` | `#000000` |
| `sideBarTitle.foreground` | `#c9d1d9` |

Only the accents stay per-district: `tab.activeBorderTop` and `panelTitle.activeBorder`.
Because `tab.activeBorderTop` sits on the dark `#0d1117` strip, a theme whose accent was
picked for a light background needs a lightened variant there (SW11 uses `#7ba6bd` on the
strip while keeping `#3c6070` for its panel title). Target at least 4.5:1 against `#0d1117`.

Panel header foregrounds (`panelTitle.activeForeground`, `panelTitle.inactiveForeground`)
remain per-theme, since the panel body keeps each district's own background.

### No Bold or Italic Type (all themes)

No theme may set `"fontStyle"` to `bold`, `italic`, or any combination containing
them, in `tokenColors` or `semanticTokenColors`. Weight and slant are brand
furniture and stay uniform. Only `underline` and `strikethrough` are allowed.

This means color and contrast have to carry all token distinctions on their own, so
new accents need a real luminance step rather than a weight or slant change to read
as distinct. When a rule loses its only `fontStyle`, give it a `foreground` instead
of leaving an empty `settings` object.

### Current Theme Specifications

**NW21 (Nordwest 21 - Moabit):**
- Editor background: #e8eefe (soft blue-tinted)
- Foreground: #1f2328 (dark gray)
- Cursor: #0969da (blue accent)
- Type: vs (light theme)
- Character: Industrial and creative Moabit
- Gentle on eyes for extended coding sessions

**W30 (West 30 - Schöneberg):**
- Editor background: #010409 (ultra-dark black)
- Foreground: #c9d1d9 (light gray)
- Cursor: #58a6ff (blue accent)
- Type: vs-dark
- Character: Schöneberg's vibrant nightlife
- Maximum contrast for low-light environments

**SW61 (Südwest 61 - Kreuzberg):**
- Editor background: #00205A (deep blue)
- Foreground: #c9d1d9 (light gray)
- Cursor: #58a6ff (blue accent)
- Type: vs-dark
- Character: Kreuzberg's alternative culture
- Calming blue tones for focused coding

**SO36 (Südost 36 - Kreuzberg):**
- Editor background: #204b81 (medium-dark blue)
- Foreground: #c9d1d9 (light gray)
- Cursor: #58a6ff (blue accent)
- Title bar: #00ccff (distinctive cyan)
- Type: vs-dark
- Character: The punk heart of Kreuzberg, raw energy and creativity
- Bold contrast with vibrant cyan accent

**SW11 (Südwest 11 - Kreuzberg):**
- Editor background: #f6f3ec (warm limestone white)
- Foreground: #2b2b2b (dark gray)
- Keywords: #3c6070 (slate-blue)
- Strings: #704214 (Anhalter brick-red)
- Numbers: #5c4a00 (muted ochre)
- Type: vs (light theme)
- Character: Sober Neues Bauen classicism of the Großbriefverteileramt
- Deliberately desaturated for calm long sessions

**41 (Berlin 41 - Steglitz):**
- Editor background: #2e3133 (graphite grey of the ventilation louvres)
- Foreground: #e89279 (salmon-orange facade panels)
- Keywords: #ff6e4a (lightened signal red)
- Strings: #ded9cf (raw concrete of the supporting stalk)
- Types: #7fb3d5 (Steglitz sky)
- Constants: #f2cf85 (warm sandstone)
- Title bar: #e8402c (signal red)
- Type: vs-dark
- Character: Pop-brutalist Bierpinsel on Schloßstraße
- Warm, low-blue dark theme with a single decisive accent
- Colorblind-friendly: git and diff use cyan vs red, never green vs red

### Testing and Validation

1. **Multi-language Testing**: Test with TypeScript, JavaScript, Python, JSON, Markdown, etc.
2. **UI Element Coverage**: Verify all VS Code interface elements are properly themed
3. **Color Blindness**: Test with color blindness simulators
4. **Different Screen Types**: Test on various displays (retina, standard, dark rooms)

### Common Tasks

- **Testing Themes**: Use F5 to launch Extension Development Host and test all theme variants
- **Build VSIX Locally**: Use `npm run build` to create installable .vsix file in ./dist/
- **Install Locally**: Use `npm run install-local` or `code --install-extension ./dist/*.vsix`
- **Validate Package**: Use `npm run validate` to check package without building
- **Automated Building**: Push to main/develop branches triggers GitHub Actions build
- **Release Process**: Create git tag (e.g., `v0.1.0`) to trigger automated release
- **Color Palette Management**: Maintain consistent color variables across all themes
- **Theme Validation**: Test with multiple languages (TypeScript, JavaScript, Python, JSON, Markdown)
- **Screenshot Generation**: Create preview images showing each theme variant

### Extension Development

- **Activation Events**: Themes activate on `*` (startup)
- **Contribution Points**: Use `themes` contribution point in package.json
- **Categories**: Use "Themes" category for marketplace
- **Keywords**: Include Berlin, postal, and district-related keywords for discoverability
- **Extension Name**: "berlin-postal-themes" with display name "Berlin Postal Themes"
- **Version**: Currently at 2.0.0 (major rebrand), ready for marketplace publication

### Next Steps & Publishing

1. **Testing**: Use F5 to test themes in Extension Development Host
2. **Icon Creation**: ✅ Extension icon added (super-themes.png)
3. **Screenshots**: ✅ Theme preview images added to README
4. **CHANGELOG**: Document version history and changes
5. **Automated Releases**: Create git tags to trigger automated releases with VSIX files
6. **Manual Publishing**: Use `vsce publish` to publish to marketplace (if desired)

### GitHub Actions Workflow

The project includes an automated build workflow (`.github/workflows/build-vsix.yml`) that:

**Triggers:**
- Push to `main` or any `feature/**` branches
- Pull requests to `main` or any `feature/**` branches
- Git tags starting with `v` (e.g., `v0.1.0`)
- Manual workflow dispatch

**Build Process:**
1. **Validation**: Checks package.json and theme files are valid JSON
2. **VSIX Creation**: Builds the extension package using `vsce package`
3. **Artifact Upload**: Stores VSIX file as GitHub artifact (30-day retention)
4. **Release Creation**: Automatically creates GitHub releases for version tags
5. **Asset Upload**: Attaches VSIX file to releases for easy download

**Usage:**
- **Development**: Push to `main` or any `feature/**` branch to validate and build
- **Feature Work**: All feature branches automatically build and validate when pushed
- **Pull Requests**: PRs to `main` or `feature/**` branches trigger builds for validation
- **Releases**: Create and push git tag (`git tag v0.1.0 && git push origin v0.1.0`)
- **Downloads**: Get VSIX files from GitHub Actions artifacts or releases

## AI Assistant Guidelines

### When Helping with Theme Development

1. **Color Theory**: Apply principles of color harmony and accessibility
2. **VS Code API**: Reference official VS Code theme color documentation
3. **JSON Structure**: Maintain proper theme file structure and syntax
4. **Testing Recommendations**: Suggest comprehensive testing approaches
5. **Marketplace Preparation**: Help with extension packaging and publishing

### Git Workflow Automation

When the user requests to "commit the latest changes" or similar:
1. **Stage Changes**: Automatically stage all modified files using `git add .`
2. **Commit Message**: Write detailed but concise commit messages using conventional commits format:
   - `feat:` for new features
   - `fix:` for bug fixes
   - `docs:` for documentation changes
   - `style:` for theme/styling changes
   - `refactor:` for code refactoring
   - `test:` for testing changes
   - `chore:` for maintenance tasks
3. **Commit**: Execute the commit with the generated message
4. **Format**: Use format like `type(scope): description` where scope is optional

### Code Quality Standards

- Validate JSON syntax in theme files
- Ensure all required package.json fields are present
- Follow semantic versioning for releases
- Maintain clean, documented code structure

### Common Issues to Watch For

- Missing color definitions causing fallbacks to default theme
- Insufficient contrast ratios for accessibility
- Inconsistent color usage across similar UI elements
- Missing theme coverage for new VS Code features

## Resources

- [VS Code Theme Color Reference](https://code.visualstudio.com/api/references/theme-color)
- [Color Theme Guide](https://code.visualstudio.com/api/extension-guides/color-theme)
- [Extension Marketplace Guidelines](https://code.visualstudio.com/api/working-with-extensions/publishing-extension)

## Development Workflow

1. Set up basic extension structure with package.json
2. Create initial theme variant (Black - completed)
3. Test in Extension Development Host
4. Create additional variants (White, Blue)
5. Ensure consistency across all variants
6. Add comprehensive documentation
7. Prepare for marketplace publication

### Theme Development Roadmap

- [x] NW21 (Moabit) - Soft light theme
- [x] W30 (Schöneberg) - Ultra-dark theme
- [x] SW61 (Kreuzberg) - Blue-tinted dark theme
- [x] SO36 (Kreuzberg) - Medium-dark blue theme with cyan title bar
- [x] SW11 (Kreuzberg) - Limestone-white light theme
- [x] 41 (Steglitz) - Graphite Bierpinsel dark theme
- [x] Major rebrand to Berlin Postal Themes
- [x] Updated documentation with Berlin heritage context
- [ ] Cross-variant consistency testing
- [ ] Accessibility compliance verification
- [ ] Update extension icon to reflect Berlin theme
- [ ] Marketplace publication with new branding

---
*Last updated: September 4, 2026*
*Update these instructions as the project evolves and new requirements emerge.*

## Recent Updates & Decisions

### September 4, 2026 - 41 Theme Added

- **New Theme**: Added 41 (Berlin 41 - Steglitz) as sixth theme variant
- **File**: themes/41-color-theme.json, registered as vs-dark uiTheme
- **Inspiration**: The Bierpinsel tower restaurant on Schloßstraße by Schüler and Schüler-Witte
- **Editor Background**: #2e3133 (graphite grey of the ventilation louvres)
- **Foreground**: #e89279 (salmon-orange of the facade panels)
- **Distinctive Feature**: Signal-red title bar (#e8402c) from the window frames
- **Accessibility**: Colorblind-friendly palette, all syntax tokens at or above WCAG AA contrast
- **package.json**: Version bumped to 3.1.0, added steglitz, bierpinsel and 41 keywords
- **Reasoning**: 41 is the first warm dark variant; W30, SW61 and SO36 are all black or blue

### June 2, 2026 - SW11 Theme Added

- **New Theme**: Added SW11 (Südwest 11 - Kreuzberg) as fifth theme variant
- **File**: themes/sw11-color-theme.json, registered as vs (light) uiTheme
- **Inspiration**: Großbriefverteileramt SW 11 beside Anhalter Bahnhof, warm limestone facade
- **Editor Background**: #f6f3ec (warm limestone white, warmer than NW21 #e8eefe)
- **Distinctive Feature**: Desaturated slate-blue, brick-red and ochre syntax accents
- **package.json**: Version bumped to 2.2.0, added sw11 and sudwest keywords
- **Reasoning**: SW11 fills the warm-light niche; NW21 is cool-light, SW11 is warm-light

### May 10, 2026 - SO36 Theme Added

- **New Theme**: Added SO36 (Südost 36 - Kreuzberg) as fourth theme variant
- **File**: themes/so36-color-theme.json with corrected type from light to dark
- **Distinctive Feature**: Cyan title bar (#00ccff) sets it apart from SW61
- **Editor Background**: #204b81 (medium-dark blue, brighter than SW61 #00205A)
- **package.json**: Registered SO36 as vs-dark uiTheme, updated description and keywords
- **Reasoning**: SO36 is the iconic Kreuzberg postal sub-district, distinct cultural
  identity from SW61 despite both being in Kreuzberg

### May 9, 2026 - Session Initialization

- **Session Start**: Initialized new coding session, reviewed full AGENTS.md and project state
- **Commit Rules Reinforced**: Conventional commits format, max 500 chars, no special characters or quoting, never commit automatically
- **Current Focus**: Cross-variant consistency testing, accessibility compliance, icon update, and marketplace publication remain as next steps
- **Reasoning**: Keeping AGENTS.md up to date with session activity and current project state

### December 19, 2025 - Version 2.0.0 Major Rebrand

- **Major Rebrand**: Complete transformation from "Super Theme Collection" to "Berlin Postal Themes"
- **Extension Rename**: Changed package name from "super-themes" to "berlin-postal-themes"
- **Theme Renames**:
  - Super Light → NW21 (Nordwest 21 - Moabit)
  - Super Black → W30 (West 30 - Schöneberg)
  - Super Blue → SW61 (Südwest 61 - Kreuzberg)
- **Theme Removed**: Discontinued Super White theme to focus on three distinct district themes
- **File Renames**: All theme files renamed to match postal district codes (nw21, w30, sw61)
- **Conceptual Shift**: Themes now inspired by historic West Berlin postal districts (Postzustellbezirke) from 1960s-1993
- **Documentation Overhaul**: Complete rewrite of README and AGENTS.md with Berlin heritage context
- **Historical Context**: Added information about Berlin Postzustellbezirke and district characteristics
- **Breaking Changes**: Users will need to re-select themes after update due to name changes
- **Reasoning**: Original "Super" theme names were too generic and likely already taken on marketplace. Berlin postal district concept provides unique branding, cultural depth, and memorable identity while maintaining the existing color palettes and technical quality.

### December 12, 2025 - Version 1.2.2 Update

- **Version Bump**: Updated version from 1.2.1 to 1.2.2
- **Reasoning**: Preparing for next release iteration

### December 12, 2025 - Version 1.2.1 Update

- **Version Bump**: Updated version from 1.2.0 to 1.2.1
- **Theme Refinement**: Removed italic formatting from comments in Super Light theme for better readability
- **Reasoning**: Minor styling improvement to enhance code readability in the Super Light theme variant

### December 12, 2025 - Version 1.2.0 Update

- **Version Documentation**: Updated AGENTS.md to reflect current version 1.2.0 from package.json
- **Super Light Theme**: Added documentation for the fourth theme variant (Super Light) with soft blue-tinted backgrounds (#e8eefe)
- **Extension Name Correction**: Updated extension name from "super-theme-collection" to "super-themes" to match package.json
- **Theme Count**: Updated from three to four theme variants throughout documentation
- **Timestamp Update**: Updated last modified date to December 12, 2025
- **Reasoning**: Synchronizing documentation with actual codebase state, ensuring all four themes are properly documented for marketplace publication

### September 17, 2025 - Version 1.1.2 Update

- **Version Bump**: Updated version from 1.1.1 to 1.1.2 across package.json, README.md, and copilot instructions
- **Extension Icon**: Added super-themes.png as extension icon for marketplace presentation
- **Changelog Addition**: Added version 1.1.2 entry to README with icon addition notes
- **Documentation Updates**: Updated Next Steps to mark icon creation as complete
- **Reasoning**: Completing marketplace readiness with custom branding on doc/add-icon branch

### September 17, 2025 - Version 1.1.1 Update

- **Version Bump**: Updated version from 1.1.0 to 1.1.1 across package.json, README.md, and copilot instructions
- **Documentation Improvements**: Added screenshots to README and removed Contributing section
- **Changelog Addition**: Added version 1.1.1 entry to README with documentation improvement notes
- **Reasoning**: Finalizing documentation with visual screenshots and cleaner structure on doc/add-screenshots branch

### September 17, 2025 - Version 1.1.0 Update

- **Version Bump**: Updated version from 1.0.10 to 1.1.0 across package.json, README.md, and copilot instructions
- **Changelog Addition**: Added version 1.1.0 entry to README with preparation notes for color theme improvements
- **Documentation Updates**: Updated copilot instructions to reflect new version number
- **Reasoning**: Preparing for upcoming color theme improvements and bug fixes on the fix/outdated-colors branch

### September 17, 2025 - Version 1.0.10 Update

- **Version Bump**: Updated version from 1.0.9 to 1.0.10 across package.json, README.md, and documentation
- **Changelog Addition**: Added version 1.0.10 entry to README with workflow improvement notes
- **Documentation Updates**: Updated workflow README examples to use v1.0.10
- **Reasoning**: Preparing for release with modernized GitHub Actions workflow and fixed permissions

### September 17, 2025

- **Theme Name Update**: Changed from "Ultralove" to "Super" throughout documentation to match actual workspace implementation
- **Version Correction**: Updated version reference from 0.1.0 to 1.0.7 to reflect current package.json
- **Roadmap Status**: Marked Super White and Super Blue as complete since all three theme files exist in the workspace
- **Reasoning**: Aligned documentation with actual codebase state for consistency and accuracy
