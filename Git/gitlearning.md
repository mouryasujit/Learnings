# Git Learning Notes

## Table of Contents
1. [Basic Setup](#basic-setup)
2. [Cloning a Repository](#cloning-a-repository)
3. [Using Remote](#using-remote)
4. [Adding Files](#adding-files)
5. [Committing Changes](#committing-changes)
6. [Stashing Changes](#stashing-changes)
7. [Working with Branches](#working-with-branches)
8. [Pulling Changes](#pulling-changes)
9. [Logging and Reviewing Work](#logging-and-reviewing-work)
10. [Reversing Changes](#reversing-changes)

---

# 1. Basic Setup
```bash
# Set username
git config user.name [your name]

# Set email
git config user.email [your email]

# Initialize a repository
git init
# Clone the main branch
git clone repository_url

# Clone a specific branch
git clone --branch branch_name repository_url

# Clone into the current directory
git clone repository_url .

# Clone into a specific directory
git clone repository_url directory_name
** 3. Using Remote**
# View remote name
git remote

# View remote URLs
git remote -v

# Rename remote
git remote rename old_name new_name

# Add a new remote
git remote add origin repo_url

# Remove a remote
git remote rm remote_name


**Add all files**
git add .

# Add specific file or directory
git add file_name
git add dir_name

# Remove a file or directory
git rm file_name
git rm dir_name

**Commit with a message**
git commit -m "commit message"

# Track and save all files with a message
git commit -am "commit message"

# Edit the previous commit message
git commit --amend -m "new commit message"

** 6. Stashing Changes **
- Scenario
- You are working on a branch and need to switch to fix a bug in another branch
- Your current changes are not lost because you use stash

git stash

# Stash staged, unstaged, and untracked files
git stash -u

# Stash everything
git stash --all

# Apply and remove the stash
git stash pop

# Apply without removing from stash
git stash apply

# Drop a specific stash
git stash drop

** 7. Working with Branches ** 
# List all local branches
git branch

# List all local and remote branches
git branch -a

** Creating and Deleting Branches**
#Create a new branch
git branch new_branch

# Switch to a branch
git checkout branch_name

# Create and switch to a new branch
git checkout -b new_branch

# Delete a branch (safe delete)
git branch -d branch_name

# Force delete a branch
git branch -D branch_name


# Rename current branch
git branch -m new_name

# Push a branch to remote
git push remote_repo branch_name

# Delete a remote branch
git push remote_repo --delete branch_name


# Merge another branch into main
git checkout main
git merge other_branch

# Compare differences between two branches
git diff branch_1 branch_2

# Compare a specific file between two branches
git diff branch_1 branch_2 file_name

**8. Pulling Changes**
## Fetch all commits and branches
git fetch remote

## Fetch a specific branch
git fetch remote branch_name

## Merge fetched changes
git merge remote/branch_name

## Fetch and merge simultaneously
git pull remote

**9. Logging and Reviewing Work**
# View all commits
git log

## View commits in a single line
git log --oneline

## View commits with statistics
git log --stat

## View commits after a certain date
git log --oneline --after="YYYY-MM-DD"

## View commits before a certain date
git log --oneline --before="YYYY-MM-DD"

# 10. Reversing Changes
## Undo the latest commit but keep changes
git reset HEAD~1

## Discard all changes from the latest commit
git reset --hard HEAD~1

# Reverting Commits
## Revert a specific commit
git revert commit_id



# Notes
- Always use git stash to safeguard uncommitted work before switching branches.
- Use git log and git diff to review changes before merging or reverting.


---

4. **Save the file**:
   - If you're using VS Code or similar, click **File** > **Save As** and save it as `gitLearning.md`.
   - If you're using a simple text editor, make sure to save it with the `.md` extension.

5. **Upload to GitHub**:
   - Navigate to your GitHub repository.
   - If the `Git` folder doesn't exist, create it.
   - Upload the `gitLearning.md` file into the `Git` folder, or if you’re using the Git command line, commit and push it.



