# Skills Test Repository

This repository tests OpenHands org/user-level skill loading from `.agents` repositories.

## Purpose

This repo is used to verify [PR #14440](https://github.com/OpenHands/OpenHands/pull/14440) which adds support for loading org/user skills from `.agents` repositories (with `.openhands` as fallback).

## How to Test

### 1. Set Up the Org/User Skills Repo

Create a `.agents` repository under your GitHub user or org:
- For user-level: `github.com/YOUR_USERNAME/.agents`
- For org-level: `github.com/YOUR_ORG/.agents`

Add skills to `.agents/skills/` in that repo.

### 2. Run OpenHands with PR #14440

```bash
# Checkout the PR
git fetch origin pull/14440/head:pr-14440
git checkout pr-14440

# Run OpenHands
export INSTALL_DOCKER=0
export RUNTIME=local
make build && make run
```

### 3. Select This Repository

In OpenHands, select `HeyItsChloe/skills_test` as your working repository.

### 4. Trigger the Skills

Try these prompts to trigger the test skills:

| Prompt | Expected Skill |
|--------|----------------|
| "Tell me a greeting" | `greeting` skill |
| "Help me debug something" | `debug-helper` skill |
| "What coding standards should I follow?" | `code-standards` skill |

### 5. Verify Loading Order

Check the logs for:
```
Found org skill repo at HeyItsChloe/.agents
```

If `.agents` doesn't exist but `.openhands` does:
```
Using fallback org skill repo HeyItsChloe/.openhands (preferred candidates ['HeyItsChloe/.agents'] not found)
```

## Repository Structure

```
skills_test/
├── README.md                    # This file
├── .agents/
│   └── skills/
│       ├── greeting.md          # Keyword-triggered skill
│       └── debug-helper/        # AgentSkills format
│           └── SKILL.md
└── skills/                      # Alternative location (for testing)
    └── code-standards.md
```

## Skills Included

| Skill | Format | Trigger |
|-------|--------|---------|
| `greeting` | Legacy markdown | Keywords: "greeting", "hello", "hi" |
| `debug-helper` | AgentSkills (SKILL.md) | Keywords: "debug", "debugging", "troubleshoot" |
| `code-standards` | Legacy markdown | Keywords: "standards", "conventions", "style guide" |
