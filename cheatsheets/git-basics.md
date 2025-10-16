# Git Basics Cheat Sheet

## Configuration

```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# View configuration
git config --list
git config user.name

# Set default branch name
git config --global init.defaultBranch main
```

## Creating Repositories

```bash
# Initialize a new repository
git init

# Clone an existing repository
git clone <repository-url>
git clone <repository-url> <directory-name>
```

## Basic Workflow

```bash
# Check status of files
git status

# Add files to staging area
git add <file>
git add .                    # Add all changes
git add *.js                 # Add all JS files

# Commit changes
git commit -m "Commit message"
git commit -am "Message"     # Add and commit tracked files

# View commit history
git log
git log --oneline
git log --graph --oneline --all
```

## Branching and Merging

```bash
# List branches
git branch
git branch -a                # Show all branches (local and remote)

# Create a new branch
git branch <branch-name>

# Switch to a branch
git checkout <branch-name>
git switch <branch-name>     # Newer syntax

# Create and switch to a new branch
git checkout -b <branch-name>
git switch -c <branch-name>  # Newer syntax

# Merge a branch
git merge <branch-name>

# Delete a branch
git branch -d <branch-name>
git branch -D <branch-name>  # Force delete
```

## Remote Repositories

```bash
# View remote repositories
git remote -v

# Add a remote repository
git remote add origin <repository-url>

# Fetch changes from remote
git fetch
git fetch origin

# Pull changes from remote
git pull
git pull origin <branch-name>

# Push changes to remote
git push
git push origin <branch-name>
git push -u origin <branch-name>  # Set upstream

# Remove a remote
git remote remove <remote-name>
```

## Undoing Changes

```bash
# Discard changes in working directory
git checkout -- <file>
git restore <file>           # Newer syntax

# Unstage a file
git reset HEAD <file>
git restore --staged <file>  # Newer syntax

# Amend the last commit
git commit --amend

# Reset to a previous commit
git reset --soft HEAD~1      # Keep changes staged
git reset --mixed HEAD~1     # Keep changes unstaged
git reset --hard HEAD~1      # Discard all changes

# Revert a commit (creates new commit)
git revert <commit-hash>
```

## Viewing Changes

```bash
# View unstaged changes
git diff

# View staged changes
git diff --staged
git diff --cached

# View changes between commits
git diff <commit1> <commit2>

# View changes in a specific file
git diff <file>
```

## Stashing

```bash
# Save changes temporarily
git stash
git stash save "Message"

# List stashes
git stash list

# Apply stashed changes
git stash apply
git stash apply stash@{n}

# Apply and remove stash
git stash pop

# Remove a stash
git stash drop stash@{n}

# Clear all stashes
git stash clear
```

## Tagging

```bash
# Create a lightweight tag
git tag <tag-name>

# Create an annotated tag
git tag -a <tag-name> -m "Tag message"

# List tags
git tag

# Push tags to remote
git push origin <tag-name>
git push origin --tags

# Delete a tag
git tag -d <tag-name>
git push origin :refs/tags/<tag-name>  # Delete remote tag
```

## Useful Commands

```bash
# Show information about a commit
git show <commit-hash>

# View file at specific commit
git show <commit-hash>:<file>

# Find commits that modified a file
git log -- <file>

# Search commit messages
git log --grep="search term"

# View who changed each line of a file
git blame <file>

# Clean untracked files
git clean -n                 # Dry run
git clean -f                 # Remove files
git clean -fd                # Remove files and directories
```

## Tips

- Write clear, descriptive commit messages
- Commit often with logical chunks of work
- Always pull before pushing
- Use branches for new features or fixes
- Review changes before committing with `git diff`
- Use `.gitignore` to exclude files from version control
