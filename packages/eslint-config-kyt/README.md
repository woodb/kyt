# kyt ESLint Linter and JavaScript Style Guide

This is an extension of the Airbnb [**JavaScript**](https://github.com/airbnb/javascript) and [**React**](https://github.com/airbnb/javascript/tree/master/react) style guides and [ESLint](http://eslint.org/) linter. Overrides, additions and warnings have been added to this document and the project lint configuration.

## Table of Contents

1.  [Install](#install)
1.  [JavaScript Overrides](#javascript-overrides)
1.  [React Overrides](#react-overrides)
1.  [ESLint Additions](#eslint-additions)
1.  [Changelog](#changelog)

## Install

Note, installing `kyt` or setting up a `starter-kyt` will install this package automatically. If you want to install this linter extension separately, follow these install instructions. If you have `kyt` installed and you want to override the linter configuration, skip to step (2).

1. Install the _eslint-config-kyt_ node module and its dependencies:
   ```sh
   npm i  --save-dev eslint babel-eslint prettier eslint-config-airbnb eslint-config-kyt eslint-plugin-import eslint-plugin-json eslint-plugin-jsx-a11y eslint-config-prettier eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks
   ```
2. Copy the following into an `.eslintrc.js` in your project:

```js
module.exports = {
  extends: 'eslint-config-kyt',
  rules: {
    /* If you must, override rules here :P */
  },
};
```

## Prettier Support

If you need to format code in your codebase, run this command:

```
npx eslint src --fix
```

`starter-kyt`s add the `lint-fix` command to your `package.json` set of `scripts`.

To keep things formatted as you develop, install an editor package. See more [here](/docs/Recipes.md#editor-configuration).

## JavaScript Overrides

**[11.1 _Don't use iterators._](https://github.com/airbnb/javascript#iterators--nope)** - This eslint rule has been overridden to allow iterators, but using JavaScript higher-order functions is still preferred.

**[11.2 _Don't use generators for now._](https://github.com/airbnb/javascript#generators--nope)** - This eslint rule has been overridden. It is ok to use generators in node.js but it is advised not to use them on the client-side.

**[19.2 Additional trailing comma: Yup. eslint: comma-dangle](https://github.com/airbnb/javascript#commas--dangling)** - This eslint rule is overridden for functions to work with older versions of node.

## React Overrides

**[Ordering](https://github.com/airbnb/javascript/tree/master/react#ordering)** - Nah.

## Eslint Additions

**[no-lonely-if](http://eslint.org/docs/rules/no-lonely-if)** - _Disallow if as the only statement in an else block._

**[max-nested-callbacks](http://eslint.org/docs/rules/max-nested-callbacks)** - _Enforces a maximum depth that callbacks can be nested to increase code clarity._ (5)

**[constructor-super](http://eslint.org/docs/rules/constructor-super)** - _Aimed to flag invalid/missing super() calls._

**[no-this-before-super](http://eslint.org/docs/rules/no-this-before-super)** - _Aimed to flag this/super keywords before super() callings._

**[prefer-spread](http://eslint.org/docs/rules/prefer-spread)** - _Aimed to flag usage of Function.prototype.apply() that can be replaced with the spread operator._

## Changelog

**1.0.0-alpha.4** - 2/1/20

- Upgrades all `peerDependencies` to latest

**1.0.0-alpha.2** - 10/23/17

- Upgrades babel-eslint and makes it a proper `peerDependency`

**1.0.0-alpha.1** - 10/23/17

- Upgrades ESLint and dependencies to 3.19.0 and Prettier to 1.5.2.

**0.5.0** - 09/16/17

- Adds rule to restrict server imports. If you have a `src/server` directory, you will need to add this [.eslintrc.js](https://github.com/NYTimes/kyt/blob/965bb7b7cd244822e353795195c7d3f22c50fac1/packages/kyt-starter-universal/starter-src/src/server/.eslintrc.js) into the root of the server directory. This may be a breaking change if you have any server imports in your project from outside of the `src/server` directory.

**0.4.0** - 07/07/17

### BREAKING CHANGES

1. Adds Prettier which may be a breaking change as your files might need some minor linting updates. Install Prettier into your favorite editor and/or `node_modules/.bin/prettier-eslint src/**/*.js --write` to apply the updates. If you manually installed, please note the new Prettier modules above that need to be installed.
2. Upgrades the following eslint plugins:

- _eslint-config-airbnb_ from [14.1.0 to 15.0.2](https://github.com/airbnb/javascript/blob/master/packages/eslint-config-airbnb/CHANGELOG.md)
- _eslint-plugin-import_ from [2.2.0 to 2.7.0](https://github.com/benmosher/eslint-plugin-import/blob/master/CHANGELOG.md)
- _eslint-plugin-jsxa11y_ from [4.0.0 to 5.1.1](https://github.com/evcohen/eslint-plugin-jsx-a11y/blob/master/CHANGELOG.md)
- _eslint-plugin-react_ from [6.10.0 to 7.1.0](https://github.com/yannickcr/eslint-plugin-react/blob/master/CHANGELOG.md)

**0.3.2** - 04/09/17

Upgrades eslint to version [3.19](https://github.com/eslint/eslint/blob/master/CHANGELOG.md) for fix below.

### BREAKING CHANGES

### FEATURES

### FIXES

- fixes `no-restricted-syntax` error in linter [#459](https://github.com/NYTimes/kyt/pull/459).

**0.3.1** - 03/27/17

Upgrades eslint to version [3.18](https://github.com/eslint/eslint/blob/master/CHANGELOG.md) for fix below.

### BREAKING CHANGES

### FEATURES

### FIXES

Fixes the following error:

```
Configuration for rule "no-unused-expressions" is invalid:
Value "data["0"].allowTaggedTemplates" has additional properties.
```

More here: https://github.com/eslint/eslint/issues/7632

**0.3.0** - 03/23/17

This release upgrades linter dependencies, fixing (among other things) `no-unused-prop-types` false positives:

- _eslint_ from [3.8.1 to 3.16.1](https://github.com/eslint/eslint/blob/master/CHANGELOG.md)
- _eslint-config-airbnb_ from [12.0.0 to 14.1.0](https://github.com/airbnb/javascript/blob/master/packages/eslint-config-airbnb/CHANGELOG.md)
- _eslint-plugin-import_ from [1.16.0 to 2.2.0](https://github.com/benmosher/eslint-plugin-import/blob/master/CHANGELOG.md)
- _eslint-plugin-jsxa11y_ from [2.2.3 to 4.0.0](https://github.com/evcohen/eslint-plugin-jsx-a11y/blob/master/CHANGELOG.md)
- _eslint-plugin-react_ from [6.4.1 to 6.10.0](https://github.com/yannickcr/eslint-plugin-react/blob/master/CHANGELOG.md)

### BREAKING CHANGES

### FEATURES

### FIXES

**0.2.0** - 02/07/17

### BREAKING CHANGES

`dependencies` were converted to `peerDependencies` and `kyt` now includes the dependencies. If you're using `kyt`, then an `npm install` should be enough. If you installed this package as a standalone extension then you'll need to follow the Installation instructions and `npm install` the named dependencies.

### FEATURES

### FIXES

**0.0.1 - 0.1.0 ** - 12/08/16 - life
