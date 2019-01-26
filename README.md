# dg-tips
Tips on all things FE

## Table of Contents
* [Terminal](#terminal)
* [Javascript](#javascript)
* [Javascript ES6](#javascript-es6)
* [Git](#git)
* [NPM](#npm)
* [CSS](#css)

## Terminal

#### Create folder
`mkdir [folder name]` - make directory

#### Create file
`touch [filename.filetype]` - create file

#### Change Directoy
`cd [folder]` || `cd ..` - move into another child directory || move up one directory

## Javascript

#### Get Elements
`document.querySelector('# or .')` - The Document method querySelector() returns the first Element

`document.querySelectorAll('# or .')` - returns a static (not live) NodeList

#### Element Attributes
`element.attributes` - List of all element details! Very useful



#### Terminology

#### Functions
#### Objects
#### Arrays

## Javascript ES6

### Arrow Functions

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

Destructure Object (old and new below)
```
let wizard = {magical: true, power: 10}
// let magical = wizard.magical;
// let power = wizard.power;
let { magical, power } = wizard;
console.log(magical, power) // true 10
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
`git push {origin} {branch name}`
Push committed files to repo where {origin} and {branch} are optional. Defaults to origin and master

#### Pull
`git pull`
fetch and merge any commits from the tracking remote branch

#### Create New Branch
`git checkout -b [branch name]`
create new branch on repository

#### Change To Another Existing Branch
`git checkout [branch name]`

#### Add local repo to github
1. Add repo on github
2. cd to local repo then `git init`
3. if you want to ignore node_modules (advised) run `touch .gitignore` and github will add a decent gitnore file
4. follow instructions from `git add [file]` until `git commit`
5. `git remote add origin [url]` add git remote to project
6. `git push -u origin master` push it to master branch

#### Reset file to last commit
`git checkout -- <file>` - Removes local changes

#### Reset Repo / Branch to old commit
`git reset --hard <old-commit-id>`
`git push -f` or `git push -f <remote-name> <branch-name>`

#### Useful Links
https://education.github.com/git-cheat-sheet-education.pdf
http://makeapullrequest.com/

## NPM

#### Intro
`npm init` Creates a package.json file in the folder (add `npm init -y` to say Yes to all questions)

#### Install from package.json
`npm install` runs package.json 

#### Dev dependencies
`-dev` Installs only in development mode

#### Node
* Gulp - 'internalBinding is not defined': run `npm install natives@1.1.6`  - https://github.com/gulpjs/gulp/issues/2246

## CSS

#### CSS Grid
See - https://developer.mozilla.org/en-US/docs/Glossary/Grid
See - http://grid.malven.co/
`display: grid` property to signify CSS Grid on containing div
`grid-template-columns: 1fr 1fr auto` or `grid-template-columns: repeat(4, 1fr)` fractions of width and auto fill 
`grid-template-columns: repeat(auto-fill, minmax(200px, 1fr))` great for responsive!
