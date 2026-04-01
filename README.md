# Git --  VERSION CONTROL SYSTEM

# MacOS brew install git # RedHat dnf install git 
# git --version

# Configure Git
# List Configuration
git config user.name
git config user.name
# Set Configuration
git config --global user.name "ahmedaelhaj"
git config --global user.email "ahmed.abdalla.elhaj@gmail.com"
# create a new repository on the command line (new repo)
# initiate local repo
git init
# add to staging area
git add .
# commit to local repo
git commit -m "first commit"
# rename branch from master to main
git branch -M main
# add remote repo
git remote add origin https://github.com/ahmedaelhaj/git.git
# push to remote
git push -u origin main

# push an existing repository from the command line (exsisting repo)
# Add Remote repo
git remote add origin https://github.com/ahmedaelhaj/git.git
# rename master to main branch
git branch -M main
# push to remote repo
git push -u origin main

# Repo Status
git status 
# Repo Log
git log
# Git Remote Branch
git remote -v
# Rename remote branch
git remote rename <old-name(origin)> <new-name>
# Remove remote branch
git remote remove <branch-name>
# Clone Public Repo 
git clone https://github.com/ahmedaelhaj/app.git
# Clone Private Repo (using tocken)
git clone https://token@github.com/ahmedaelhaj/private_repo.git
# Fetch repo (fetch the changes without merging)
git fetch origin <branch>
# Pull Repo (pull the change with merge)
git pull

# Branch
# New
git branch <name>
# Switch
git switch <name> / git checkout <name>
# create and switch branch
git checkout -b <name>
# List
git branch
git branch -a 
# Rename
git branch -m <old-name> <new-name>
# Merge (you switch to the main branch first)
git merge <branch-to-bring-in>
# Delete
git branch -d <name>
git branch -D <name>
# Delete Remote
git push origin --delete <name>
# History
git log --oneline --graph --all

# Checkout
