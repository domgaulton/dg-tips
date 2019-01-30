# Git

## Git help
* `git --help` - Gives you list of commands

## Git status
* `git status` - Shows what has been modified in working directory

## Clone
* `git clone https://github.com/domgaulton/dg-tips.git` - Clone a repository to your local drive

## Rename file
* `git mv 'old file name' 'new file name'` - So that changes can still be tracked

## Add a file to the repository
* `git add {file}` - Add file or files updates so that git tracks it, use `.` to add all updated files

## Un-add (unstage / remove) from repository
* `git reset HEAD {file}` - Removes (unstages) file

## Commit
* `git commit -m 'lorem ipsum'` - Commit added files from above and add a commit message

## Reset file to last commit
* `git checkout -- {file}` - Removes local changes

## Push
* `git push {origin} {branch-name}`
Push committed files to repo where {origin} and {branch} are optional. Defaults to origin and master

## Pull
* `git pull`
fetch and merge any commits from the tracking remote branch

## Create new branch
* `git checkout -b {branch-name}`
create new branch on repository

## Change to another existing branch
* `git checkout {branch-name}`

## Delete a branch
* `git branch -D {branch-name}`

## Merge upstream branch to master
1. Checkout master branch `git checkout {master}` 
2. Pull changes from upstream branch `git pull https://github.com/{original-owner}/{original-repository}.git {branch-name}`
3. Address conflicts if there are any
4. Commit the merge
5. Push to master branch `git push origin {master}`

## Add local repo to github
1. Add repo on github
2. cd to local repo then `git init`
3. if you want to ignore node_modules (advised) run `touch .gitignore` and github will add a decent gitnore file
4. follow instructions from `git add [file]` until `git commit`
5. `git remote add origin [url]` add git remote to project
6. `git push -u origin master` push it to master branch

## Reset repository / Branch to old commit
* `git reset --hard {old-commit-id}`
* `git push -f` or `git push -f {remote-name} {branch-name}`

#### Useful Links
https://education.github.com/git-cheat-sheet-education.pdf
http://makeapullrequest.com/