# Pull Request Update Guide

This guide explains how to update code when working with pull requests in the TSMNet repository.

## Understanding Pull Requests

A pull request (PR) is a way to propose changes to the codebase. When you have an open PR, you may need to update it based on:
- Review feedback
- Changes in the base branch
- New requirements
- Bug fixes

## How to Update Code in Your Pull Request

### 1. Make Changes Locally

First, make sure you're on the correct branch:

```bash
# Check which branch you're on
git branch

# Switch to your PR branch if needed
git checkout your-branch-name
```

Edit your files as needed, then stage and commit the changes:

```bash
# Stage your changes
git add .

# Or stage specific files
git add path/to/file.py

# Commit with a descriptive message
git commit -m "Description of changes"
```

### 2. Push Changes to Update the PR

Once you've committed your changes, push them to update the PR:

```bash
# Push to the remote branch
git push origin your-branch-name
```

The pull request will automatically update with your new commits.

### 3. Update from Base Branch

If the base branch has changed and you need to incorporate those changes:

```bash
# Fetch the latest changes
git fetch origin

# Merge changes from the base branch
git merge origin/main

# Or rebase your changes on top of the base branch
git rebase origin/main

# Push the updated branch (may need --force-with-lease if you rebased)
git push origin your-branch-name
```

**Note:** Use `--force-with-lease` instead of `--force` when force-pushing to avoid accidentally overwriting others' work.

### 4. Address Review Comments

When reviewers provide feedback:

1. Make the requested changes in your local branch
2. Commit the changes with clear messages
3. Push to update the PR
4. Reply to review comments to indicate you've addressed them

## Best Practices

1. **Keep commits focused**: Each commit should address a specific change
2. **Write clear commit messages**: Describe what changed and why
3. **Test before pushing**: Ensure your changes work and don't break existing functionality
4. **Keep PRs small**: Smaller PRs are easier to review and merge
5. **Update regularly**: Sync with the base branch frequently to avoid merge conflicts

## Common Scenarios

### Scenario 1: Fixing a Bug in Your PR

```bash
# Make the fix
git add fixed-file.py
git commit -m "Fix bug in calculation logic"
git push origin your-branch-name
```

### Scenario 2: Adding a New Feature to Your PR

```bash
# Add the new feature
git add new-feature.py
git commit -m "Add new feature X"
git push origin your-branch-name
```

### Scenario 3: Resolving Merge Conflicts

```bash
# Fetch and merge the base branch
git fetch origin
git merge origin/main

# If there are conflicts, Git will mark them in the files
# Edit the conflicted files to resolve conflicts
# Then stage and commit the resolution
git add resolved-file.py
git commit -m "Resolve merge conflicts with main"
git push origin your-branch-name
```

## Getting Help

If you encounter issues:
- Check the [GitHub documentation](https://docs.github.com/en/pull-requests)
- Ask for help in the PR comments
- Contact the repository maintainers

## Related Commands

```bash
# View current status
git status

# View commit history
git log --oneline

# View changes in files
git diff

# View remote branches
git branch -r

# Discard local changes
git checkout -- file.py

# Undo last commit (keeping changes)
git reset --soft HEAD~1
```
