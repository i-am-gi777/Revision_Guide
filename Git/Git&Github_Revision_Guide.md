# 1.What is Git?
Git is a version control system used to track changes in files and collaborate with others on code. It helps you:
- Save different versions of your work
- Revert to previous versions if something breaks
- Collaborate with teammates without overwriting each other’s work
# 2.What is a Git Repository?
A Git repository (repo) is a folder that Git is tracking. It can be local (on your computer) or remote (like on GitHub).
# Common Git Terminologies
Repository: A project folder tracked by Git
Commit: A saved version of your changes
Branch: A separate line of development (e.g., main, feature-x)
Merge:	Combining changes from one branch into another
Remote:	A Git repo stored online (e.g., on GitHub)
Clone:	Downloading a remote repo to your local machine
Push:	Sending your commits to the remote repo
Pull:	Downloading others’ changes from the remote repo
Staging area:	Where files are prepared before being committed
🔁 Git Workflow (Step-by-Step)
Here's how you usually work with Git:

```bash
# 1. Initialize Git (if starting a new project)
git init
# 2. Check the status
git status
# 3. Stage changes (add files to be committed)
git add filename.py         # Adds one file
git add .                   # Adds all files
# 4. Commit changes (save a version)
git commit -m "Your message here"
# 5. Connect to GitHub (if not done)
git remote add origin https://github.com/yourusername/repo.git
# 6. Push to GitHub
git push -u origin main
# Cloning an Existing Repo
# If you're joining a project from GitHub:
git clone https://github.com/username/project.git
cd project
# Creating and Using Branches
# Create a new branch:
git checkout -b feature-branch
# Switch between branches:
git checkout main
# Merge a branch:
git checkout main
git merge feature-branch
# Useful Git Commands
# Command	What it does
git log	View commit history
git diff	See what changed
git reset --hard HEAD	Undo all local changes
git pull	Get changes from GitHub
git push	Upload your changes
# Git + GitHub
# Git is the tool on your local computer.
# GitHub is a remote place to store your Git projects (like Dropbox for 
# code).
# You use Git to interact with GitHub.
# Best Practices
# Commit often with meaningful messages
# Use branches to isolate work
# Always pull before you push
# Don’t commit sensitive info (like passwords)
# Use .gitignore to skip unnecessary files (e.g., .pyc, .DS_Store)
# Summary Diagram
# Work → Add → Commit → Push → GitHub
# GitHub → Pull → Update local repo



