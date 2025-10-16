# GitHub Essentials Cheat Sheet

## Repository Basics

### Creating a Repository
- Click "New" button on GitHub homepage
- Choose repository name and visibility (public/private)
- Optionally add README, .gitignore, and license
- Click "Create repository"

### Cloning a Repository
```bash
# HTTPS
git clone https://github.com/username/repository.git

# SSH
git clone git@github.com:username/repository.git

# GitHub CLI
gh repo clone username/repository
```

## Branches

### Working with Branches
```bash
# Create branch on GitHub via web interface
# Or create locally and push
git checkout -b feature-branch
git push -u origin feature-branch

# View branches
git branch -a

# Switch branches
git checkout main
git switch main

# Delete remote branch
git push origin --delete branch-name
```

### Branch Protection Rules
- Go to Settings > Branches
- Add rule for branch name pattern
- Configure protections:
  - Require pull request reviews
  - Require status checks
  - Require conversation resolution
  - Restrict who can push

## Pull Requests

### Creating a Pull Request
1. Push your branch to GitHub
2. Navigate to the repository
3. Click "Pull requests" > "New pull request"
4. Select base and compare branches
5. Add title and description
6. Assign reviewers, labels, projects
7. Click "Create pull request"

### Pull Request Best Practices
- Write clear, descriptive titles
- Provide context in the description
- Reference related issues with `#issue-number`
- Request reviews from appropriate team members
- Keep PRs focused and reasonably sized
- Respond to review comments promptly

### Merging Strategies
- **Merge commit**: Preserves all commits and creates merge commit
- **Squash and merge**: Combines all commits into one
- **Rebase and merge**: Adds commits individually without merge commit

## Issues

### Creating Issues
1. Go to "Issues" tab
2. Click "New issue"
3. Add title and description
4. Add labels, assignees, projects, milestones
5. Click "Submit new issue"

### Issue Best Practices
- Use clear, descriptive titles
- Provide steps to reproduce for bugs
- Include expected vs actual behavior
- Add relevant labels
- Use task lists for tracking work
- Link related issues and PRs

### Issue Templates
- Create `.github/ISSUE_TEMPLATE/` directory
- Add markdown templates for different issue types
- Configure via Settings > Features > Issues

## Actions (CI/CD)

### Basic Workflow
```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    - name: Run tests
      run: npm test
```

### Workflow Triggers
- `push`: On push to branches
- `pull_request`: On PR events
- `schedule`: Cron-based scheduling
- `workflow_dispatch`: Manual trigger
- `issues`: Issue events
- `release`: Release events

## Collaboration Features

### Code Review
- Add comments on specific lines
- Request changes or approve
- Use "Start a review" for batch comments
- Mark conversations as resolved

### Discussions
- Enable in Settings > Features
- Create categories for different topics
- Use for Q&A, announcements, and ideas
- Convert issues to discussions

### Projects
- Create project boards for organization
- Use Views (table, board, roadmap)
- Add automation with workflows
- Link issues and PRs

### Wiki
- Enable in repository settings
- Create and edit pages
- Use for documentation
- Clone wiki as Git repository

## GitHub CLI

```bash
# Installation
# See: https://cli.github.com/

# Authentication
gh auth login

# Repository operations
gh repo create
gh repo clone
gh repo view

# Issue operations
gh issue create
gh issue list
gh issue view <number>
gh issue close <number>

# Pull request operations
gh pr create
gh pr list
gh pr view <number>
gh pr checkout <number>
gh pr merge <number>

# Workflow operations
gh workflow list
gh workflow run <workflow-name>
gh run list
gh run view <run-id>
```

## Security Features

### Security Advisories
- Report vulnerabilities privately
- Collaborate on fixes
- Publish advisories

### Dependabot
- Automated dependency updates
- Security vulnerability alerts
- Configure in `.github/dependabot.yml`

### Code Scanning
- Automated security testing
- CodeQL analysis
- Third-party integrations

### Secret Scanning
- Detects committed secrets
- Alerts repository admins
- Partner pattern detection

## GitHub Pages

### Enabling GitHub Pages
1. Go to Settings > Pages
2. Select source branch
3. Choose folder (root or /docs)
4. Save

### Custom Domains
- Add CNAME file with domain name
- Configure DNS settings
- Enable HTTPS

## Keyboard Shortcuts

### Global
- `?` - Show keyboard shortcuts
- `s` or `/` - Focus search bar
- `g n` - Go to notifications
- `g i` - Go to issues
- `g p` - Go to pull requests

### Repository
- `t` - Open file finder
- `b` - Open blame view
- `.` - Open in github.dev (web-based editor)
- `l` - Jump to line

### Issues/Pull Requests
- `c` - Create issue
- `e` - Edit issue/PR
- `r` - Reply to issue/PR

## Best Practices

1. **Keep README updated** - Clear description, installation, usage
2. **Use .gitignore** - Exclude unnecessary files
3. **Add LICENSE** - Specify how others can use your code
4. **Write good commit messages** - Clear, concise, descriptive
5. **Use branches** - Isolate features and fixes
6. **Review before merging** - Ensure code quality
7. **Document your code** - Comments, docs, wikis
8. **Use labels** - Organize issues and PRs
9. **Set up CI/CD** - Automate testing and deployment
10. **Secure your repository** - Use security features, protect branches

## Resources

- [GitHub Docs](https://docs.github.com/)
- [GitHub Skills](https://skills.github.com/)
- [GitHub Community](https://github.com/community)
- [GitHub Blog](https://github.blog/)
