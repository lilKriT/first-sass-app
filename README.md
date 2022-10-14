# first-sass-app

My first app using Sass.
Created by lilKriT.

# Extensions

.sass - specific to sass. Indentations instead of curly braces and no semicolons.
.scss - css compatible. More popular!

# Variables

`$name: value`
css now has variables, but this is a bit easier to write.

# Nesting

Instead of:

```
nav {

}
```

nav ul...
nav ul li...

you write

```
nav {
    ul {
        li {

        }
    }
}
```

# Modules / Partials

CSS can import files too but that creates multiple http requests.
Sass takes care of it during compilation.

Create a file, and in another file `@use 'filename';`
start the name with \_
`_base.scss` - this way it won't be compiled unless it's imported

# Mixins / Functions

```
@mixin transform($property) {
    transform: $property;
}
.box { @include transform(rotate(30deg));}
```

# Inheritance

```
%base-class {
    // style
}

.child-class {
    @extend %base-class;
}
```

# Operations

`width: 1920 / 4`

# Conditionals

```
@if $variable == value {
    // style
} @else if $variable == otherValue {

}
```

# Ampersand Parent

& means parent.
It can be used as

```
.hero {
    // style
}

&-content {
    // more style
}
```

# Lighten / Darken

`lighten($color, 10%)`
`darken($color, 10%)`

# Loops

```
$spaceAmounts: (1, 2, 3, 4, 5);

@each $space in $spaceAmounts {
    .m-#{$space} {
        margin: #{$space}rem;
    }
}
```

# Workflow

- create /css and /scss
- create style.scss
- `npm init -y`
- `npm i -g sass`
- add a script `sass --watch scss/style.scss css/style.css` or use live sass plugin
- optionally, create `_config.scss` with all the variables, functions, mixins etc and then import it with `@import "config"`

# General advice

- have different files for variables (config)
- have a file for utilities
- have a file for buttons etc
- inheritance is good for multiple buttons (every button has a border and padding, but some are green or blue)
- functions are good when you need conditional logic
- mixins are good when you want a few lines of code depending on one (set a background color, AND depending on that, text color)
- a mixin is a function that doesn't return anything
- make a `_mobile.scss` file for media queries
- location of `import` matters! so for example config on top, everything else on the bottom.

# Examples

function that changes color of text based on background

```
@function set-text-color($color) {
    @if(lightness($color) > 70) {
    @return #333;
} @else {
        @return #fff;
    }
}

.class{
color: set-text-color($background);
}
```

a mixin that sets background AND text color

```
@mixin set-background($color){
    background-color: $color;
    color: set-text-color($color);
}

.class {
    @include set-background($color);
}
```
