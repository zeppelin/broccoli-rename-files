# [broccoli](https://github.com/joliss/broccoli)-rename-files [![Build Status](https://travis-ci.org/zeppelin/broccoli-rename-files.svg?branch=master)](https://travis-ci.org/zeppelin/broccoli-rename-files)

Rename files in a tree. Currently only prepend/append is supported and doesn't touch file extensions, but will eventually add more features.

## Install

```sh
$ npm install --save broccoli-rename-files
```


## Usage

```js
var renameFiles = require('broccoli-rename-files');
tree = renameFiles(tree, {
  prepend: 'wow-',
  append: '-new'
});
```


## API

### renameFiles(tree, options)

#### Options

`options.prepend` *{String}* Optional. The string to be prepended to the filename.

`options.append` *{String}* Optional. The string to be appended to the filename.


## License

MIT &copy; [Gabor Babicz](http://zeppelin.im)
