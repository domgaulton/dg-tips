# Drupal

## Get content array variables

On the `project.theme` add the following where `{template_name__here}` is the twig template `template-name--here.twig.html`

```
function {project}_preprocess_{template_name__here}(array &$variables) {
  dump($variables);
}
```

To get the array variable it can either be `theme_hook_original` name or look for an array with loads of children