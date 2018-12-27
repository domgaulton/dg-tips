# dg-tips
Tips on all things FE

## Terminal

#### Create folder


#### Create file

## Javascript

### Terminology

#### Functions
#### Objects
#### Arrays

## Git

### Commands

#### Add local repo to github
1. Add repo on github
2. cd to local repo then `git init`
3. if you want to ignore node_modules (advised) run `touch .gitignore` and github will add a decent gitnore file
4. follow `git add [file]` below until `git commit`
5. `git remote add origin [url]` add git remote to project
6. `git push -u origin master` push it to master branch

#### Clone
`git clone https://github.com/domgaulton/dg-tips.git`
Clone a repository to your local drive

#### Git Status
`git status`
shows what has been modified in working directory

#### Add
`git add [file]` 
Add file or files updates so that git tracks it, use `.` to add all updated files

#### Commit
`git commit -m'lorem ipsum'`
Commit added files from above and add a commit message

#### Push
`git push`
Push committed files to the branch you're on

#### Pull
`git pull`
fetch and merge any commits from the tracking remote branch

#### Useful Links
https://education.github.com/git-cheat-sheet-education.pdf

## NPM

### Intro
`npm init` Creates a package.json file in the folder (add `npm init -y` to say Yes to all questions)

### Install from package.json
`npm install` runs package.json 

### Dev dependencies
`-dev` Installs only in development mode