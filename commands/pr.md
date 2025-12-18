# Generate PR Description

📝 **Command:** `@prdescription`

**Version:** 2.0.0

AI-powered PR description generator using @prdescription command

## Instructions

When invoked with `@prdescription`, automatically (without prompting the user):

### 1. Get Git Context

- Run `git branch --show-current` to get the current branch name
- Run `git diff main...HEAD` (or `git diff master...HEAD` if main doesn't exist) to get all changes between the current branch and base branch
- Run `git diff main...HEAD --stat` to get a summary of changed files (for reference only, don't show this to user)
- Run `git log main..HEAD --oneline` to see commit messages (for context)
- Do NOT ask the user for any git information - get it automatically

### 2. Load PR Template

- Read the template from `.github/pull_request_template.md`
- The template structure is: PR Checklist, Summary, Implementation Notes, How to tell that it works

### 3. Generate PR Description

- Analyze the git diff to understand what the PR does
- Write a **VERY BRIEF Summary** (1 sentence ideal, 2 sentences absolute max) that explains what the PR does and what problem it solves (NOT a list of files changed, NOT implementation details)
- Write **VERY BRIEF Implementation Notes** (omit the entire section unless there's a critical gotcha):
  - Only include the "## Implementation Notes" section if there's a non-obvious gotcha that will break things if reviewers miss it
  - If included, maximum 1 bullet point if absolutely necessary
  - Do NOT include: standard patterns, obvious refactors, routine changes, design decisions that are self-evident
  - **Do NOT include an empty "## Implementation Notes" section** - omit it entirely if there are no notes
- Write **How to tell that it works** with 1-2 brief steps maximum (omit if obvious from the summary)

### 3.1 Implementation Notes Style

When Implementation Notes are necessary (only for critical gotchas), follow this style:

- **Format**: Use bullet points, maximum 1 bullet point
- **Tone**: Direct, technical, and concise - no fluff or explanations of obvious patterns
- **Content**: Focus exclusively on non-obvious gotchas that could break things if missed
- **What to include**:
  - Critical technical details that aren't obvious from the code
  - Non-obvious side effects or breaking changes
  - Important assumptions or dependencies reviewers must know
- **What to exclude**:
  - Standard patterns (e.g., "uses React hooks", "awaits async functions")
  - Obvious refactors or routine changes
  - Self-evident design decisions
  - File-by-file explanations
  - Common coding practices
- **Example style**: "The new validation runs before the existing check, so invalid data now fails earlier in the flow."

### 4. Output as Markdown File

- Generate the complete PR description following the template structure
- Use the exact template format from `.github/pull_request_template.md`
- **Omit the "## Implementation Notes" section entirely if there are no notes** - do not include an empty section
- Save the PR description to a markdown file: `PR_DESCRIPTION_<branch_name>.md` in the repository root
- Also display the markdown content in the response so the user can see it
- Keep everything extremely brief - aim for the shortest possible description that still conveys the essential information

## Key Guidelines

- Automatically fetch all git information without user prompts
- **Summary: 1 sentence ideal, 2 sentences absolute maximum** - high-level only, no file-by-file breakdown, no implementation details
- **Implementation Notes: Omit the entire section unless there's a critical gotcha** - do not include an empty section, maximum 1 bullet point if absolutely necessary
- **How to tell that it works: 1-2 steps maximum, omit if obvious**
- Be extremely concise - omit obvious details, routine changes, standard patterns, and self-evident information
- Avoid listing files changed, explaining modifications, describing common coding practices, or including anything that's obvious from the code
- When in doubt, omit it - less is more
- Output must be valid markdown following the PR template structure

