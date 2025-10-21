# GIT

This repository will contain all of [Git commands](https://git-scm.com/cheat-sheet) as a cheat sheet.

## Working directory, staging area and repository

| Concept           | Meaning                                                               | Example        |
| ----------------- | --------------------------------------------------------------------- | -------------- |
| Working Directory | The place where you edit your files                                   | edit README.md |
| Staging Area      | A middle space where you prepare the files before make a commit       | git add .      |
| Repository        | Commit history which contains versions of your project in each commit | git commit     |

## Cheat Sheet

Note: The dangerous command will be present with that _format_ and the obsolete command with that ~~format~~.

### Initial

- `git init` starts a new repository.
- `git clone` clones a existing repository.

### Configuration

#### Local

Git configuration only affects current repository. Ideal when you want to show other information than the global configuration.

**file path**: <your repository>/.git/config

- `git config --local --list` displys a list of local configurations.
- `git config --local user.name 'joe.doe'` adds a user name.
- `git config --local user.email 'joe.doe@gmail.com'` adds a user email.
- `git config --local core.editor 'code --wait'` adds a default editor path. In that case Visual Studio Code shortcut.

#### Global

Git configuration affects all repositories in the user session. Ideal when you dont want to use the same information in all repositories.

**Linux file path**: /home/user/.gitconfig

**Windows file path**: C:/Users/<your user>/.gitconfig

- `git config --global --list` displays a list of global configurations.
- `git config --global user.name 'joe.doe'` adds a user name.
- `git config --global user.email 'joe.doe@gmail.com'` adds a user email.
- `git config --global core.editor 'code --wait'` adds a default editor path. In that case Visual Studio Code shortcut.

#### System

Git configuration affects all repositories in all user sessions.

**Linux file path**: /etc/gitconfig

**Windows file path**: C:/ProgramData/Git/config

- `git config --system --list` displays a list of global configurations.
- `git config --system user.name 'joe.doe'` adds a user name.
- `git config --system user.email 'joe.doe@gmail.com'` adds a user email.
- `git config --system core.editor 'code --wait'` adds a default editor path. In that case Visual Studio Code shortcut.

### Prepare the staging area

- `git status` displays the staging area status (file outside or inside the staging area).
- `git add README.md` adds a file to staging area.
- `git restore README.md` restores the file to the actual commit if it was modified.
- `git reset README.md` unstages the file.

### Prepare to commit

- `git commit` opens default editor and makes a commit (when close editor).
- `git commit -m 'Write the first commit'` makes a commit with a message in git bash.
- `git commit -am 'Write the second commit'` makes a commit only with tracked files (files that are in the latest commit).
- `git commit --amend` allows you to modify the latest commit.

### Audit to the commit history

#### Log

- `git log` displays the detailed commit history.
- `git log -n 3` displays n details commits.
- `git log --oneline` displays each commit as a single-line view.
- `git log --graph` displays a graphic relation of each commits.
- `git log -n 5 --oneline --graph` displays latest 5 commits as a single-line view with a graphic relation between each one.

#### Diff

##### Working directory

- `git diff README.md` compares the file in working directory with the file in the last commit.
- `git diff <commit> -- README.md` compares the file in working directory with the file in a specific commit.
- `git diff <commit> <commit> -- README.md` compares the file in two specific commits.
- `git diff <commit> <branch> -- README.md` compares the version of the file in the specified commit with the version in the specified branch.

##### Staging area

- `git diff --staged README.md` compares the file in staging area with the file in the latest commit.
- `git diff --staged <commit> -- README.md` compares the file in staging area with the file in a specific commit.
- `git diff --staged <commit> <branch> -- README.md` compares the file in staging area with the file in a specific commit into a current branch with other specific branch.

### Manage commit

- _`git reset --soft HEAD~1`_ reset the history back by n commits, preserving the staged changes. **Be careful to use it in a share repository**.
- _`git reset --hard HEAD~1`_ reset the history back by n commits, without preserving the staged changes. **Be careful to use it in a share repository**.
- `git revert HEAD` safely reverts the latest commit by creating an inverse commit. Useful for shared repositories.

### Stash

Stash command is usually used for cleaning the directory without losing your current changes, saving in a temporary copy.

**File path**: <your repository>/.git/refs/stash

- `git stash list` displays a stash list.
- `git stash push -m 'Temporal data'` saves the file tracked as a temporal copy (doesn't include untracked file).
- `git stash push -u -m 'Temporal data'` saves the file tracked/untracked as a temporal copy (doesn't include ignored files).
- `git stash push -a -m 'Temporal data'` saves all the files as a temporal copy.
- `git stash apply` brings back the latest stash whitout deleting it.
- `git stash apply stash@{0}` brings back a specific stash whitout deleting it.
- `git stash pop` brings back the latest stash deleting it in a process.
- `git stash pop stash@{0}` brings back a specific stash deleting it in a process.

### Manage branch

- `git branch` displays a list of branchs.
- `git branch <branch-name>` creates a branch.
- `git branch -d <branch-name>` Deletes an specify branch
- `git switch <branch-name>` Switches branch.
- `git switch -c <branch-name>` Creates and switches branch.
- `git rebase <main-branch>` Brings all <main-branch> commits into current branch.
- `git merge <develop-branch>` Brings all <develop-branch> new commits and merge to current branch, usually named main/master.

### Squashing

Usually used to join multiple commits into one.

- `git rebase -i HEAD~2` Squashes n commits. Default code editor will open and then you could chose what commit will be the pick and what commits will be the squash.

### Cherry-pick

Cherry-pick command is used to

- `git cherry-pick <commit-hash> <branch-name>` picks a particular commit from a group of commits and applies it to the current branch.

### Configure remote repository

- `git remote add <remote-name> <url-repository>` Links a remote repository with a local repository.
- `git pull <remote-name> <branch-name>` fetches the remote repository commits to local repository.
- `git push <remote-name> <branch-name>` Uploads local repository commits to remote repository.
