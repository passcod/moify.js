# Moify library

[![Greenkeeper badge](https://badges.greenkeeper.io/passcod/moify.js.svg)](https://greenkeeper.io/)

This is the official library for the [moify.me] service. It is used
internally by the web interface.

Moify is a rate-limited service, this library is low-level and will
return a fail if you hit the limit, leaving you to handle this and/or
retry later. In this case, please follow an exponential backoff.

## Install

    npm install --save moify

## Usage

```js
let moify = require('moify')

moify.url('')
.then(moifiedUrl => void console.log(moifiedUrl))
.catch(console.error)

moify.file('/path/to/file.png') // or jpeg, or gif, or webm...
.then(moifiedBlob => {})

require('fs').createReadStream('file.gif').pipe(moify.blob())
moify.blob(require('fs').readFileSync('file.jpg')) // Buffers are fine

moify.cache('17264a72f73bc9233d83474e274f274237')
.then(moifiedUrl => {})
```

## API

Promises are native ES6, and may be consumed by any Promise-aware library.

In browser environments, `Blob`s are used where `Buffer`s are specified below,
and the Stream variants are not available. In browsers where native Promises
are not available, they are shimmed using jakearchibald's ES6 Promise polyfill.

### moify.url(url: String[, options: Object]) -> Promise

//

### moify.url([options: Object]) -> StreamReadWriter

//

### moify.file(filename: String[, options: Object]) -> Promise

//

### moify.file([options: Object]) -> StreamReadWriter

//

### moify.blob(image: Buffer[, options: Object]) -> Promise

//

### moify.blob([options: Object]) -> StreamReadWriter

//

### moify.fromHash(hash: String[, options: Object]) -> Promise

//

### moify.fromHash([options: Object]) -> StreamReadWriter

//

## Options

### storage: 's3' | false

//

### hash: String | Buffer

//

### shape: Not Implemented

//

### position: Not Implemented

//

### apikey: Not Implemented

//

## About

Licensed under [MIT].

[MIT]: http://passcod.mit-license.org
[moify.me]: https://moify.me
