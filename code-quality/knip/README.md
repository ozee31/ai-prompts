# Knip

**Purpose**: Safely remove unused code identified by [Knip](https://knip.dev) using AI-assisted verification.

**Why not just use `knip --fix`?**
- `--fix` blindly removes everything flagged (including false positives)
- No validation after changes (TypeScript, ESLint, tests)
- Can break production code silently

**What the AI agent does**:
- ✅ Verifies each item with `grep` before removal
- ✅ Distinguishes test-only vs production usage
- ✅ Adds `@internal` tag for exports used internally but exported for testing
- ✅ Runs validation suite after each change
- ✅ Commits atomically with proper messages
- ✅ Stops and asks if unsure

**Usage**:
1. Run Knip to identify issues
npx knip --production --strict
2. Give the prompt to your AI agent with the Knip output
3. Let the agent iterate through each item safely

**Prompt**:
https://github.com/ozee31/ai-prompts/blob/main/code-quality/knip/prompt.md
