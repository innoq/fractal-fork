fractal-fork
============

<p>
  <a href="https://www.npmjs.com/package/fractal-fork" title="Current version">
    <img src="https://img.shields.io/npm/v/fractal-fork.svg" alt="">
  </a>
  <!-- License -->
  <a href="https://github.com/frctl/fractal/blob/main/LICENSE" title="MIT license">
    <img alt="GitHub" src="https://img.shields.io/github/license/frctl/fractal">
  </a>
</p>

This is a fork of the open-source [Fractal][docs] tool for helping you **build** and **document** website component libraries and design systems.

Those familiar with [Fractal][docs] will know that it is a great tool for developing lightweight frontend components without being dependent on any heavy JavaScript framework.

Unfortunately, Fractal has suffered over the years with out-of-date dependencies and is now officially
[unmaintained](https://github.com/frctl/fractal/issues/1167).
I use Fractal frequently and successfully in customer projects and therefore have the desire to maintain a _version_ of Fractal with up-to-date dependencies, but I do not use all of the features of the official branch, so I am providing this fork instead.

**The goal of this fork is to maximize maintainability for customer projects and _not_ to provide complete feature parity with the official branch.** The project is therefore developed with the following concrete goals:

1. Maximize maintainability by reducing size of source code
2. Minimize number of dependencies

I use real Fractal projects to test any changes that I make to the source code. However, this also means that **any feature that I do not personally use for any Fractal projects is at risk of being removed in the future** (especially if it uses dependencies which are poorly maintained).

## Migration Guide from `@frctl/fractal` to `fractal-fork`

The changes to offical Fractal branch are listed here as follows:

* `fractal-fork` uses a single repository for ease of deployment. To migrate from `@frctl/fractal` to `fractal-fork` do the following:
  * Replace `require('@frctl/core')` with `require('fractal-fork').core`
  * Replace `require('@frctl/fractal')` with `require('fractal-fork').fractal`
  * Replace `require('@frctl/handlebars')` with `require('fractal-fork').handlebars`
  * Replace `require('@frctl/mandelbrot')` with `require('fractal-fork').mandelbrot`
  * Replace `require('@frctl/web')` with `require('fractal-fork').web`
* Replace the `fractal` command in your package.json scripts with `fractal-fork`
* `fractal-fork` does not support the `twig`, `nunjucts`, or `react` adapters (if you still need them, it should be possible for you to maintain a separate fork for those adapters)
* `fractal-fork` does not support the `new` CLI command (it's a command I've rarely used because I usually create the repository structure and `fractal.config.js` by hand and the CLI was one area which had horrible dependencies which needed to be removed)
* The CLI output for `fractal-fork` is much less pretty -- there are no colors and the console never overwrites previous log output. This means particularly for the `build` command that the console output is much longer
* Automatic port discovery is not supported for `fractal-fork`. If a port is blocked, `fractal-fork` will quit with an error and it is the developer's responsibility to set a different port via `--port`.


[Read the full Fractal documentation][docs]

## Introduction to Fractal

Component (or pattern) libraries are a way of designing and building websites in a modular fashion, breaking up the UI into small, reusable chunks that can then later be assembled in a variety of ways to build anything from larger components right up to whole pages.

Fractal helps you assemble, preview and document website component libraries, or even scale up to document entire design systems for your organisation.

Check out the [documentation][docs] for more information.


## Getting started

### Install into your project (recommended)

```shell
npm install fractal-fork --save-dev
```

Then create your `fractal.config.js` file in the project root, and configure using the [official documentation][docs] but keeping in mind the changes to imports listed out in [the migration guide](#migration-guide-from-frctlfractal-to-fractal-fork).

An example pattern library using the `fractal-fork` library can be found in the `example` folder.

Then you can either run `npx fractal start` to start up the project, or create an alias under the `scripts` section in your package.json as a shortcut.

e.g.

```json
"scripts": {
    "fractal:start": "fractal-fork start --sync",
    "fractal:build": "fractal-fork build"
}
```

then

```shell
npm run fractal:start
```

### Submitting pull requests

We will always welcome pull requests on any of the [frctl organisation](https://github.com/frctl) repositories. Please submit PRs against `main` branch with an explanation of your intention.

We use [conventional commits](https://www.conventionalcommits.org/), which means that every pull request title should conform to the standard.

### Development

## Testing

Existing tests can be run using the `npm test` command.

## License

[MIT](https://github.com/frctl/fractal/blob/main/LICENSE)

[docs]: https://fractal.build
