---
triggers:
  - debug
  - debugging
  - troubleshoot
  - bug
  - error
  - fix
description: Systematic debugging methodology for identifying and resolving code issues
---

# Debug Helper

A structured approach to debugging code issues.

## Debugging Methodology

When helping debug an issue, follow this systematic approach:

### 1. Understand the Problem
- What is the expected behavior?
- What is the actual behavior?
- When did it start happening?
- What changed recently?

### 2. Reproduce the Issue
- Create a minimal reproduction case
- Identify the exact steps to trigger the bug
- Note any error messages or stack traces

### 3. Isolate the Cause
- Use binary search to narrow down the problem
- Check recent commits with `git bisect` if applicable
- Add logging/print statements strategically
- Use a debugger when appropriate

### 4. Form Hypotheses
List 3-5 possible causes, ranked by likelihood:
1. Most likely cause
2. Second most likely
3. ...

### 5. Test and Fix
- Test each hypothesis systematically
- Make one change at a time
- Verify the fix doesn't introduce regressions

### 6. Document
- Explain what caused the bug
- Explain why the fix works
- Consider if similar bugs might exist elsewhere

## Common Debugging Commands

```bash
# Check recent changes
git log --oneline -10
git diff HEAD~1

# Search for patterns
grep -rn "error_pattern" .

# Run tests
pytest -xvs tests/

# Check logs
tail -f /tmp/app.log
```

## Anti-patterns to Avoid

- Making multiple changes at once
- Not reading error messages carefully
- Assuming instead of verifying
- Ignoring test failures
