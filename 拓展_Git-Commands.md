Git Commands
============

_A list of my commonly used Git commands_

*If you are interested in my Git aliases, have a look at my `.bash_profile`, found here: https://github.com/joshnh/bash_profile/blob/master/.bash_profile*

--

### Tell Git who you are

| Command                                            | Description                                              |
| -------------------------------------------------- | -------------------------------------------------------- |
| git config --global user.name "Youkou"             | Configure the author name to be used with your commits.  |
| git config --global user.email "3003002865@qq.com" | Configure the author email to be used with your commits. |

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes(but not yet to the remote repository) |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List all the branches in your repo, and also tell you what branch you're currently in |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branchName]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the your active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |
| `git checkout [branch name]` | Switch from one branch to another |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit,Fetch and merge changes on the remote server to your working directory |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository,If you haven't connected your local repository to a remote server, add the server to be able to push to it. |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |
| `git remote -v` | List all currently configured remote repositories. |
| `git push --all origin` | Push all branches to your remote repository |

### Inspection & Comparison&Tags

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git tag 1.0.0 [commitID]` | You can use tagging to mark a significant changeset, such as a release |
| `git push --tags origin` | Push all tags to remote repository |

### View all the merge conflicts

| Command                                  | Description                                                  |
| ---------------------------------------- | ------------------------------------------------------------ |
| `git diff`                               | View all the merge conflicts                                 |
| `git diff --base [filename]`             | View the conflicts against the base file                     |
| `git diff [sourcebranch] [targetbranch]` | Preview changes, before merging                              |
| `git add [filename]`                     | After you have manually resolved any conflicts, you mark the changed file |

### **Undo local changes**

| Command                          | Description                                                  |
| -------------------------------- | ------------------------------------------------------------ |
| `git checkout -- [filename]`     | If you mess up, you can replace the changes in your working tree with the last content in head;Changes already added to the index, as well as new files, will be kept |
| `git fetch origin`               | drop all your local changes and commits                      |
| `git reset --hard origin/master` | fetch the latest history from the server and point your local master branch at it, do this |

### Search

| Command             | Description                               |
| ------------------- | ----------------------------------------- |
| `git grep "main()"` | Search the working directory for `main()` |

