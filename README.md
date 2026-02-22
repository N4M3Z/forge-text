# forge-text

Text processing and content analysis skills for AI coding tools.

## What Is This?

A collection of 12 text transformation skills that work with [Claude Code](https://claude.ai/code), [Gemini CLI](https://github.com/google-gemini/gemini-cli), [Codex CLI](https://github.com/openai/codex), and [OpenCode](https://opencode.ai). Each skill is a plain text file that teaches your AI assistant a new capability.

## Available Skills

| Skill | What it does |
|-------|-------------|
| `/CleanText` | Strips URLs, HTML tags, and noise from text |
| `/Emojify` | Adds context-appropriate emojis at natural break points |
| `/ExplainSimply` | Rewrites complex content in simple, accessible language |
| `/FixGrammar` | Fixes grammar and spelling, preserves everything else |
| `/GenerateGlossary` | Creates an alphabetical glossary of key terms |
| `/GenerateOutline` | Generates a hierarchical outline from any document |
| `/HighImpactChanges` | Identifies the 10 highest-impact changes in a document |
| `/MakeLonger` | Expands text to roughly twice its length |
| `/MakeShorter` | Condenses text to roughly half its length |
| `/Pandoc` | Renders markdown documents to PDF via pandoc |
| `/RewriteAsTweet` | Rewrites content as a tweet or tweet thread |
| `/Translate` | Translates text into any target language |

## Quick Start

```bash
git clone https://github.com/N4M3Z/forge-text.git
cd forge-text
git submodule update --init lib
make -C lib build
make install
```

Skills are now available as slash commands in Claude Code. For other providers, `make install` deploys to their directories too.

## How It Works

Each skill is a `SKILL.md` file with YAML frontmatter (name, description, version) and instructions. Your AI tool reads the description to decide when to activate the skill, then follows the instructions when you invoke it.

```
skills/
  CleanText/     SKILL.md + SKILL.yaml
  Emojify/       SKILL.md + SKILL.yaml
  ...
```

`defaults.yaml` controls which skills deploy to which providers. All 12 skills deploy to all 4 providers by default.

## Submodule Integration

To add forge-text to an existing forge setup:

```bash
git submodule add https://github.com/N4M3Z/forge-text.git modules/forge-text
cd modules/forge-text && make install SCOPE=workspace
```

### Makefile Integration

```makefile
install-forge-text:
	@$(MAKE) -C modules/forge-text install SCOPE=$(SCOPE)
```

## Requirements

- [Git](https://git-scm.com/downloads)
- [Rust](https://rustup.rs/) (to build forge-lib deployment tools)
- An AI coding tool: Claude Code, Gemini CLI, Codex CLI, or OpenCode

## License

[EUPL 1.2](LICENSE)
