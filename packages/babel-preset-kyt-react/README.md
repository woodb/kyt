## babel-preset-kyt-react

[![npm](https://img.shields.io/npm/v/babel-preset-kyt-react.svg?maxAge=2592000)](https://www.npmjs.com/package/babel-preset-kyt-react)
This is a babel preset meant for React projects built with kyt.

See the included presets and plugins [here](/packages/babel-preset-kyt-react/lib/index.js)
(Note: this preset includes babel-preset-kyt-core)

To use in your project:

1. `npm install babel-preset-kyt-react --save`
2. In your .babelrc.js:

```js
module.exports = {
  presets: ['babel-preset-kyt-react'],
};
```

## Options

_(see [documentation](https://babeljs.io/docs/plugins/#plugin-preset-options) for Babel preset options)_

- `envOptions` (`Object`)- pass down babel-preset-env options to babel-preset-kyt-core. See more in the `envOptions` [kyt-core documentation](/packages/babel-preset-kyt-core/README.md#options).

- `includeRuntime` (`Boolean`)- whether or not to include [`babel-plugin-transform-runtime`](https://www.npmjs.com/package/babel-plugin-transform-runtime); default: `false`
