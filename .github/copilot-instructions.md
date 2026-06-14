# Copilot Instructions

forge-text is a text processing and content analysis module. It provides skills for text transformation, grammar correction, content analysis, and document conversion.

## Structure

- `skills/` -- skill directories, each with SKILL.md (instructions) and SKILL.yaml (sidecar metadata)
- `defaults.yaml` -- module config stub; the forge CLI embeds provider defaults
- `module.yaml` -- module metadata (name, version, description)

## Conventions

- Skill names use PascalCase matching directory names
- SKILL.yaml carries `sources:` and provider config -- never duplicates name/description from SKILL.md
- `config.yaml` (gitignored) overrides `defaults.yaml` (committed)

## Build

```bash
make install     # deploy skills via forge CLI and activate git hooks
make validate    # module structure and code checks
make release     # build release tarball
make clean       # remove build artifacts
```
