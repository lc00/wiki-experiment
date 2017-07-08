## Variables

`$purple: #f0f !default;`

* Variables follow scoping rules
* `!default` uses inherited value if not overridden

## Nesting

```scss
ul {
    li {
        color: $purple
    }
}
```

## Partials

`_template_name.scss`  
`@import "template_name";`

* Only used with `@import`, not processed into CSS

## Mixins

```scss
@mixin border-radius($radius) {
    -webkit-border-radius: $radius;
}
.bordered {
    @include border-radius(10px);
}
```

## Inheritance

```scss
.parent {
    color: red;
}
.child {
    @extend .parent !optional;
    font-size: 1.5rem;
}
```

* `!optional` allows for null includes

## Operators

`-` `+` `/` `*` `%`

## Namespaced Properties

```scss
body {
    font: {
        family: arial;
        weight: 700;
    }
}
```

## Conditionals

```scss
@if $boolean_value {
    color: red;
} @else if ($other_value) {
    color: blue;
} @else {
    color: green;
}
```

## For Loops

```scss
$for $i from 1 through 3 {
    .item-#{$i}{
        color: black;
    }
}
```

## Each Loop

```scss
@each $var in $map_or_list {
    .#{var}-icon {
        color: blue;
    }
}
```

* Can do multiple variables

## While Loops

```scss
@while $i > 0 {
    // Something
    // $i = $i - 1;
}
```

## Functions

```scss
@function name($variable){
    @return $variable + 2px;
}
```

* Predefined functions for color, opacity, strings, numbers, lists, maps, selectors and introspection

## Notes

* Reference parent with &, can also be a partial name
* Comments can be `/* */` or `//`
* Can concatenate strings
* Media queries can be embedded inside nested rules
* `@at-root` inserts rule in the root level
* `@debug` and `@warn` send messages to the error output
