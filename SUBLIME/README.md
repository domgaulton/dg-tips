# Sublime 3

## User settings
```json
{
  "tab_size": 2,
  "translate_tabs_to_spaces": true,
}
```

## EsLint Plugin
1. Install eslint globally `npm install -g eslint`
2. Install Package Manager for Sublime (`cmd + shift + p` and type Install Package)
3. Install `SublimeLinter` package - http://www.sublimelinter.com/en/stable/
4. Install `SublimeLinter-contrib-eslint` - So it knows to look at the JavaScript https://github.com/sublimelinter/sublimelinter-eslint
5. Restart Sublime

## Editor config
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
