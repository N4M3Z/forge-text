# Verify

Instructions for the AI agent. Run these checks when the user asks to verify their setup, or when something isn't working.

## Check 1: Directory Structure

Verify the expected files exist:

```
.claude-plugin/plugin.json    -- plugin manifest (skills discovery)
CLAUDE.md                     -- AI ground rules
skills/*/SKILL.md             -- 12 skill files
```

If `.claude-plugin/plugin.json` is missing, the plugin won't load. Recreate it:

```json
{
    "name": "forge-text",
    "version": "0.1.0",
    "description": "Text processing and content analysis skills for AI coding tools",
    "skills": ["./skills"]
}
```

## Check 2: Skills Discovery

List the contents of `skills/`. There should be 12 skill directories, each containing a `SKILL.md`. If any are missing, report which ones.

Expected skills: CleanText, Emojify, ExplainSimply, FixGrammar, GenerateGlossary, GenerateOutline, HighImpactChanges, MakeLonger, MakeShorter, Pandoc, RewriteAsTweet, Translate.

## Check 3: Deployment Verification

After `make install`, check that skills deployed to provider directories:

```bash
ls .claude/skills/
ls .gemini/skills/
ls .codex/skills/
ls .opencode/skills/
```

Each should contain 12 skill directories matching the source.

## Reporting Results

After running all checks, present results concisely:

- **Pass**: "Your setup looks good. All 12 skills are in place."
- **Issues found**: List what's wrong and offer to fix each one.
