Git Learning Documentation
1. Basics Setup
Set Username:
bash
Copy code
git config user.name "[your name]"
Set Email:
bash
Copy code
git config user.email "[your email]"
Initialize Repository:
bash
Copy code
git init
2. Cloning a Repository
Clone the main branch:
bash
Copy code
git clone <repository_url>
Clone a specific branch:
bash
Copy code
git clone --branch <branch_name> <repository_url>
Clone into the current directory:
bash
Copy code
git clone <repository_url> .
Clone into a specific directory:
bash
Copy code
git clone <repository_url> <directory_name>
3. Remote Commands
View remote name(s):
bash
Copy code
git remote
View remote URL(s):
bash
Copy code
git remote -v
Rename a remote:
bash
Copy code
git remote rename <old_name> <new_name>
Add a remote:
bash
Copy code
git remote add <remote_name> <repository_url>
Remove a remote:
bash
Copy code
git remote remove <remote_name>
4. Staging Files
Add all files:
bash
Copy code
git add .
Add specific file/directory:
bash
Copy code
git add <file_name> <directory_name>
Remove a file/directory:
bash
Copy code
git rm <file_name> <directory_name>
5. Committing Changes
Commit with a message:
bash
Copy code
git commit -m "[commit message]"
Track and save all changes with a message:
bash
Copy code
git commit -am "[commit message]"
Edit the previous commit message:
bash
Copy code
git commit --amend -m "[new commit message]"
6. Stash
Scenario:
Use git stash to save uncommitted changes temporarily, even when switching branches.

Stash changes:
bash
Copy code
git stash
Stash including untracked files:
bash
Copy code
git stash -u
Stash all files:
bash
Copy code
git stash --all
Apply and pop stash:
bash
Copy code
git stash pop
Apply stash without popping:
bash
Copy code
git stash apply
Drop stash:
bash
Copy code
git stash drop
7. Branching
List branches:
bash
Copy code
git branch
git branch --list
git branch -a  # Includes remote branches
Create a new branch:
bash
Copy code
git branch <new_branch>
Switch to a branch:
bash
Copy code
git checkout <branch>
Create and switch to a new branch:
bash
Copy code
git checkout -b <new_branch>
Delete a branch safely:
bash
Copy code
git branch -d <branch>
Force delete a branch:
bash
Copy code
git branch -D <branch>
Rename the current branch:
bash
Copy code
git branch -m <new_name>
Push a branch to remote:
bash
Copy code
git push <remote_repo> <branch>
Delete a remote branch:
bash
Copy code
git push <remote_repo> --delete <branch>
Merge a branch into the main branch:
bash
Copy code
git checkout main
git merge <branch>
8. Pulling Changes
Fetch changes without applying:
bash
Copy code
git fetch <remote>
Fetch a specific branch:
bash
Copy code
git fetch <remote> <branch>
Fetch and merge changes:
bash
Copy code
git pull <remote>
9. Logging and Reviewing
View all commits:
bash
Copy code
git log
View commit summaries:
bash
Copy code
git log --oneline
View commits with diff info:
bash
Copy code
git log --stat
View commits after a date:
bash
Copy code
git log --oneline --after="YYYY-MM-DD"
View commits before a date:
bash
Copy code
git log --oneline --before="YYYY-MM-DD"
10. Reverting and Resetting
Undo latest commit but keep changes:
bash
Copy code
git reset HEAD~1
Discard changes in the latest commit:
bash
Copy code
git reset --hard HEAD~1
Revert a specific commit:
bash
Copy code
git revert <commit_id>
11. Comparing Changes
Compare branches:
bash
Copy code
git diff <branch_1> <branch_2>
Compare a specific file between branches:
bash
Copy code
git diff <branch_1> <branch_2> <file>