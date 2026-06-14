# forge-text

> Text processing and content analysis skills for AI coding tools. Teaches AI assistants to clean, transform, analyze, and convert text.

*This file follows the [install.md](https://github.com/mintlify/install-md) standard: structured instructions for AI agents to execute autonomously. Human readers: see [README.md](README.md) for conventional documentation.*

I want you to install forge-text for me. Execute all the steps below autonomously.

## OBJECTIVE

Deploy forge-text skills to all AI providers via Makefile.

## DONE WHEN

- `make validate` passes
- `ls ~/.claude/skills/FixGrammar/SKILL.md` confirms skill deployment
- `git config core.hooksPath` returns `.githooks`

## Prerequisites

- Claude Code (or another AI provider CLI)
- forge-cli (see step below)

Without forge: copy `skills/` into the provider config directory (e.g., `~/.claude/skills/`) directly.

## TODO

- [ ] Clone the repository
- [ ] Install forge-cli if missing
- [ ] Run `make install` to deploy
- [ ] Verify skill deployment
- [ ] Verify git hooks are active

## Steps

### Clone

```sh
git clone https://github.com/N4M3Z/forge-text.git
cd forge-text
```

If already cloned, pull latest:

```sh
git pull
```

### Install forge-cli (if missing)

```sh
git clone https://github.com/N4M3Z/forge-cli.git
cd forge-cli
make install
cd ../forge-text
```

### Install

```sh
make install
```

### Verify skill deployment

```sh
ls ~/.claude/skills/FixGrammar/SKILL.md
```

### Verify git hooks

```sh
git config core.hooksPath
```

Should return `.githooks`.

EXECUTE NOW: Complete the above TODO list.
