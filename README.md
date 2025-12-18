# My Cursor Commands

A collection of custom Cursor AI commands to enhance your development workflow. These commands provide AI-powered assistance for code visualization, PR generation, file reviews, code simplification, and TypeScript error fixing.

## Installation

To use these commands in your project:

1. **Clone or download this repository**
   ```bash
   git clone https://github.com/yourusername/my-cursor-commands.git
   # or download as ZIP and extract
   ```

2. **Copy commands to your project**
   - Navigate to your project root
   - Create the `.cursor/commands/` directory if it doesn't exist:
     ```bash
     mkdir -p .cursor/commands
     ```
   - Copy the command files from this repository:
     ```bash
     cp my-cursor-commands/commands/*.md .cursor/commands/
     ```

3. **Verify installation**
   - The commands should now be available in Cursor when you type `@` followed by the command name

## Available Commands

### `@mermaid [filepath]`

**Version:** 1.0.0

Generate Mermaid diagrams from your code to visualize structure, data flow, and control flow.

**Features:**
- Automatically analyzes code structure
- Generates flowcharts, sequence diagrams, class diagrams, or state diagrams
- Creates markdown files in `docs/diagrams/`
- Supports single files or multiple files

**Usage:**
```
@mermaid
@mermaid app/components/UserProfile.tsx
```

**Example Output:**
- Creates a diagram file at `docs/diagrams/UserProfile_diagram.md`
- Displays the diagram in the response

---

### `@prdescription`

**Version:** 2.0.0

Automatically generate concise PR descriptions from your git changes.

**Features:**
- Automatically fetches git context (branch, diff, commits)
- Uses your PR template from `.github/pull_request_template.md`
- Generates brief, focused descriptions
- Saves output to `PR_DESCRIPTION_<branch_name>.md`

**Usage:**
```
@prdescription
```

**Requirements:**
- Must be run from a git repository
- Requires `.github/pull_request_template.md` template file

**Example Output:**
- Generates PR description following your template
- Saves to `PR_DESCRIPTION_feature-branch.md`

---

### `@reviewfile [filepath]`

**Version:** 1.0.0

Review file changes using git diff to analyze modifications, identify issues, and suggest improvements.

**Features:**
- Analyzes git diff for the specified file
- Identifies key changes, potential issues, and suggestions
- Works with staged, unstaged, or all changes
- Handles new untracked files

**Usage:**
```
@reviewfile
@reviewfile app/components/Button.tsx
```

**Example Output:**
- Summary of changes
- Key modifications highlighted
- Potential issues flagged
- Actionable suggestions

---

### `@simplify [filepath]`

**Version:** 1.0.0

Get AI-powered suggestions to simplify and refactor your code using functional programming patterns.

**Features:**
- Identifies complexity hotspots
- Suggests functional programming improvements
- React-specific state management simplifications
- Prioritizes high-impact, low-effort changes

**Usage:**
```
@simplify
@simplify app/utils/dataProcessor.ts
```

**Example Output:**
- Code simplification suggestions
- Before/after examples
- Functional programming improvements
- State management optimizations (for React)

---

### `@typescriptError [filepath]`

**Version:** 1.0.0

Automatically detect, analyze, and fix TypeScript errors following best practices.

**Features:**
- Automatically detects TypeScript errors
- Analyzes context and root causes
- Proposes fixes following codebase conventions
- Applies fixes directly to files
- Verifies fixes don't introduce new errors

**Usage:**
```
@typescriptError
@typescriptError app/components/Form.tsx
```

**Example Output:**
- Error analysis with root causes
- Proposed fixes with explanations
- Automatic fix application
- Verification of fixes

## Usage Tips

1. **Command Context**: Most commands work with the currently open file if no filepath is provided
2. **Git Integration**: Commands like `@prdescription` and `@reviewfile` require git repository context
3. **File Paths**: Use relative paths from your project root when specifying file paths
4. **Multiple Files**: Some commands (like `@mermaid`) support analyzing multiple files or directories

## Project Structure

```
my-cursor-commands/
├── README.md
├── LICENSE
├── .gitignore
└── commands/
    ├── mermaid.md
    ├── pr.md
    ├── reviewFile.md
    ├── simplify.md
    └── typescriptError.md
```

## Contributing

Contributions are welcome! If you'd like to add new commands or improve existing ones:

1. Fork this repository
2. Create a new command file in the `commands/` directory
3. Follow the existing command format and structure
4. Update this README with your new command
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

If you encounter any issues or have questions about using these commands:

1. Check the command documentation in the `commands/` directory
2. Review the examples in this README
3. Open an issue on GitHub

## Version History

- **v1.0.0** - Initial release with 5 core commands
  - Mermaid diagram generator
  - PR description generator (v2.0.0)
  - File review with git diff
  - Code simplification suggestions
  - TypeScript error fixer

