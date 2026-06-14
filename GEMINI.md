# GEMINI.md

This file provides instructional context for the Gemini AI agent when working with the **forge-text** codebase.

## Project Overview

**forge-text** is a text processing and content analysis module for the Forge ecosystem. It provides skills covering text transformation, grammar correction, content analysis, and document conversion.

### Core Responsibilities

- **Text Transformation:** Skills for simplifying, expanding, condensing, and cleaning text.
- **Grammar and Style:** Fixing grammar, adding emojis, rewriting as tweets.
- **Content Analysis:** Generating glossaries, outlines, and identifying high-impact changes.
- **Document Conversion:** Rendering markdown to PDF via pandoc, translating between languages.

## Building and Testing

```bash
make install          # deploy skills via forge CLI and activate git hooks
make validate         # module structure and code checks
make release          # build release tarball
make clean            # remove build artifacts
```

## Skills

| Skill | Responsibilities |
|:------|:-----------------|
| `CleanText` | URL, HTML, and noise stripping |
| `Emojify` | Context-appropriate emoji insertion |
| `ExplainSimply` | Rewriting complex content in simple, accessible language |
| `FixGrammar` | Grammar and spelling correction |
| `GenerateGlossary` | Alphabetical glossary creation |
| `GenerateOutline` | Hierarchical outline generation |
| `HighImpactChanges` | Document change impact analysis |
| `MakeLonger` | Text expansion to roughly double length |
| `MakeShorter` | Text condensation to roughly half length |
| `MarkdownExtract` | Batch document-to-markdown conversion (docx, rtf, odt, html) |
| `Pandoc` | Document format conversion via pandoc |
| `RewriteAsTweet` | Content rewriting as tweet or thread |
| `Translate` | Text translation to any target language |

## Skill File Convention

Each skill directory contains:

- `SKILL.md` -- AI instructions with YAML frontmatter (name, description, version)
- `SKILL.yaml` -- sidecar metadata (sources, provider-specific config)
- Optional `sample.md` demo files

## Configuration

- `defaults.yaml`: module config stub (committed)
- `config.yaml`: user overrides (gitignored), same structure as defaults
- `module.yaml`: module metadata (name, version, description)

## Development Conventions

- **Skill naming**: PascalCase directories matching `name:` in SKILL.md frontmatter
- **Provider routing**: all skills deploy to all providers; the forge CLI's embedded defaults define provider targets
- **Deployment**: [forge CLI](https://github.com/N4M3Z/forge-cli) assembles and deploys skills per provider
