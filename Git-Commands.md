# Git Commands for Beginners

This guide will help you understand and use the most common Git commands for version control.

## Table of Contents
- [Setting Up Git](#setting-up-git)
- [Local Repository Basics](#local-repository-basics)
- [Working with Branches](#working-with-branches)
- [Remote Repository Operations](#remote-repository-operations)
- [Merging and Conflict Resolution](#merging-and-conflict-resolution)
- [Pull Requests](#pull-requests)
- [Advanced Git Commands](#advanced-git-commands)

## Setting Up Git

### Initial Configuration
```bash
# Set your username
git config --global user.name "Your Name"

# Set your email
git config --global user.email "your.email@example.com"

# Check your configuration
git config --list
```

## Local Repository Basics

### Creating and Initializing Repository
```bash
# Initialize a new Git repository
git init

# Check repository status
git status
```

### Basic File Operations
```bash
# Add files to staging area
git add filename.txt        # Add specific file
git add .                  # Add all files

# Remove files
git rm filename.txt        # Remove file from Git and workspace
git rm --cached filename.txt # Remove file from Git only

# Commit changes
git commit -m "Your commit message"
git commit -am "Commit message" # Add and commit tracked files in one command
```

### Viewing History
```bash
# View commit history
git log
git log --oneline         # Compact view
git log --graph          # Graphical view

# View changes
git diff                 # View unstaged changes
git diff --staged        # View staged changes
```

## Working with Branches

### Branch Management
```bash
# List all branches
git branch               # Local branches
git branch -a           # All branches (including remote)

# Create new branch
git branch branch-name

# Switch to a branch
git checkout branch-name
git switch branch-name   # New command (Git 2.23+)

# Create and switch to new branch
git checkout -b new-branch
git switch -c new-branch # New command (Git 2.23+)

# Delete branch
git branch -d branch-name  # Safe delete
git branch -D branch-name  # Force delete
```

## Remote Repository Operations

### Setting Up Remote
```bash
# Add remote repository
git remote add origin https://github.com/username/repo.git

# View remote repositories
git remote -v

# Change remote URL
git remote set-url origin https://github.com/username/repo.git
```

### Syncing with Remote
```bash
# Download changes from remote
git fetch origin

# Download and merge changes
git pull origin branch-name

# Upload local changes
git push origin branch-name

# Set upstream branch
git push -u origin branch-name
```

## Merging and Conflict Resolution

### Merging Branches
```bash
# Merge branch into current branch
git merge branch-name

# Abort merge in case of conflicts
git merge --abort
```

### Handling Conflicts
When conflicts occur:
1. Open the conflicted files
2. Look for conflict markers (<<<<<<, =======, >>>>>>>)
3. Edit files to resolve conflicts
4. Add resolved files: `git add filename`
5. Complete the merge: `git commit`

## Pull Requests
Pull Requests (PRs) are typically managed through platforms like GitHub, GitLab, or Bitbucket.

### Creating a Pull Request
1. Push your branch to remote: `git push origin your-branch`
2. Visit your repository on GitHub/GitLab
3. Click "New Pull Request"
4. Select base branch and compare branch
5. Add title and description
6. Create the pull request

### Best Practices for PRs
- Keep changes focused and small
- Write clear descriptions
- Reference related issues
- Request reviews from team members
- Respond to feedback and make requested changes

## Advanced Git Commands

### Stashing Changes
```bash
# Save changes temporarily
git stash

# List stashes
git stash list

# Apply stashed changes
git stash apply
git stash pop          # Apply and remove stash

# Clear stashes
git stash clear
```

### Reverting Changes
```bash
# Undo last commit (keep changes)
git reset HEAD~1

# Revert a specific commit
git revert commit-hash

# Hard reset to a specific commit (dangerous!)
git reset --hard commit-hash
```

### Tagging
```bash
# Create tag
git tag v1.0.0

# Create annotated tag
git tag -a v1.0.0 -m "Version 1.0.0"

# Push tags to remote
git push origin --tags
```

## Tips and Best Practices

1. **Commit Messages**
   - Write clear, descriptive commit messages
   - Use present tense ("Add feature" not "Added feature")
   - Keep first line under 50 characters
   - Add detailed description if needed

2. **Branch Management**
   - Keep `main/master` branch stable
   - Create feature branches for new work
   - Delete merged branches to avoid clutter

3. **Before Pushing**
   - Review your changes: `git diff`
   - Run tests if available
   - Check for sensitive data

4. **Regular Updates**
   - Regularly pull from main branch
   - Keep local repository up to date
   - Resolve conflicts promptly

## Common Issues and Solutions

1. **Wrong Branch**
   ```bash
   # Save changes
   git stash
   # Switch branch
   git checkout correct-branch
   # Apply changes
   git stash pop
   ```

2. **Committed to Wrong Branch**
   ```bash
   # Copy commit to correct branch
   git cherry-pick commit-hash
   ```

3. **Large Files Committed**
   ```bash
   # Remove large file from history
   git filter-branch --force --tree-filter 'rm -f path/to/large/file' HEAD
   ```

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Interactive Git Learning](https://learngitbranching.js.org)

Remember: Git is powerful but can be complex. Always make sure you understand what a command does before running it, especially commands that modify history or perform force operations.
