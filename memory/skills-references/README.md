# Skills References - Large Files

These large reference files were moved from ~/.hermes/skills/ to Obsidian to reduce Hermes memory footprint.

## Files Moved

1. **llms-full.md** (1.1MB)
   - Original: ~/.hermes/skills/mlops/training/unsloth/references/llms-full.md
   - Content: Complete LLMs reference documentation
   - Skill: mlops/training/unsloth

2. **llms-txt.md** (795KB)
   - Original: ~/.hermes/skills/mlops/training/unsloth/references/llms-txt.md
   - Content: LLMs reference in plain text format
   - Skill: mlops/training/unsloth

## Why Moved?

- These files are >500KB each, contributing ~1.9MB to Hermes memory
- They are reference documentation, not executable code
- Session search in SQLite provides better retrieval than full text loading
- Obsidian provides better organization and search for reference materials

## Access Pattern

When working with the `unsloth` skill:
1. Load skill normally via `skill_view(name='mlops/training/unsloth')`
2. References will point here via relative paths if configured
3. Use Obsidian search to find specific LLM reference content

## Session Created
- May 21, 2026