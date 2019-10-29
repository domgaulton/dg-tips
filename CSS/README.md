# CSS

## CSS Grid
See - https://developer.mozilla.org/en-US/docs/Glossary/Grid
See - http://grid.malven.co/
`display: grid` property to signify CSS Grid on containing div
`grid-template-columns: 1fr 1fr auto` or `grid-template-columns: repeat(4, 1fr)` fractions of width and auto fill
`grid-template-columns: repeat(auto-fill, minmax(200px, 1fr))` great for responsive!

## SCSS & BEM
* Targeting an element inside a modifier

```html
<div class="block">

  <div class="block__element">
  </div>

  <div class="block__element">
  </div>
</div>

<div class="block block--modified">

  <div class="block__element">
  </div>

  <div class="block__element">
  </div>
</div>
```

```
.block {
  background: white;

  &__element {
    background: block;
  }

  &--modified {
    background: black;

    &__element {
      background: white;
    }
  }
}
```