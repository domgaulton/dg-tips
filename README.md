# dg-tips
Tips on all things FE

## Table of Contents
* [Terminal](#terminal)
* [Javascript](#javascript)
* [Javascript ES6](#javascript-es6)
* [Git](#git)
* [NPM](#npm)

## Terminal

#### Create folder
`mkdir [folder name]` - make directory

#### Create file
`touch [filename.filetype]` - create file

#### Change Directoy
`cd [folder]` || `cd ..` - move into another child directory || move up one directory

## Javascript

#### Terminology

#### Functions
#### Objects
#### Arrays

## Javascript ES6

#### Const and Let (block scoping)
`const x =` used when we don't want variable to change (note it can still be added to e.g. in an Array method such as `.push()`)
`let y =` used when variable might change in new block of code / class / function. Inner Block Scope prevents variable being changed outside of variable and vica versa

#### Template Literals (backticks)
Great for injecting inline
```
const name = 'Foo';
const hello = `Hello ${name}`
console.log(hello); // 'Hello Foo'
```

#### Spread Operator (...)
No need to concat anymore...
```
let a = [7, 8, 9];
let b = [6, a..., 10];
console.log(b); // [6, 7, 8, 9, 10]
```

Or we can add to an array from comma seperated list...
```
function spread(...a) {
  console.log(a)
};
spread(1, 2, 3, 4, 5); // [1, 2, 3, 4, 5]
```
```
function spreadAdd(...b) {
  let a = [1, 2, 3,...b];
  return a;
}

spreadAdd(4, 5, 6); // [1, 2, 3, 4, 5, 6]
```

### Destructuring
Used instead of [0], [1] etc
```
let items = [1, 2, 3, 4, 5]
let [a, b] = items;
console.log(b); // 2
```
## Git

#### Clone
`git clone https://github.com/domgaulton/dg-tips.git`
Clone a repository to your local drive

#### Git Status
`git status`
shows what has been modified in working directory

#### Add
`git add [file]` 
Add file or files updates so that git tracks it, use `.` to add all updated files

#### Un Add
`git reset HEAD [file]` 
Removes (unstages) file

#### Commit
`git commit -m 'lorem ipsum'`
Commit added files from above and add a commit message


#### Push
`git push`
Push committed files to the branch you're on

#### Pull
`git pull`
fetch and merge any commits from the tracking remote branch

#### Add local repo to github
1. Add repo on github
2. cd to local repo then `git init`
3. if you want to ignore node_modules (advised) run `touch .gitignore` and github will add a decent gitnore file
4. follow instructions from `git add [file]` until `git commit`
5. `git remote add origin [url]` add git remote to project
6. `git push -u origin master` push it to master branch

#### Useful Links
https://education.github.com/git-cheat-sheet-education.pdf

## NPM

#### Intro
`npm init` Creates a package.json file in the folder (add `npm init -y` to say Yes to all questions)

#### Install from package.json
`npm install` runs package.json 

#### Dev dependencies
`-dev` Installs only in development mode