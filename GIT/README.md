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
* `git add {file}` - Add file or files updates so that git tracks it, use `.` or `--a` to add all updated files

## Un-add (unstage / remove) from repository
* `git reset HEAD` - Removes all changes that you've done on the branch
* `git reset HEAD {file}` - Removes (unstages) file

## Remove file / directory from git
* `git rm -r {file or directory}` - Removes file from git (-r = recursive for directories)

## Git diff
* `git diff` to see old and new between files.
* `git diff --a -p` patch through each commit line and stage or unstage on a line per line perspective.
**HINT**: Use `?` to see list of what commands you can use https://git-scm.com/docs/git-add#Documentation/git-add.txt--p
```
y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk or any of the later hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
e - manually edit the current hunk
? - print help
```


## Commit
* `git commit -m 'lorem ipsum'` - Commit added files from above and add a commit message

## Reset file to last commit
* `git checkout -- {file}` - Removes local changes

## Push
* `git push {origin} {branch-name}` -Push committed files to repo where {origin} and {branch} are optional. Defaults to origin and master

## Pull
* `git pull` -fetch and merge any commits from the tracking remote branch

## Create new branch
* `git checkout -b {branch-name}`
create new branch on repository

## Change to another existing branch
* `git checkout {branch-name}`

## Git Stash
* Save local files whilst changing branches. Below stashes branch and then adds it to the new branch after you check that out
```
git stash
git checkout -b {new-branch-name}
git stash pop
```

## Git interative add all
* `git add --a -p`
* `? [enter]`

## Merge branch to master
1. Start a new feature from development branch
```
git checkout {development-branch}
git checkout -b {new-feature}
```
2. Edit some files
`git add {file}`
`git commit -m "Start a feature"`
3. Edit some files
`git add {file}`
`git commit -m "Finish a feature"`
4. Ensure your branch has latest from main branch (e.g. master / develop)
`git rebase {development-branch}` or `git merge {development-branch}` or from another branch `git fetch develop/feature/ABC-123`
5. Merge in the new-feature branch (but recommended to use a pull request)
`git checkout master`
`git merge {new-feature}`
`git branch -d {new-feature}`

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

## Git Flow
* Used for features, bugs - https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
* Install - `brew install git-flow`
* Creating and finishing branches
```
git flow feature start feature_branch branched_from
git flow feature finish feature_branch branched_from
```
* Where `feature_branch` is your branch name and `branched_from` is for example `develop` or `release_branch`
```
$ git flow hotfix start hotfix_branch
$ git flow hotfix finish hotfix_branch
```

## Git Cherrypick
* Pull code from specific commits `git cherry-pick [01ab98]` with commit id

#### Useful Links
https://education.github.com/git-cheat-sheet-education.pdf
http://makeapullrequest.com/
