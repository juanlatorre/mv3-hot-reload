# mv3-hot-reload

Enable hot reloading for content script and background script (service worker) in MV3.

## Install

```
yarn add mv3-hot-reload
```

## Usage

### 1. Import files into your background script (service worker) and content script

The code for hot reloading will only execute when `process.env.NODE_ENV === 'development'`.

```ts
// background.ts
import 'mv3-hot-reload/background'

// your code...
```

```ts
// content.ts
import 'mv3-hot-reload/content'

// your code...
```

### 2. Add a script to your `package.json` and run it before development

Example:

```diff
    "watch:src": "webpack --config webpack/webpack.dev.js --watch",
+   "watch:dist": "mv3-hot-reload",
+   "dev": "concurrently yarn:watch:*",
```

## mv3-hot-reload.config.js

```js
module.exports = {
  // Specify the port of hot reload server, defaults to 9012
  port: 9012,
  // Specify the directory you want to watch, defaults to 'dist
  directory: 'dist',
  // Specifies an array of filenames that should be excluded in watched directory
  exclude: [],
}
```

## Example

[pacexy/chrome-extension-typescript-starter](https://github.com/pacexy/chrome-extension-typescript-starter)

## Credits

The implementation of hot reloading in mv3 refers to [theprimone/violet](https://github.com/theprimone/violet).

## License

MIT
