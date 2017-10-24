# [broccoli](https://github.com/joliss/broccoli)-rename-files [![Build Status](https://travis-ci.org/zeppelin/broccoli-rename-files.svg?branch=master)](https://travis-ci.org/zeppelin/broccoli-rename-files)

## Deprecated

This project has been **deprecated** in favor of [broccoli-funnel](https://www.npmjs.com/package/broccoli-funnel). Please see `getDestinationPath` for a corresponding API.

---

Rename files in a tree. Currently only prepend/append is supported and doesn't touch file extensions, but will eventually add more features.

## Install

```sh
$ npm install broccoli-rename-files
```

## Simple Usage

You can easily add text around a filename using the `prepend` and `append` options.
The following example renames `path/to/file.txt` to `path/to/wow-file-new.txt`

```js
var BroccoliRenameFiles = require('broccoli-rename-files');

tree = new BroccoliRenameFiles(tree, {
  prepend: 'wow-',
  append: '-new'
});
```

## Complex Usage

To achieve more complex renames, override the filter's  `transformFilename`
function. It receives the full filename, the basename, and the extension name
(as calculated by node's native
[path module](http://nodejs.org/docs/v0.4.9/api/path.html#path.basename)).
These arguments are somewhat redundant, but they allow you to easily construct
the filename you want.

For reference, here is the default implementation. Note that you can access
options on the filter:

```js
function(filename, basename, extname) {
  var prepend = this.options.prepend || '';
  var append = this.options.append || '';

  return prepend + basename + append + extname;
};
```

And here is a version that renames `foo.module.js` to `foo.js`.

```js
var BroccoliRenameFiles = require('broccoli-rename-files');

tree = new BroccoliRenameFiles(tree, {
  transformFilename: function(filename, basename, extname) {
    return filename.replace('.module', '');
  }
});
```

This filter is not intended to move files between directories. There are other
filters that do that well.


## API

### renameFiles(tree, options)

#### Options

`options.prepend` *{String}* Optional. The string to be prepended to the filename.

`options.append` *{String}* Optional. The string to be appended to the filename.

`options.keepOriginal` *{Boolean}* Optional. Whether to keep the original file as well.

## License

MIT &copy; [Gabor Babicz](http://zeppelin.im)
