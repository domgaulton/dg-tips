# NPM

## Intro

`npm init` Creates a package.json file in the folder (add `npm init -y` to say Yes to all questions)

## Install from package.json

`npm install` runs package.json

## Dev dependencies

`-dev` Installs only in development mode

## Node

- Gulp - 'internalBinding is not defined': run `npm install natives@1.1.6` - https://github.com/gulpjs/gulp/issues/2246

## Create and Deploy Package

1. Create folder and move into it `mkdir package-name` then  `cd package-name`
2. Set up npm by creating a package.json using `npm init` - Set up your `[npm-module-name]` for `name` and for `entry` use `index.js`
3. Create your index.js file `touch index.js`
4. Set up your package - remember from the directory in the terminal you can run `node index.js` to test the package
5. Publish to npm using `npm publish [npm-module-name]`
