# Copilot Instructions

forge-text is a text processing and content analysis module. It provides 12 skills for text transformation, grammar correction, content analysis, and document conversion.

## Structure

- `skills/` -- 12 skill directories, each with SKILL.md (instructions) and SKILL.yaml (sidecar metadata)
- `defaults.yaml` -- Skill roster, provider model mapping
- `lib/` -- forge-lib git submodule (Rust binaries for deployment)

## Conventions

- Skill names use PascalCase matching directory names
- SKILL.yaml carries `sources:` and provider config -- never duplicates name/description from SKILL.md
- `config.yaml` (gitignored) overrides `defaults.yaml` (committed)

## Build

```bash
make install    # deploy skills to all providers
make verify     # check deployment
make test       # validate-module convention checks
make lint       # mdschema + shellcheck
```
