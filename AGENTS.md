# VS Code Theme Development - Copilot Instructions

## Project Overview
This is a VS Code theme development project for creating a family of custom Visual Studio Code color themes. The project focuses on developing cohesive, aesthetically pleasing themes that enhance the coding experience across different environments and preferences.

### Theme Variants Planned
- **Super Black** (Complete) - Ultra-dark theme with deep black backgrounds (#010409) for low-light coding
- **Super White** (Complete) - Clean light theme with high contrast for bright environments
- **Super Light** (Complete) - Soft light theme with gentle blue-tinted backgrounds (#e8eefe) for comfortable daylight coding
- **Super Blue** (Complete) - Blue-tinted theme for a calming coding experience

### Current Status
All four theme variants are implemented and functional. The extension is ready for testing, packaging, and potential marketplace publication.

## Project Structure
```
vscode-theme/
├── package.json                          # Extension manifest (Complete)
├── README.md                            # Project documentation (Complete)
├── LICENSE                              # MIT License
├── .copilot-instructions.md             # AI assistant guidelines
├── .gitignore                           # Git ignore file with VSIX exclusions
├── themes/                              # Theme definition files
│   ├── super-black-color-theme.json  # Complete - Ultra-dark theme
│   ├── super-white-color-theme.json  # Complete - Light theme
│   ├── super-light-color-theme.json  # Complete - Soft light theme
│   └── super-blue-color-theme.json   # Complete - Blue-tinted theme
├── .github/                             # GitHub configuration
│   └── workflows/                       # GitHub Actions workflows
│       └── build-vsix.yml               # Automated VSIX build workflow
├── dist/                                # Build output directory (gitignored)
├── .vscode/                             # VS Code workspace settings (Optional)
│   ├── launch.json                      # Debug configuration for testing
│   └── settings.json                    # Workspace settings
├── assets/                              # Additional assets (Optional)
│   └── screenshots/                     # Theme preview images for marketplace
├── icon.png                             # Extension icon (Optional)
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
- Theme files: `super-[variant]-color-theme.json`
- Variants: `black`, `white`, `light`, `blue`
- Use kebab-case for file names
- Maintain consistent naming across all theme variants

### Theme Variant Guidelines
- **Black Variant**: Ultra-dark backgrounds (#010409), high contrast, minimal eye strain
- **White Variant**: Clean light backgrounds, sharp contrast, bright environment optimized
- **Light Variant**: Soft light backgrounds (#e8eefe), gentle blue tint, comfortable daylight coding
- **Blue Variant**: Blue-tinted backgrounds, calming atmosphere, balanced contrast
- **Consistency**: Maintain similar syntax highlighting patterns across variants
- **Accessibility**: Ensure all variants meet WCAG contrast requirements

### Current Theme Specifications
**Super Black Theme:**
- Editor background: #010409 (ultra-dark black)
- Foreground: #c9d1d9 (light gray)
- Cursor: #58a6ff (blue accent)
- Line highlight: #21262d
- Selection: #264f78
- Type: vs-dark

**Super White Theme:**
- Editor background: #ffffff (pure white)
- Type: vs (light theme)
- High contrast design for bright environments

**Super Light Theme:**
- Editor background: #e8eefe (soft blue-tinted white)
- Foreground: #1f2328 (dark gray)
- Cursor: #0969da (blue accent)
- Type: light
- Gentle on eyes for daylight coding

**Super Blue Theme:**
- Blue-tinted color scheme
- Type: vs-dark
- Calming blue accents throughout interface

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
- **Keywords**: Include relevant theme-related keywords for discoverability
- **Extension Name**: "super-themes" with display name "Super Theme Collection"
- **Version**: Currently at 1.2.1, ready for marketplace publication

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
- [x] Super Black - Core dark theme
- [x] Super White - Light variant
- [x] Super Light - Soft light variant
- [x] Super Blue - Blue-tinted variant
- [ ] Cross-variant consistency testing
- [ ] Accessibility compliance verification
- [ ] Marketplace assets and documentation

---
*Last updated: December 12, 2025*
*Update these instructions as the project evolves and new requirements emerge.*

## Recent Updates & Decisions

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
