---
description: Create pull requests using GitHub CLI with proper templates and formatting
argument-hint: None required - interactive guide for PR creation
---

# How to Create a Pull Request Using GitHub CLI

This guide explains how to create pull requests using GitHub CLI in our project.

**Important**: All PR titles and descriptions should be written in English.

## Prerequisites

Check if `gh` is installed, if not follow this instruction to install it:

1. Install GitHub CLI if you haven't already:

   ```bash
   # macOS
   brew install gh

   # Windows
   winget install --id GitHub.cli

   # Linux
   # Follow instructions at https://github.com/cli/cli/blob/trunk/docs/install_linux.md
   ```

2. Authenticate with GitHub:
   ```bash
   gh auth login
   ```

## Creating a New Pull Request (Interactive Mode)

**Goal:** Create a PR that is clear, descriptive, and ready for review.

1.  **Check for Template:** Look for a PR template in `.github/pull_request_template.md`.
    *   If found: Use it as the base for the PR description.
    *   If missing: **Offer to use the Default Accessible Template** (see below) or create a simple description.

2.  **Gather Information:** Ask the user for the following if not already provided:
    *   **Scope:** What part of the app does this change? (e.g., `auth`, `ui`, `api`)
    *   **Type:** What kind of change is it? (Feature, Fix, Docs, etc.)
    *   **Description:** A brief summary of *what* changed and *why*.
    *   **Breaking Changes:** Are there any breaking changes?

3.  **Construct Command:**
    *   Generate a title using the **Emoji + Conventional Commit** format (e.g., `✨(auth): add login flow`).
    *   Construct the `gh pr create` command. **Always use `--draft` initially** to allow for review.

    ```bash
    gh pr create --draft --title "TYPE(SCOPE): TITLE" --body "DESCRIPTION" --base main
    ```

## Default Accessible Template

If no project-specific template exists, use this structure to ensure quality and accessibility:

```markdown
## 💡 Summary
<!-- What changes are being made? -->

## 🎯 Motivation
<!-- Why are these changes necessary? Link to issue if applicable. -->

## 📸 Screenshots (if appropriate)
<!-- For UI changes, please attach before/after screenshots. -->

## ♿ Accessibility Checklist
- [ ] Semantic HTML used
- [ ] Keyboard navigable
- [ ] Color contrast checked
- [ ] Screen reader friendly (ARIA labels added where needed)
```

## Best Practices

1. **Language**: Always use English for PR titles and descriptions

2. **PR Title Format**: Use conventional commit format with emojis

   - Always include an appropriate emoji at the beginning of the title
   - Use the actual emoji character (not the code representation like `:sparkles:`)
   - Examples:
     - `✨(supabase): Add staging remote configuration`
     - `🐛(auth): Fix login redirect issue`
     - `📝(readme): Update installation instructions`
     - `♿️(a11y): Improve button contrast`

3. **Description Template**: Always use our PR template structure from @.github/pull_request_template.md if it exists.

4. **Draft PRs**: Start as draft when the work is in progress
   - Use `--draft` flag in the command
   - Convert to ready for review when complete using `gh pr ready`

### Success Checklist

1.  **English Only**: All PR content is in English.
2.  **Correct Headers**: Section headers match the template.
3.  **Accessibility**: You've considered the impact on users with disabilities.
4.  **Screenshots**: Visual changes include screenshots for easier review.

### Missing Sections

Always include all template sections, even if some are marked as "N/A" or "None"

## Additional GitHub CLI PR Commands

Here are some additional useful GitHub CLI commands for managing PRs:

```bash
# List your open pull requests
gh pr list --author "@me"

# Check PR status
gh pr status

# View a specific PR
gh pr view <PR-NUMBER>

# Check out a PR branch locally
gh pr checkout <PR-NUMBER>

# Convert a draft PR to ready for review
gh pr ready <PR-NUMBER>

# Add reviewers to a PR
gh pr edit <PR-NUMBER> --add-reviewer username1,username2

# Merge a PR
gh pr merge <PR-NUMBER> --squash
```

## Related Documentation

- [PR Template](.github/pull_request_template.md)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub CLI documentation](https://cli.github.com/manual/)
- [Gitmoji Guide](https://gitmoji.dev/)
