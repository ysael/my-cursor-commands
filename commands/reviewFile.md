# Review File with Git Diff

📝 **Command:** `@reviewfile [filepath]`

**Version:** 1.0.0

AI-powered file review using git diff to analyze changes

## Instructions

When invoked with `@reviewfile` (optionally with a file path), automatically (without prompting the user):

### 1. Determine File to Review

- If a file path is provided as an argument, use that file
- If no file path is provided, use the currently open/focused file from the editor context
- If no file can be determined, ask the user which file to review

### 2. Get Git Diff for File

- Run `git diff <filepath>` to get unstaged changes for the file
- Run `git diff --staged <filepath>` to get staged changes for the file
- Run `git diff HEAD <filepath>` to get all changes (staged + unstaged) for the file
- Run `git log -1 --oneline <filepath>` to see the last commit that touched this file (for context)
- If the file is not tracked by git, check if it's a new file with `git status --porcelain <filepath>`

### 3. Analyze Changes

Review the git diff and provide:

- **Summary**: Brief overview of what changed in this file (1-2 sentences)
- **Key Changes**: Bullet points highlighting the most significant modifications:
  - New features or functionality added
  - Bug fixes or corrections
  - Refactoring or code improvements
  - Breaking changes or API modifications
  - Performance optimizations
- **Potential Issues**: Any concerns, risks, or things to watch out for:
  - Missing error handling
  - Potential bugs or edge cases
  - Code quality concerns
  - Testing gaps
  - Breaking changes or migration needs
- **Suggestions**: Optional improvements or follow-up actions

### 4. Output Format

Display the review in a clear, structured format:

```markdown
## File Review: <filepath>

### Summary

[Brief overview of changes]

### Key Changes

- [Significant change 1]
- [Significant change 2]

### Potential Issues

- [Issue or concern 1]
- [Issue or concern 2]

### Suggestions

- [Suggestion 1]
- [Suggestion 2]
```

## Key Guidelines

- Automatically fetch git diff information without user prompts
- Focus on meaningful changes - don't list every single line modification
- Be concise but thorough - highlight what matters
- Identify potential problems proactively
- Provide actionable feedback when possible
- If the file has no changes, indicate that clearly
- If the file is new (untracked), note that and review the entire file content
- Use code references when pointing to specific lines or sections

