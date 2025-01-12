# Git & GitHub

1. Command to Create new repository on command line

```
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/Afzal-8282/Git-GitHub.git
git push -u origin main
```

2. Commands to Push an existing repository through command line

```
git remote add origin https://github.com/Afzal-8282/Git-GitHub.git
git branch -M main
git push -u origin main
```

3. Commands for moving pointer Head to previous commit

    Here, HEAD = refers to the current commit, HEAD~1 = refers to the commit just before the current one, HEAD~2 = would refer to 2 commits behind

```
git checkout HEAD~1 
git checkout <commit-hash>
git switch --detach HEAD~1
```

4. Commands to recover files from previous commits

```
git status
git restore <file-name>(To restore a particular file)
git restore . (To restore all files)
git checkout <commit-hash> -- <file-name>(To restore file from a particular commit)
git show <commit-hash>:<file-name>(To see the files of a particular commit)
```

5. Few more commands

```
# Create a new branch and reset it to the current state of the working directory
git checkout --orphan new-branch

# Add all files to the new branch
git add .

# Commit the current state as the first commit
git commit -m "Initial commit after history reset"

# Delete the old branch (e.g., main or master)
git branch -D main

# Rename the new branch to main
git branch -m main

# Force push to update the remote repository
git push --force --set-upstream origin main

```

6. To delete specific commits from history

    here, -i means interactive

```
git rebase -i HEAD~<number-of-commits>
git rebase -i HEAD~5
git push --force
```

7. For reseting a branch to desire commit

```
git reset --hard <commit-hash>
git clean -fd(Optionally, if the unwanted commits modified the working directory, you can clean up untracked files)
git push --force
```

8. For looking at previous logs

```
git log
git log --oneline
```

9. Methods of rebasing

pick (default):- Keep the commit as-is.
reword:- Edit the commit message without changing its content.
edit:- Pause the rebase process to modify the commit (e.g., change files or amend the commit).
squash:- Combine the commit with the previous one and merge their commit messages.
fixup:- Like squash, but discards the commit message.
drop:- Remove the commit entirely from history.

```
pick abc123 Commit message for the first commit
drop def456 Commit message for the second commit
reword ghi789 Commit message for the third commit
```

After resolving changes or editing commits, you may need to continue the rebase process with

```
git rebase --continue
```

To rewrite the history, including the first commit, you need to rebase the entire history

```
git rebase -i --root
```

10. Add file and commit together by using single command

```
git commit -am "Your commit message"
git add . && git commit -m "Your commit message"
```

11. Diff Command is used for:- Viewing changes in our working directory, staging area, or between commits. It shows the differences line by line, making it a powerful tool for reviewing changes

```
# Unstaged Changes for a Specific File
git diff <file>

# Staged Changes for a Specific File
git diff --staged <file>

# Between Commits for a Specific File
git diff <commit1> <commit2> <file>

# Comparison between two commits
git diff <commit1> <commit2>

# Comparison between commit and Working Directory
git diff <commit>

# View changes from the last 4 commits
git diff HEAD~3 HEAD

```

12. Commands to Merge

```
git checkout <target-branch>
git merge feature-branch
git merge <branch-to-merge> -m "Merge message"(Commit Message During Merge)
git merge --abort(If something goes wrong)
```

13. Commands to fetch:- Use git fetch when you want to inspect new commits or branches in the remote repository
                        without modifying your working directory

```
git fetch(Fetch all changes (commits, branches, tags) from the default remote (origin))
git fetch <remote-name>(If your repository has multiple remotes, specify the remote name)
git fetch <remote-name> <branch-name>(To fetch changes for a specific branch)
git fetch --prune(Remove references to remote branches that have been deleted)
git log origin/<branch-name>(View Changes Without Applying Them, check the changes have been fetched)
git merge origin/main(Merge the fetched changes into your local branch (if needed))
```

14. Commands to Pull
            The git pull command is used to fetch changes from a remote repository and automatically merge them into your current branch. It’s essentially a combination of two Git commands: git fetch (to retrieve the changes from the remote) and git merge (to apply those changes to your current branch)

```
git pull <remote-name> <branch-name>
git pull origin main
git pull --rebase(avoids a merge commit)
```

15. Git stashing:- Tempory pause in working branch so that can switch to other branch when needed.

```
git stash
git stash pop
```

16. Command to use multiple remote repositories simultaneously

```
git remote add <remote-name> <url>(commonly we give origin name for remote repository but it could be anything.)
```