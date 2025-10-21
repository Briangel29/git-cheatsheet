# Binnacle

I will type git cases and their solutions, starting with the easiest ones and moving up to more complex cases (personal attempt).

# 1. First commit with a local user information.

```git
git init

git remote add origin https://github.com/Briangel29/git-binnacle.git

git config --local user.name briangel
git config --local user.email briangel@gmail.com
git config --local core.editor 'code --wait'

touch README.md

git add README.md
git status

git commit -m '1. First commit with a local user information'
git log

git push origin main

```
