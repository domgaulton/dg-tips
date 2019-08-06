# Sublime 3

## User settings

```json
{
  "tab_size": 2,
  "translate_tabs_to_spaces": true
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

## Current Styles 2019

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
