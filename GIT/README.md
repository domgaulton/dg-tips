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
* `git reset HEAD` - Removes all changes that you've done on the branch
* `git reset HEAD {file}` - Removes (unstages) file

## Remove file / directory from git
* `git rm -r {file or directory}` - Removes file from git (-r = recursive for directories)

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

## Merge branch to master
1. Start a new feature
`git checkout -b {new-feature} master`
2. Edit some files
`git add {file}`
`git commit -m "Start a feature"`
3. Edit some files
`git add {file}`
`git commit -m "Finish a feature"`
4. Ensure your branch has latest from main branch (e.g. master / develop)
`git rebase {branch}` or `git merge {branch}` or `git fetch develop/feature/ABC-123`
5. Merge in the new-feature branch
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


#### Useful Links
https://education.github.com/git-cheat-sheet-education.pdf
http://makeapullrequest.com/
