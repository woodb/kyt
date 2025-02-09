# kyt Stylelint Linter and CSS/Sass Style Guide

This is an extension of [stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard) with some overrides for CSS/Sass Modules.

## Table of Contents

1. [Install](#install)
1. [CSS + Sass Guide](#css--sass-guide)
   - [Formatting](#formatting)
   - [Comments](#comments)
   - [ID Selectors](#id-selectors)
   - [Syntax](#syntax)
   - [Ordering](#ordering-of-property-declarations)
   - [Variables](#variables)
   - [Mixins](#mixins)
1. [Changelog](#changelog)

## Install

If you want to install this linter extension, follow these install instructions.

1. Install the `stylelint-config-kyt` npm package:
   ```
   npm i --save-dev stylelint stylelint-config-kyt stylelint-config-standard
   ```
1. Add a `.stylelintrc` file to your project's root
1. Add configuration:

```json
{
  "extends": "stylelint-config-nyt",
  "rules": {}
}
```

## CSS + Sass Guide

The following guide is best used with the `kyt` linter against CSS/Sass Modules.

### Formatting

- Use soft tabs (2 spaces) for indentation.
- Always use camelCasing in class names.
- Do not use ID selectors.
- Do not use element selectors in CSS Modules files.
- When using multiple selectors in a rule declaration, give each selector its own line.
- Put a space before the opening brace `{` in rule declarations.
- In properties, put a space after, but not before, the `:` character.
- Put closing braces `}` of rule declarations on a new line
- Put blank lines between rule declarations and nested pseudo-selectors.

**Bad**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}
.no,
.nope,
.not_good {
  // ...
}
#lol-no {
  // ...
}
```

**Good**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.perLine {
  // ...
}
```

### Comments

- Prefer line comments (`//` in Sass-land) to block comments.
- Prefer comments on their own line.
- Write detailed comments for code that isn't self-documenting:
  - Uses of z-index
  - Compatibility or browser-specific hacks

### ID selectors

While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) to your rule declarations, and they are not reusable.

You should never define an ID selector in a CSS Module.

### Syntax

- Use the `.scss` syntax, never the original `.sass` syntax
- Order your regular CSS and `@include` declarations logically (see below)

### Ordering of property declarations

1. `@include` or `composes` declarations
2. Property declarations in alphabetical order

   ```scss
   .btnGreen {
     @include transition(background 0.5s ease);
     background: green;
     color: red;
     font-weight: bold;
     // ...
   }
   ```

3. Nested pseudo-selectors

   Nested pseudo-selectors go last, and nothing goes after them.

   ```scss
   .btn {
     @include color(red);
     font-weight: bold;

     &:hover {
       cursor: pointer;
     }
   }
   ```

### Variables

Prefer camelCased variable names (e.g. `$myVariable`).

### Mixins

- 1 space after the mixin name before the opening parens
- 1 space after colons and between params
- Commas are used as separators unless passing in a comma separated list as an argument, in these cases use a semicolon
  Default values can be used when it's convenient
