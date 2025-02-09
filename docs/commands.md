# kyt command line interface

`kyt` includes a CLI with all the commands needed for development.

`kyt setup` includes these commands as scripts in your `package.json`:

```
npm run dev
```

Or you can run a command with `npx kyt command`

```
npx kyt build
```

1. [`dev`](/docs/commands.md#dev) starts up a development environment
1. [`build`](/docs/commands.md#build) compiles server and client code for production use
1. [`setup`](/docs/commands.md#setup) is a tool for creating new kyt projects. It installs [`starter-kyt`s](/docs/Starterkyts.md) and all the tools you need to begin development.
1. [`list`](/docs/commands.md#list) provides information about available `starter-kyt`s
1. `--help` shows commands and their documentation

## `dev`

The `dev` command takes the entry `index.js` in `src/client/` and `src/server/`, compiles them, and starts client and backend servers. The dev environment includes hot-reloading to allow for fast development.

If `hasServer` is set to `false` in [kyt.config.js](/docs/kytConfig.md), `src/server/` is ignored and no backend server is started.

If `hasClient` is set to `false` in [kyt.config.js](/docs/kytConfig.md), `src/client/` is ignored and no client server is started.

Optionally, you can configure urls for the development servers in the [kyt config](/docs/kytConfig.md).

You can pass flags to the node server through `kyt dev`.
For example:

```
kyt dev -- --inspect
```

will run the [node debugging for Chrome DevTools](https://medium.com/@paul_irish/debugging-node-js-nightlies-with-chrome-devtools-7c4a1b95ae27#.mpuwgy17v)

## `build`

The `build` command takes the entry `index.js` in `src/client/` and `src/server/` (ignoring the latter if `hasServer` set to false in [kyt.config.js](/docs/kytConfig.md)), compiles them, and saves them to a build folder. This is an optimized production build.

The build command will also copy the `src/public` directory for static assets.

`build` uses option `-C`(`--config`) to denote a path to a different [kyt.config.js](/docs/kytConfig.md) file

### `setup`

The `setup` command sets up your project with all the application files that you'll need to use kyt:

1. Creates a new [kyt.config.js](/docs/kytConfig.md)
1. Install necessary npm packages
1. Creates a .gitignore and .editorconfig
1. Creates linter configurations - .eslintrc.js files
1. Adds kyt commands to npm scripts

If `kyt` finds any files with duplicate names, it will back up your file before replacing it.

`kyt setup` will take you through the process of setting up a new `kyt` project with a set of interactive questions. If you wish to automate this process you can use these optional flags:

- `-d` The name of the new project directory. If not specified `kyt` will install the project in your current working directory.
- `-r` The Github url for a `starter-kyt`. If not specified you will be prompted to select a `starter-kyt` from the supported list.
- `-k` For local development purposes, you can override the version of `kyt` to be installed by passing in a new version number or a file path eg. `file:../../my-local-kyt`
- `-p` The package manager to use, either `npm` or `yarn`. If not specified, defaults to `yarn` if it's installed globally, otherwise `npm` will be used.

kyt will provide you with a list of supported `starter-kyt`s to install. The supported `starter-kyt`s are:

- [kyt-starter-universal](/packages/kyt-starter-universal)
- [kyt-starter-static](/packages/kyt-starter-static)
- [kyt-starter-server](/packages/kyt-starter-server)

## `list`

The `list` command lists the supported `starter-kyt`s.
It includes:

- A description of best use cases
- Installation instructions

`kyt list`

### Recommended `starter-kyt`s

#### [Universal React `starter-kyt`](/packages/kyt-starter-universal)

This default `starter-kyt` is a good base for building advanced, universal React apps.

## Setup a new project

`kyt setup`

#### [Static `starter-kyt`](/packages/kyt-starter-static)

`kyt setup`
Select `I have my own url` when prompted to set up a `starter-kyt`

## Setup an existing project

Run `kyt setup` in your project directory.
Select `I don't want a starter-kyt` when prompted to setup.

## See a list of supported `starter-kyt`s

`kyt list`
