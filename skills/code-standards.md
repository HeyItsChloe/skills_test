---
triggers:
  - standards
  - conventions
  - style guide
  - coding style
  - best practices
description: Coding standards and conventions for this project
---

# Code Standards

Follow these coding standards when working on this project.

## General Principles

1. **Clarity over cleverness** - Write code that's easy to understand
2. **Consistency** - Follow existing patterns in the codebase
3. **Simplicity** - Prefer simple solutions over complex ones

## Python Standards

### Formatting
- Use `ruff` for linting and formatting
- Maximum line length: 88 characters
- Use type hints for function signatures

### Naming
- `snake_case` for functions and variables
- `PascalCase` for classes
- `SCREAMING_SNAKE_CASE` for constants

### Imports
- Group imports: stdlib, third-party, local
- Sort alphabetically within groups
- Use absolute imports

### Example

```python
from typing import Optional

import httpx
from pydantic import BaseModel

from myproject.utils import helper_function


class UserConfig(BaseModel):
    """Configuration for a user."""
    
    name: str
    email: Optional[str] = None
    
    def validate_email(self) -> bool:
        """Check if the email is valid."""
        if not self.email:
            return False
        return "@" in self.email
```

## Testing Standards

- Write tests for new functionality
- Use descriptive test names: `test_<function>_<scenario>_<expected>`
- Prefer real implementations over mocks
- Aim for 80%+ coverage on new code

## Documentation

- Add docstrings to public functions and classes
- Keep comments minimal - code should be self-explanatory
- Update README when adding features
