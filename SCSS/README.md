# SCSS

## SCSS & BEM
* Targeting an element inside a modifier and `#{ $self }` scope

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

## Using Scope `#{ $self }`

```scss
.block {
  $self: &; // set self as scope
  background: white;

  &__element {
    background: black;

    #{ $self }--modified & { // use self scope
      background: white
    }
  }

  &--modified {
    background: red;

    #{ $self }__element { // use self scope
      background: white;
    }
  }
}
```