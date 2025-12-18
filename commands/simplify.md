# Simplify Code

📝 **Command:** `@simplify [filepath]`

**Version:** 1.0.0

AI-powered code simplification and refactoring suggestions

## Instructions

When invoked with `@simplify` (optionally with a file path), automatically (without prompting the user):

### 1. Determine File to Analyze

- If a file path is provided as an argument, use that file
- If no file path is provided, use the currently open/focused file from the editor context
- If no file can be determined, ask the user which file to simplify
- Read the entire file content to understand the full context

### 2. Analyze Code Structure

Examine the code to identify:

- Complexity hotspots (nested conditionals, deep callbacks, long functions)
- State management patterns (if React)
- Type definitions and usage
- Function composition opportunities
- Code duplication
- Unnecessary abstractions or over-engineering

### 3. Generate Simplification Suggestions

Based on the code type, provide targeted refactoring suggestions:

#### For TypeScript (Non-React):

**Functional Programming Approach:**

- Extract pure functions from impure code
- Replace imperative loops with functional methods (map, filter, reduce, etc.)
- Use function composition instead of nested calls
- Prefer immutable data transformations
- Extract complex logic into small, testable functions
- Use higher-order functions to reduce duplication
- Replace classes with functions and data structures where appropriate
- Use type inference to reduce verbosity
- Simplify conditional logic with early returns and guard clauses
- Extract complex expressions into named variables

**Readability Improvements:**

- Break down long functions into smaller, single-purpose functions
- Use descriptive function and variable names
- Reduce nesting levels (extract functions, use early returns)
- Simplify type definitions (use type inference, avoid over-typing)
- Remove unnecessary abstractions
- Consolidate duplicate code

#### For React Components:

**Functional Programming Approach:**

- Extract pure functions from components (business logic, data transformations)
- Replace imperative loops with functional methods (map, filter, reduce, etc.) in JSX and data processing
- Use function composition for data transformations
- Prefer immutable data transformations (avoid mutating state directly)
- Extract complex logic into small, testable pure functions
- Use higher-order functions and custom hooks to reduce duplication
- Simplify conditional logic with early returns and guard clauses
- Extract complex expressions into named variables or functions
- Use function composition for event handlers and data flow
- Prefer declarative patterns over imperative ones

**State Management Simplification:**

- Consolidate related state into single state objects or use `useReducer` for complex state
- Extract state logic into custom hooks (functional approach)
- Use derived state instead of storing redundant state (compute from existing state)
- Minimize the number of state variables
- Make state updates predictable (pure functions for state updates)
- Use `useMemo` and `useCallback` judiciously (only when necessary)
- Prefer local state over prop drilling when appropriate
- Extract stateful logic from components into hooks (functional separation)

**Component Structure:**

- Break down large components into smaller, focused components
- Extract complex JSX into separate components or helper functions (pure functions)
- Simplify conditional rendering (use early returns, extract to pure functions)
- Remove unnecessary `useEffect` dependencies or split effects
- Prefer server components when possible (Next.js)
- Extract business logic from components into pure functions
- Use composition over complex prop passing
- Make components pure when possible (minimize side effects)

**General React Simplifications:**

- Remove unnecessary `useState` calls (use derived values computed functionally)
- Simplify event handlers (extract to named pure functions)
- Reduce prop drilling (consider context or component composition)
- Make component data flow unidirectional and predictable
- Extract constants and configuration outside components
- Use functional patterns for data transformations (map, filter, reduce)

### 4. Output Format

Provide suggestions in a clear, actionable format:

```markdown
## Code Simplification Suggestions: <filepath>

### Summary

[Brief overview of the main simplification opportunities]

### Key Simplifications

#### 1. [Specific Area/Pattern to Simplify]

**Current Issue:** [What makes it complex]
**Suggestion:** [How to simplify it]
**Benefits:** [Why this helps]

[Code example showing before/after if helpful]

#### 2. [Next Area/Pattern]

...

### Functional Programming Improvements

- [Specific suggestion 1 - applies to both TypeScript and React]
- [Specific suggestion 2]

### State Management Improvements (React)

- [Specific suggestion 1]
- [Specific suggestion 2]

### Readability Improvements

- [Specific suggestion 1]
- [Specific suggestion 2]
```

### 5. Implementation Priority

When providing suggestions, prioritize:

1. **High Impact, Low Effort**: Quick wins that significantly improve readability
2. **Functional Programming Patterns**: Converting to functional programming style (applies to both TypeScript and React)
3. **State Predictability** (React): Making state management easier to reason about using functional patterns
4. **Code Reduction**: Removing unnecessary complexity
5. **Maintainability**: Changes that make future modifications easier

## Key Guidelines

- Focus on **simplicity and readability** over cleverness
- Prioritize **functional programming** patterns for both TypeScript and React
- Make **state predictable and easy to understand** for React using functional patterns
- Provide **actionable, specific suggestions** with examples when helpful
- Consider the **full context** of the file, not just isolated sections
- Suggest **incremental improvements** that can be applied step-by-step
- Avoid suggesting changes that would break existing functionality
- When showing code examples, use code references for existing code and markdown code blocks for proposed changes
- Be direct and technical - no fluff or explanations of obvious patterns
- If the code is already simple and well-structured, acknowledge that clearly

