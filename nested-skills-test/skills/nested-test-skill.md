---
triggers:
  - nested test
  - test nested
  - inner skill
description: A test skill in a nested directory structure
---

# Nested Test Skill

This is a test skill placed in a nested directory structure to verify the skills loading system handles deep nesting properly.

## Purpose

Verify that skills located in subdirectories (beyond the root `skills/` folder) can be loaded and used by the OpenHands system.

## Example Usage

When this skill is loaded, it should demonstrate:
- Deep directory traversal for skill discovery
- Consistent skill loading behavior across different paths
- Proper trigger detection in nested locations
