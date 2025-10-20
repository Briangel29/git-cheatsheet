# GIT

This repository will containt all of [Git commands](https://git-scm.com/cheat-sheet) as a cheat sheet.

## Diference between working directory, staging area and repository

| Concept           | Meaning                                                                | Example            |
| ----------------- | ---------------------------------------------------------------------- | ------------------ |
| Working Directory | The place where you edit your files                                    | You edit README.md |
| Staging Area      | A middle space where you prepare the files before make a commit        | git add .          |
| Repository        | Commit history which containts version of your proyect in each commits | git commit         |

## Cheat Sheet

The dangerous command will be present with that _format_ and the obsolet command with that ~~format~~

### Initial

- `git init` starts a new repository.
- `git clone` clones a existing repository.

### Configuration

#### Local

Git configuration only affects actual repository. Ideal when you want to show other information than the global configuration.

**file path**: <your repository>/.git/config

- `git config --local --list` shows a list of local configurations.
- `git config --local user.name 'joe.doe'` adds a user name.
- `git config --local user.email 'joe.doe@gmail.com'` adds a user email.
- `git config --local core.editor 'code --wait'` adds a default editor path. In that case visual studio code shortcut.

#### Global

Git configuration affects all repositories in the user session. Ideal when you dont want to show the same information in all repositories.

**Linux file path**: /home/user/.gitconfig
**Windows file path**: C:Users/<your user>/.gitconfig

- `git config --global --list` shows a list of global configurations.
- `git config --global user.name 'joe.doe'` adds a user name.
- `git config --global user.email 'joe.doe@gmail.com'` adds a user email.
- `git config --global core.editor 'code --wait'` adds a default editor path. In that case visual studio code shortcut.

#### System

Git configuration affects all repositories in all user session.

**Linux file path**: /etc/gitconfig
**Windows file path**: C:/ProgramData/Git/config

- `git config --system --list` shows a list of global configurations.
- `git config --system user.name 'joe.doe'` adds a user name.
- `git config --system user.email 'joe.doe@gmail.com'` adds a user email.
- `git config --system core.editor 'code --wait'` adds a default editor path. In that case visual studio code shortcut.

### Prepare the staging area

- `git status` displays the staging area status (file outside or inside the staging area).
- `git add README.md` adds a file to staging area.
- `git restore README.md` restores the file to the actual commit if it was modified.
- `git reset README.md` unstages the file.

### Prepare to commit

- `git commit` opens default editor and makes a commit (when close editor).
- `git commit -m 'Write the first commit'` makes a commit with a message in git bash.
- `git commit -am 'Write the second commit'` makes a commit only with tracked files (files that is in latest commit).
- `git commit --amend` allows you to modify the latest commit.

### Audit to the commit history

#### Log

- `git log` displays the details commit history
- `git log -n 3` displays n details commits.
- `git log --oneline` displays each commits as a single-line view.
- `git log --graph` displays a graphic relation of each commits.
- `git log -n 5 --oneline --graph` displays latest 5 commits as a single-line view with a graphic relation between each one.

#### Diff

##### Working directory

- `git diff README.md` compares the file in working directory with the file in the last commit.
- `git diff <commit> -- README.md` compares the file in working directory with the file in a specific commit.
- `git diff <commit> <commit> -- README.md` compares the file in two specific commits.
- `git diff <commit> <branch> -- README.md` compares the file in working directory with the file in a specific commit into a specific branch.

##### Staging area

- `git diff --staged README.md` compares the file in staging area with the file in the latest commit.
- `git diff --staged <commit> -- README.md` compares the file in staging area with the file in a specific commit.
- `git diff --staged <commit> <branch> -- README.md` compares the file in staging area with the file in a specific commit into a specific branch.

### Manage commit

- _`git reset --soft HEAD~1`_ reset the commit history n commits back, preserving the staged changes. **Be careful to use it in a share repository**
- _`git reset --hard HEAD~1`_ reset the commit history n commits back, without preserving the staged changes. **Be careful to use it in a share repository**
- `git revert HEAD` revert n commit safety by creating an inverse commit. In that case the current commit. Useful for share repository.

### Stash

Stash command is usually used for cleaning the directory without lose your current changed, saving in a temporal copy.

**File path**: <your repository>/.git/refs/stash

- `git stash list` displays a stash list.
- `git stash push -m 'Temporal data'` saves the file tracked as a temporal copy (doesn't include untracked file).
- `git stash push -u -m 'Temporal data'` saves the file tracked/untracked as a temporal copy (doesn't include ignored files).
- `git stash push -a -m 'Temporal data'` saves all the files as a temporal copy.
- `git stash apply` brings back the latest stash whitout deleting it.
- `git stash apply stash@{0}` brings back a specific stash whitout deleting it.
- `git stash pop` brings back the latest stash deleting it in a process.
- `git stash pop stash@{0}` brings back a specific stash deleting it in a process.
