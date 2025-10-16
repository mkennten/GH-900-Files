# Getting Started with Git and GitHub

A beginner-friendly guide to get you started with Git and GitHub from scratch.

## What You'll Learn

- What Git and GitHub are
- How to install Git
- How to create your first repository
- How to make your first commit
- How to push to GitHub

## What is Git?

**Git** is a version control system that tracks changes to your files over time. It allows you to:
- Save snapshots of your work (commits)
- Go back to previous versions
- Work on different features simultaneously (branches)
- Collaborate with others

## What is GitHub?

**GitHub** is a web-based platform that hosts Git repositories online. It adds:
- A place to store your code in the cloud
- Collaboration tools (pull requests, issues)
- Project management features
- A portfolio for your work

## Step 1: Install Git

### Windows

1. Download Git from [git-scm.com](https://git-scm.com/download/win)
2. Run the installer
3. Use the default settings (recommended)
4. Open "Git Bash" from the Start menu

### macOS

Option 1: Using Homebrew (recommended)
```bash
brew install git
```

Option 2: Using Xcode Command Line Tools
```bash
xcode-select --install
```

### Linux

#### Ubuntu/Debian
```bash
sudo apt-get update
sudo apt-get install git
```

#### Fedora
```bash
sudo dnf install git
```

### Verify Installation

Open your terminal and run:
```bash
git --version
```

You should see something like: `git version 2.x.x`

## Step 2: Configure Git

Set your name and email (this will appear on your commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Verify your configuration:
```bash
git config --list
```

## Step 3: Create a GitHub Account

1. Go to [github.com](https://github.com)
2. Click "Sign up"
3. Follow the registration steps
4. Verify your email address

## Step 4: Create Your First Local Repository

1. Create a new folder for your project:
```bash
mkdir my-first-project
cd my-first-project
```

2. Initialize Git:
```bash
git init
```

You should see: `Initialized empty Git repository`

3. Create a file:
```bash
echo "# My First Project" > README.md
```

4. Check the status:
```bash
git status
```

You'll see `README.md` listed as an untracked file.

5. Add the file to staging:
```bash
git add README.md
```

6. Create your first commit:
```bash
git commit -m "Initial commit"
```

Congratulations! You've made your first commit! 🎉

## Step 5: Push to GitHub

1. Go to GitHub and click the "+" icon → "New repository"
2. Name it `my-first-project`
3. Leave it public (or choose private)
4. Don't initialize with README (we already have one)
5. Click "Create repository"

6. Connect your local repository to GitHub:
```bash
git remote add origin https://github.com/YOUR-USERNAME/my-first-project.git
git branch -M main
git push -u origin main
```

Replace `YOUR-USERNAME` with your actual GitHub username.

7. Refresh the GitHub page - your code is now online! 🎊

## Step 6: Make More Changes

Let's add more content and push again:

1. Edit your README:
```bash
echo "This is my first Git project!" >> README.md
```

2. Check what changed:
```bash
git status
git diff
```

3. Stage and commit:
```bash
git add README.md
git commit -m "Add project description"
```

4. Push to GitHub:
```bash
git push
```

5. Check GitHub - your new changes are there!

## Common Commands Summary

```bash
# Check status
git status

# Add files to staging
git add <file>
git add .              # Add all files

# Commit changes
git commit -m "Message"

# Push to GitHub
git push

# Pull from GitHub
git pull

# View history
git log
git log --oneline

# Create a branch
git branch feature-name

# Switch branches
git checkout feature-name
git switch feature-name  # Newer syntax

# Create and switch
git checkout -b feature-name
git switch -c feature-name
```

## Understanding the Basic Workflow

```
Working Directory → Staging Area → Local Repository → Remote Repository
                ↓               ↓                  ↓
              git add        git commit         git push
```

1. **Working Directory**: Where you edit files
2. **Staging Area**: Files ready to be committed
3. **Local Repository**: Committed changes on your computer
4. **Remote Repository**: Your code on GitHub

## Best Practices for Beginners

1. **Commit often** - Make small, frequent commits
2. **Write clear messages** - Describe what you changed and why
3. **Pull before push** - Always get latest changes first
4. **Use branches** - Don't work directly on main
5. **Check before commit** - Use `git status` and `git diff`

## Example Workflow

```bash
# Start working on a new feature
git checkout -b add-login-page

# Make changes to files
# Edit login.html

# Check what changed
git status
git diff

# Stage changes
git add login.html

# Commit
git commit -m "Add login page with email and password fields"

# Push to GitHub
git push -u origin add-login-page

# On GitHub: Create pull request to merge into main
```

## Troubleshooting

### "Permission denied" when pushing

You might need to set up SSH keys or use a personal access token.

**Quick fix**: Use HTTPS with a personal access token:
1. Go to GitHub → Settings → Developer settings → Personal access tokens
2. Generate new token (classic)
3. Use the token as your password when pushing

### "Merge conflict"

Don't panic! This happens when two people change the same lines.

```bash
# Pull the latest changes
git pull

# Open the file with conflicts
# Look for <<<<<<< and >>>>>>>
# Edit to keep what you want

# Stage the resolved file
git add <file>

# Commit
git commit -m "Resolve merge conflict"

# Push
git push
```

### Want to undo changes?

```bash
# Undo changes in working directory
git checkout -- <file>

# Unstage a file
git reset HEAD <file>

# Undo last commit (keep changes)
git reset --soft HEAD~1
```

## Next Steps

Now that you understand the basics:

1. **Practice** - Create more repositories and commits
2. **Explore branches** - Learn to work on multiple features
3. **Collaborate** - Contribute to open source projects
4. **Learn GitHub features** - Issues, pull requests, actions
5. **Read documentation** - Check out [Git documentation](https://git-scm.com/doc)

## Useful Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Skills](https://skills.github.com/)
- [Git Cheat Sheet](cheatsheets/git-basics.md)
- [GitHub Essentials](cheatsheets/github-essentials.md)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)

## Getting Help

- **In your terminal**: `git help <command>` or `git <command> --help`
- **GitHub Docs**: [docs.github.com](https://docs.github.com/)
- **Stack Overflow**: Tag your question with `git` and `github`
- **GitHub Community**: [github.com/community](https://github.com/community)

## Remember

- It's okay to make mistakes - that's what version control is for!
- Everyone was a beginner once
- The Git community is helpful and welcoming
- Practice makes perfect

**You've got this!** 🚀

---

Ready to dive deeper? Check out our other guides:
- [Git Workflows](git-workflows.md)
- [Markdown Guide](markdown-guide.md)
- [Contributing Guidelines](contributing.md)
