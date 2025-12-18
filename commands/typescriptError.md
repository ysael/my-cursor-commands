# Review TypeScript Error and Propose Fix

📝 **Command:** `@typescriptError [filepath]`

**Version:** 1.0.0

AI-powered TypeScript error review and fix proposal using best practices

## Instructions

When invoked with `@typescriptError` (optionally with a file path), automatically (without prompting the user):

### 1. Determine Scope

- If a file path is provided as an argument, focus on TypeScript errors in that file only
- If no file path is provided, check for TypeScript errors across the entire workspace
- Use `read_lints` to get all TypeScript errors (filter for severity: error, ignore warnings unless explicitly requested)

### 2. Analyze Each Error

For each TypeScript error found:

#### 2.1 Read Context

- Read the file containing the error
- Read surrounding code (at least 20-30 lines before and after the error line)
- Understand the type definitions involved (check imports, type definitions, interfaces)
- Check related files if the error involves imported types or functions
- Understand the codebase patterns (functional programming, React patterns, Next.js conventions)

#### 2.2 Understand the Error

- Parse the error message to understand:
  - What type is expected vs what type is provided
  - Missing properties or methods
  - Type incompatibilities
  - Null/undefined handling issues
  - Generic type constraints
  - Module resolution issues
- Identify the root cause, not just the symptom

#### 2.3 Consider Best Practices

When proposing fixes, follow these best practices aligned with the codebase:

**TypeScript Best Practices:**

- Use type inference where possible to reduce verbosity
- Prefer types over interfaces (per codebase conventions)
- Avoid enums; use maps instead
- Use proper null/undefined handling (early returns, guard clauses, optional chaining)
- Use type narrowing with type guards when appropriate
- Prefer discriminated unions for complex type scenarios
- Use `as const` for literal types when needed
- Avoid `any` - use `unknown` and type guards if necessary
- Use proper generic constraints
- Leverage utility types (Partial, Pick, Omit, etc.) when appropriate

**Error Handling:**

- Prioritize error handling: handle errors and edge cases early
- Use early returns and guard clauses
- Model expected errors as return values in Server Actions
- Use proper type narrowing for null/undefined checks

**Functional Programming:**

- Prefer functional patterns over imperative
- Use pure functions where possible
- Avoid mutating data structures

**React/Next.js Specific:**

- Follow React Server Components patterns when applicable
- Use proper typing for props and state
- Handle async operations with proper types
- Use proper typing for hooks and context

### 3. Propose Fix

For each error, provide:

#### 3.1 Error Analysis

- **Error Location**: File path and line number
- **Error Message**: The exact TypeScript error message
- **Root Cause**: Brief explanation of why this error is occurring
- **Context**: Relevant code context that contributes to the error

#### 3.2 Proposed Fix

- **Solution**: Clear explanation of the fix approach
- **Code Change**: Show the specific code change needed using code references for existing code and markdown code blocks for proposed changes
- **Alternative Approaches**: If multiple valid solutions exist, mention them briefly
- **Why This Fix**: Brief explanation of why this approach follows best practices

#### 3.3 Implementation

- Apply the fix directly to the file using the appropriate editing tool
- Ensure the fix doesn't introduce new errors
- Maintain code style and patterns consistent with the codebase
- Preserve existing functionality

### 4. Output Format

Display the analysis and fixes in a clear, structured format:

````markdown
## TypeScript Error Review

### Error 1: [Brief Description]

**Location:** `filepath:line:column`
**Error:** [Exact error message]

**Root Cause:**
[Explanation of why the error occurs]

**Context:**
[Relevant code context]

**Proposed Fix:**

**Solution:** [Approach to fix]

```startLine:endLine:filepath
// existing code with error
```
````

```typescript
// proposed fix
```

**Why This Fix:**
[Brief explanation of best practices followed]

---

### Error 2: [Brief Description]

...

```

### 5. Verification

After proposing fixes:

- Re-check for TypeScript errors using `read_lints` to verify fixes resolved the issues
- If new errors were introduced, analyze and fix those as well
- Ensure no regressions were introduced

## Key Guidelines

- **Automatically detect errors** - don't ask the user to provide error messages
- **Read full context** - understand the codebase patterns before proposing fixes
- **Follow codebase conventions** - match existing code style and patterns
- **Prioritize type safety** - avoid `any`, use proper type narrowing
- **Be direct and technical** - no fluff, focus on the fix
- **Apply fixes automatically** - don't just suggest, implement the changes
- **Verify after fixing** - check that errors are resolved and no new ones introduced
- **Consider edge cases** - ensure fixes handle null/undefined and error cases properly
- **Use code references** for existing code and markdown code blocks for proposed changes
- **Multiple errors**: Fix all errors found, not just the first one
- **Complex errors**: If an error requires understanding multiple files, read all relevant files before proposing a fix

## Special Cases

### Null/Undefined Errors

- Use optional chaining (`?.`) when appropriate
- Use nullish coalescing (`??`) for default values
- Add type guards for proper type narrowing
- Use early returns for null/undefined checks

### Type Mismatch Errors

- Check if types need to be widened or narrowed
- Consider using type assertions only when absolutely necessary (prefer type guards)
- Check if utility types (Partial, Pick, Omit) can help
- Verify imported types are correct

### Generic Type Errors

- Ensure generic constraints are properly defined
- Check if type parameters need to be specified explicitly
- Verify generic type inference is working as expected

### Module Resolution Errors

- Check import paths are correct
- Verify type definitions exist
- Check tsconfig.json settings if needed

