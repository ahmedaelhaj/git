# Git – Version Control System

Git is a distributed version control system used to track changes in source code during software development. This guide covers commonly used Git commands with explanations.

---

## Installation

- **macOS**:  
  `brew install git`
- **Red Hat / Fedora**:  
  `sudo dnf install git`
- **Debian / Ubuntu**:  
  `sudo apt install git`

Verify installation:  
`git --version`

---

## Configuration

Set your identity globally (required for commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

View current configuration:

```bash
git config --list
git config user.name          # show specific value
```

Configuration is stored in `~/.gitconfig` (global) or `.git/config` (per repository).

---

## Creating a New Repository

Start a new repository from scratch:

```bash
# Initialize local repository
git init

# Add all files to staging area
git add .

# Commit changes with a message
git commit -m "first commit"

# Rename default branch to main (optional, but common)
git branch -M main

# Add remote repository URL
git remote add origin https://github.com/username/repo.git

# Push to remote and set upstream tracking
git push -u origin main
```

---

## Working with an Existing Repository

If you already have a local repository and want to connect it to a remote:

```bash
git remote add origin https://github.com/username/repo.git
git branch -M main
git push -u origin main
```

Clone a repository from GitHub (or any remote):

```bash
# Public repository
git clone https://github.com/username/repo.git

# Private repository using a token
git clone https://token@github.com/username/private_repo.git
```

---

## Checking Status and History

- **`git status`** – Show the state of the working directory and staging area.  
- **`git log`** – Display commit history.  
  - `git log --oneline` – Compact one-line per commit.  
  - `git log --oneline --graph --all` – Visualize branch history.

---

## Remote Management

- **`git remote -v`** – List remote repositories with URLs.  
- **`git remote rename <old> <new>`** – Rename a remote.  
- **`git remote remove <name>`** – Remove a remote.  

Fetch and integrate changes:

- **`git fetch origin <branch>`** – Download changes from remote without merging.  
- **`git pull`** – Fetch and merge changes from the upstream branch.  
- **`git push`** – Upload local commits to remote.

---

## Branches

Branches allow parallel development.

- **Create branch**: `git branch <branch-name>`  
- **Switch branch**: `git switch <branch-name>` or `git checkout <branch-name>`  
- **Create and switch**: `git checkout -b <branch-name>`  
- **List branches**:  
  - `git branch` – local branches  
  - `git branch -a` – all (local + remote)  
- **Rename branch**: `git branch -m <old-name> <new-name>`  
- **Delete branch (local)**:  
  - `git branch -d <name>` – safe delete (merged only)  
  - `git branch -D <name>` – force delete  
- **Delete remote branch**: `git push origin --delete <name>`

---

## Merging

Integrate changes from one branch into another. First switch to the target branch (e.g., `main`), then merge:

```bash
git checkout main
git merge <branch-to-merge>
```

If conflicts arise, resolve them manually, then `git add` and `git commit` to complete the merge.

---

## Undoing Changes

### Restore (recommended for unstaged/staged changes)

- **Discard unstaged changes in a file**:  
  `git restore <filename>`  
- **Discard all unstaged changes**:  
  `git restore .`  
- **Unstage a file (keep changes)**:  
  `git restore --staged <filename>`  
- **Restore a file from a previous commit**:  
  `git restore --source HEAD~2 <filename>`  

### Reset (move branch pointer, rewrite history)

- **`git reset --soft HEAD~1`** – Undo last commit but keep changes staged.  
- **`git reset --mixed HEAD~1`** – Undo last commit and unstage changes (default).  
- **`git reset --hard HEAD~1`** – Completely remove last commit and changes (dangerous).  

*Use `reset` with caution, especially on shared branches.*

### Revert (safe undo, creates a new commit)

- **`git revert <commit-hash>`** – Creates a new commit that undoes the changes of a specific commit, preserving history.

---

## Stashing

Temporarily save uncommitted changes without committing.

- **`git stash`** – Stash current modifications.  
- **`git stash list`** – View stashes.  
- **`git stash apply`** – Reapply most recent stash (keep stash).  
- **`git stash pop`** – Reapply and remove stash.  
- **`git stash drop`** – Delete a stash.  
- **`git stash clear`** – Remove all stashes.

---

## Tags

Tags mark specific points in history (e.g., releases).

- **List tags**: `git tag`  
- **Create lightweight tag**: `git tag <tag-name>`  
- **Create annotated tag**: `git tag -a <tag-name> -m "message"`  
- **Push tags to remote**: `git push origin <tag-name>` or `git push --tags`  
- **Delete local tag**: `git tag -d <tag-name>`  
- **Delete remote tag**: `git push origin --delete <tag-name>`

---

## Aliases

Create shortcuts for frequently used commands.

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"
```

Now you can use `git co`, `git br`, etc.

---

## Useful Tips

- Always pull before pushing when working with a shared branch.  
- Use `.gitignore` to exclude files (e.g., build artifacts, secrets).  
- Write clear commit messages: present tense, concise, explain "why".  
- To see what will be pushed: `git diff origin/main..main` (compare local vs remote).  
- To amend the last commit (add forgotten files or fix message):  
  `git commit --amend` – but avoid amending commits already pushed.

---
