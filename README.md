# forge-text

Text processing and content analysis skills for AI coding tools.

## What Is This?

A collection of text transformation skills that work with [Claude Code](https://claude.ai/code), [Gemini CLI](https://github.com/google-gemini/gemini-cli), [Codex CLI](https://github.com/openai/codex), and [OpenCode](https://opencode.ai). Each skill is a plain text file that teaches your AI assistant a new capability.

## Available Skills

| Skill | What it does |
|-------|-------------|
| `/CleanText` | Strips URLs, HTML tags, and noise from text |
| `/Emojify` | Adds context-appropriate emojis at natural break points |
| `/ExplainSimply` | Rewrites complex content in simple, accessible language |
| `/FixGrammar` | Fixes grammar and spelling, preserves everything else |
| `/GenerateGlossary` | Creates an alphabetical glossary of key terms |
| `/GenerateOutline` | Generates a hierarchical outline from any document |
| `/HighImpactChanges` | Identifies the highest-impact changes in a document |
| `/MakeLonger` | Expands text to roughly twice its length |
| `/MarkdownExtract` | Batch-converts a folder of source documents to canonical markdown |
| `/MakeShorter` | Condenses text to roughly half its length |
| `/Pandoc` | Renders markdown documents to PDF via pandoc |
| `/RewriteAsTweet` | Rewrites content as a tweet or tweet thread |
| `/Translate` | Translates text into any target language |

## Quick Start

```bash
git clone https://github.com/N4M3Z/forge-text.git
cd forge-text
make install
```

`make install` deploys every skill to all providers via the [forge CLI](https://github.com/N4M3Z/forge-cli). If `forge` is missing, ask your AI assistant to execute [INSTALL.md](INSTALL.md), or copy `skills/` into your provider config directory (e.g., `~/.claude/skills/`) directly.

Skills are then available as slash commands in Claude Code.

## How It Works

Each skill is a `SKILL.md` file with YAML frontmatter (name, description, version) and instructions. Your AI tool reads the description to decide when to activate the skill, then follows the instructions when you invoke it.

```
skills/
  CleanText/     SKILL.md + SKILL.yaml
  Emojify/       SKILL.md + SKILL.yaml
  ...
```

All skills deploy to all providers. Create `config.yaml` (gitignored) to override the defaults in `defaults.yaml`.

## Requirements

- [Git](https://git-scm.com/downloads)
- [forge CLI](https://github.com/N4M3Z/forge-cli) (deployment tooling)
- An AI coding tool: Claude Code, Gemini CLI, Codex CLI, or OpenCode

## License

[EUPL 1.2](LICENSE)
