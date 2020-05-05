# Sublime 3

## User settings

```json
{
  "tab_size": 2,
  "translate_tabs_to_spaces": true
}
```

## ES Lint
* Check if it's already installed `eslint -v`
* If not install using `npm install -g eslint`
* Note: You might need to install `npm install -g eslint-plugin-html` and `npm install -g eslint-plugin-markdown` the first time
* Run `eslint {filename.js}` in your terminal to see if it's working
* Create a eslintrc file - `touch .eslintrc` to create a configure file.
* Add the below json object to the file WHERE;
* `env` : your environments that you'll be working with https://eslint.org/docs/user-guide/configuring#specifying-environments
* `extends` : what your checking your code against - To install airbnb follow https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb (npm5+ and global install `npx install-peerdeps --dev eslint-config-airbnb -g`)
* `rules` : overwrites the extends rules

```js
{
  "env": {
    "es6": true,
    "browser": true
  },
  // "extends": "eslint:recommended", // Use this before installing airbnb plugin
  "extends": "airbnb", // https://github.com/airbnb/javascript
  "rules": {
    "no-console": 0, // no-console: 0 (off) ... therefore console functions are allowed. Other rules 1) warn 2) error - https://eslint.org/docs/rules/no-console
    "no-unused-vars": 1 // warning rather than error for unused vars - https://eslint.org/docs/rules/no-unused-vars
  },
  "plugins": ["html", "markdown"] // used for JavaScript in HTML <script> or ```js Markdown
}
```

* Install `sublimelinter eslint` in package control
* Sublime and other text editors need the `.eslintrc` file in project or anywhere in root of app to query against.

### ES Lint Plugin

1. Install eslint globally `npm install -g eslint`
2. Install Package Manager for Sublime (`cmd + shift + p` and type Install Package)
3. Install `SublimeLinter` package - http://www.sublimelinter.com/en/stable/
4. Install `SublimeLinter-contrib-eslint` - So it knows to look at the JavaScript https://github.com/sublimelinter/sublimelinter-eslint
5. Restart Sublime

### Editor config

```
# http://editorconfig.org
root = true

[*]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false
```

### Current Styles 2019

```
{
  "default_line_ending": "unix",
  "font_size": 12,
  "ignored_packages":
  [
    "Vintage"
  ],
  "tab_size": 2,
  "translate_tabs_to_spaces": true,
  "trim_trailing_white_space_on_save": true
}
```

## Git blame

- Make sure you have Git package installed then run Git Blame from package control `cmd + shift + p` then `Git Blame`
- To see who made the changes in too bar follow these instruction https://gist.github.com/rodrigobdz/dbcdcaac6c5af7276c63ec920ba894b0
