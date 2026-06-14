# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/).

## [Unreleased]

### Added

- MarkdownExtract: batch-convert a folder of source documents (docx, rtf, odt, html) to canonical markdown
- LICENSE (EUPL-1.2), CHANGELOG, CODEOWNERS, CONTRIBUTING, SECURITY
- Git hooks (`.githooks/pre-commit`) with prek, forge, and hash-verified fallback validation
- CI workflows: quality gate on push/PR, release on version tags
- Markdown schemas for the repo root and `skills/`

### Changed

- Module tooling migrated from the forge-lib submodule to the forge CLI: `make install` now runs `forge install --target ~`, validation runs through `.githooks/pre-commit`
- `defaults.yaml` reduced to a config stub; skill deployment derives from `skills/` and the forge CLI's embedded provider defaults

### Removed

- forge-lib submodule (`lib/`) and `.gitmodules`
- VERIFY.md; verification is embedded in INSTALL.md's DONE WHEN section
- Tracked provider directory placeholders; provider directories are now fully gitignored

## [0.1.0] - 2026-02-22

### Added

- Text processing skills: CleanText, Emojify, ExplainSimply, FixGrammar, GenerateGlossary, GenerateOutline, HighImpactChanges, MakeLonger, MakeShorter, Pandoc, RewriteAsTweet, Translate
- Multi-provider deployment: Claude Code, Gemini CLI, Codex, OpenCode
