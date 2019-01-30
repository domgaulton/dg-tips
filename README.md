# dg-tips
Tips on all things FE

## Formatting
* Use `backticks` for something you would run in terminal
* Use bullet points for each block of instructions or
1. Numbered list
2. If you must
3. Follow a list 
4. Of Commands
5. In order
* For variables like file names use {curly-bracket} and lisp case (https://en.wikipedia.org/wiki/Naming_convention_(programming)#Lisp)
* For blocks of code use 3 back tickets and itentify the type of code it is

## Table of Contents
* [Terminal](/TERMINAL/README.md)
* [Javascript](/JS/README.md)
* [Javascript ES6](/JS/README.md)
* [Git](/GIT/README.md)
* [NPM](#npm)
* [CSS](#css)

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
