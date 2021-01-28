![Svelte for Meteor](banner.png)

Build [cybernetically enhanced web apps](https://svelte.dev) with Meteor and Svelte.

## Installation

To use `meteor-svelte`, run the following commands:

```
$ meteor add svelte:compiler
$ meteor npm install svelte@<version>
```

**Important:** The version of the `svelte` npm package should match the version of `svelte:compiler`.

To support legacy browsers, the package must be recompiled. This will be done automatically by Meteor by creating a symbolic link in the `imports` directory:

```
$ cd imports
$ ln -s ../node_modules/svelte .
```

## Options

Compiler options can be specified with a `"svelte:compiler"` property in `package.json`. For example:

```
{
  ...
  "svelte:compiler": {
    "extensions": ["svelte", "html"],
    "hydratable": true,
    "css": false
  }
}
```

**`extensions` (default: `["svelte"]`)**

An array of file extensions to be recognized by the package.
Note that HTML files are not compiled with the Svelte compiler if they contain top-level `<head>` or `<body>` elements.
Instead, the contents of the elements are added to the respective sections in the HTML output generated by Meteor (similar to what the `static-html` package does).

**`hydratable` (default: `false`)**

By default, Svelte removes server-rendered static HTML when the application is loaded on the client and replaces it with a client-rendered version.
If you want to reuse (hydrate) server-rendered HTML, set the `hydratable` option to `true` (which generates additional code for client components) and [use the `hydrate` option when instantiating your root component](https://svelte.dev/docs#Creating_a_component).

**`css` (default: `true`)**

Svelte can [extract styles for server-side rendering](https://svelte.dev/docs#Server-side_component_API).
If you want to render CSS on the server, you might want to set the `css` option to `false` so that client-rendered components don't insert CSS into the DOM.

## Server-Side Rendering

`meteor-svelte` supports server-side rendering with minimal configuration.
If you import Svelte components on the server, they are automatically built for server-side rendering.
See the [Svelte API docs](https://svelte.dev/docs#Server-side_component_API), the [example app](https://github.com/meteor-svelte/ssr-example), and the `hydratable` and `css` options above for more details.

## Examples

* [Apollo integration](https://github.com/meteor-svelte/apollo-example)
* [Tracker integration](https://github.com/meteor-svelte/tracker-example)
* [Server-side rendering](https://github.com/meteor-svelte/ssr-example)
* [Server-side rendering with Tracker integration](https://github.com/qnipp/meteor-svelte-tracker-ssr-example)
