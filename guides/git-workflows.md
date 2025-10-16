# Git Workflows Guide

This guide covers common Git workflows used in software development teams.

## Table of Contents

- [Basic Workflow](#basic-workflow)
- [Feature Branch Workflow](#feature-branch-workflow)
- [Gitflow Workflow](#gitflow-workflow)
- [GitHub Flow](#github-flow)
- [Trunk-Based Development](#trunk-based-development)
- [Forking Workflow](#forking-workflow)

## Basic Workflow

The simplest workflow for individual developers or small teams.

### Process

1. Make changes in working directory
2. Stage changes
3. Commit changes
4. Push to remote

### Commands

```bash
# Make changes to files
git status

# Stage changes
git add .

# Commit changes
git commit -m "Descriptive message"

# Push to remote
git push origin main
```

### When to Use

- Personal projects
- Small teams
- Simple projects
- Learning Git

## Feature Branch Workflow

Each new feature is developed in a dedicated branch.

### Process

1. Create a feature branch from main
2. Make changes and commit
3. Push feature branch to remote
4. Create pull request
5. Review and merge to main
6. Delete feature branch

### Commands

```bash
# Update main branch
git checkout main
git pull origin main

# Create feature branch
git checkout -b feature/user-authentication

# Make changes and commit
git add .
git commit -m "Add login functionality"

# Push feature branch
git push -u origin feature/user-authentication

# After PR is merged, delete local branch
git checkout main
git pull origin main
git branch -d feature/user-authentication
```

### Branch Naming Conventions

- `feature/` - New features
- `bugfix/` - Bug fixes
- `hotfix/` - Urgent fixes
- `refactor/` - Code improvements
- `docs/` - Documentation updates

Examples:
- `feature/user-authentication`
- `bugfix/login-error`
- `hotfix/security-patch`

### When to Use

- Small to medium teams
- Projects with regular releases
- When code review is important

## Gitflow Workflow

A strict branching model with dedicated branches for different purposes.

### Main Branches

- **main/master** - Production-ready code
- **develop** - Integration branch for features

### Supporting Branches

- **feature/** - New features (from develop, merge to develop)
- **release/** - Release preparation (from develop, merge to main and develop)
- **hotfix/** - Emergency fixes (from main, merge to main and develop)

### Process

#### Starting a Feature

```bash
# Update develop
git checkout develop
git pull origin develop

# Create feature branch
git checkout -b feature/new-feature

# Work on feature
git add .
git commit -m "Add new feature"

# Push to remote
git push -u origin feature/new-feature
```

#### Finishing a Feature

```bash
# Update develop
git checkout develop
git pull origin develop

# Merge feature
git merge --no-ff feature/new-feature

# Push to remote
git push origin develop

# Delete feature branch
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

#### Creating a Release

```bash
# Create release branch from develop
git checkout develop
git pull origin develop
git checkout -b release/1.0.0

# Bump version, update changelog
git add .
git commit -m "Bump version to 1.0.0"

# Test and fix bugs in release branch
```

#### Finishing a Release

```bash
# Merge to main
git checkout main
git pull origin main
git merge --no-ff release/1.0.0
git tag -a v1.0.0 -m "Version 1.0.0"
git push origin main --tags

# Merge back to develop
git checkout develop
git merge --no-ff release/1.0.0
git push origin develop

# Delete release branch
git branch -d release/1.0.0
git push origin --delete release/1.0.0
```

#### Creating a Hotfix

```bash
# Create hotfix branch from main
git checkout main
git pull origin main
git checkout -b hotfix/1.0.1

# Fix the issue
git add .
git commit -m "Fix critical bug"
```

#### Finishing a Hotfix

```bash
# Merge to main
git checkout main
git merge --no-ff hotfix/1.0.1
git tag -a v1.0.1 -m "Version 1.0.1"
git push origin main --tags

# Merge to develop
git checkout develop
git merge --no-ff hotfix/1.0.1
git push origin develop

# Delete hotfix branch
git branch -d hotfix/1.0.1
git push origin --delete hotfix/1.0.1
```

### When to Use

- Large teams
- Scheduled release cycles
- Multiple versions in production
- Complex projects

## GitHub Flow

A simpler alternative to Gitflow, centered around pull requests.

### Process

1. Create a branch from main
2. Make changes and commit
3. Push branch and open pull request
4. Discuss and review
5. Deploy for testing (optional)
6. Merge to main
7. Deploy to production

### Commands

```bash
# Update main
git checkout main
git pull origin main

# Create branch
git checkout -b feature-name

# Make changes
git add .
git commit -m "Add feature"

# Push and create PR
git push -u origin feature-name
```

### Pull Request Best Practices

- Small, focused changes
- Clear description
- Reference related issues
- Request specific reviewers
- Respond to feedback promptly
- Keep branch up to date

### When to Use

- Continuous deployment
- Small to medium teams
- Web applications
- When simplicity is important

## Trunk-Based Development

Developers collaborate on code in a single branch (trunk/main) with short-lived feature branches.

### Characteristics

- Very short-lived branches (< 1 day)
- Frequent commits to main
- Feature flags for incomplete features
- Strong CI/CD pipeline
- High test coverage

### Process

```bash
# Update main
git checkout main
git pull origin main

# Create short-lived branch
git checkout -b short-feature

# Make small changes
git add .
git commit -m "Small change"

# Push and create PR immediately
git push -u origin short-feature

# Quick review and merge (< 1 hour)
```

### Feature Flags Example

```javascript
if (featureFlags.newFeature) {
  // New code
} else {
  // Old code
}
```

### When to Use

- Experienced teams
- Strong CI/CD culture
- High test coverage
- Continuous deployment
- Fast-paced development

## Forking Workflow

Used in open-source projects where contributors don't have write access.

### Process

1. Fork repository to your account
2. Clone your fork locally
3. Create feature branch
4. Make changes and commit
5. Push to your fork
6. Create pull request to original repository

### Commands

```bash
# Fork on GitHub UI

# Clone your fork
git clone https://github.com/your-username/repository.git
cd repository

# Add upstream remote
git remote add upstream https://github.com/original-owner/repository.git

# Create branch
git checkout -b feature-name

# Make changes
git add .
git commit -m "Add feature"

# Push to your fork
git push origin feature-name

# Create PR on GitHub

# Keep fork updated
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

### Syncing Your Fork

```bash
# Fetch upstream changes
git fetch upstream

# Checkout your main branch
git checkout main

# Merge upstream/main
git merge upstream/main

# Push to your fork
git push origin main
```

### When to Use

- Open-source projects
- External contributors
- No write access to main repository
- Large number of contributors

## Choosing a Workflow

Consider these factors:

### Team Size
- **Small (1-5)**: Basic or Feature Branch
- **Medium (5-20)**: Feature Branch or GitHub Flow
- **Large (20+)**: Gitflow or Trunk-Based

### Release Frequency
- **Continuous**: GitHub Flow or Trunk-Based
- **Regular sprints**: Feature Branch
- **Scheduled releases**: Gitflow

### Team Experience
- **Beginners**: Basic or Feature Branch
- **Intermediate**: GitHub Flow
- **Advanced**: Trunk-Based or Gitflow

### Project Complexity
- **Simple**: Basic or Feature Branch
- **Medium**: GitHub Flow
- **Complex**: Gitflow

## Best Practices for All Workflows

1. **Commit Often** - Small, logical commits
2. **Write Good Messages** - Clear and descriptive
3. **Pull Before Push** - Stay up to date
4. **Use Branches** - Isolate changes
5. **Review Code** - Maintain quality
6. **Test Before Merge** - Prevent bugs
7. **Delete Old Branches** - Keep repository clean
8. **Document Decisions** - In commits and PRs
9. **Automate Testing** - CI/CD pipelines
10. **Communicate** - With team members

## Common Commands Reference

```bash
# View branches
git branch -a

# Switch branch
git checkout branch-name
git switch branch-name

# Create and switch
git checkout -b new-branch
git switch -c new-branch

# Update from remote
git fetch
git pull

# Push changes
git push origin branch-name

# Merge branch
git merge branch-name

# Rebase branch
git rebase main

# Delete branch
git branch -d branch-name
git push origin --delete branch-name

# View history
git log --oneline --graph --all

# Stash changes
git stash
git stash pop
```

## Resources

- [Git Documentation](https://git-scm.com/doc)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [GitHub Guides](https://guides.github.com/)
- [Pro Git Book](https://git-scm.com/book/en/v2)
