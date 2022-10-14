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
