# bops

[![Build Status](https://travis-ci.org/chrisdickinson/tar-parse.png)](https://travis-ci.org/chrisdickinson/tar-parse)
[![TESTLING](https://ci.testling.com/chrisdickinson/bops.png)](https://ci.testling.com/chrisdickinson/bops)
[![NPM](https://nodei.co/npm/bops.png?downloads=true&stars=true)](https://nodei.co/npm/bops/)

buffer/typed array agnostic buffer operations.

`bops` presents a JavaScript API for working with binary data that will work exactly the same in supported browsers and in node. due to the way that `Buffer` is implemented in node it is impossible to take code written against the `Buffer` API and make it work on top of binary data structures (Array Buffers and Typed Arrays) in the browser.

instead you have to fake the API on top of `Object`, but `Object` isn't designed for holding raw binary data and will be really slow/memory inefficient for many common binary use cases (parsing files, writing files, etc).

use `bops` in place of `Buffer` or `Uint8Array` to make your binary JS code fast + portable.

```javascript
var binary = require('bops')

binary.readUInt8(Buffer.from([10]), 0) // === 10

```

in browser, will default to using `Uint8Array` instances.
in node, will default to using `Buffer` instances.

## API

> ## supported encodings
> * utf8
> * hex
> * base64

#### bops.from(str, encoding="utf8") -> buf

given a string (and optional encoding) return a native buffer instance.
also accepts arrays.

#### bops.to(buf, encoding="utf8") -> str

given a native buffer (and optional encoding) return a string.

#### bops.is(buf) -> bool

given a native buffer returns true.  Returns false for other values.

#### bops.subarray(buf, start[, end]) -> buf

return a view onto the original buffer.

#### bops.join([buf, buf, buf]) -> buf

compile several buffers into a single buffer.

#### bops.create(size) -> buf

create a native buffer instance of `size`.

#### bops.copy(source, target, target_start, source_start, source_end)

perform a fast copy from one native buffer to another.

#### readUInt8(buf, at)
#### readInt8(buf, at)
#### readUInt16LE(buf, at)
#### readUInt32LE(buf, at)
#### readInt8(buf, at)
#### readInt16LE(buf, at)
#### readInt32LE(buf, at)
#### readFloatLE(buf, at)
#### readDoubleLE(buf, at)
#### readUInt16BE(buf, at)
#### readUInt32BE(buf, at)
#### readInt16BE(buf, at)
#### readInt32BE(buf, at)
#### readFloatBE(buf, at)
#### readDoubleBE(buf, at)

read a value from a buffer at a given byte offset.

#### writeUInt8(buf, value, at)
#### writeInt8(buf, value, at)
#### writeUInt16LE(buf, value, at)
#### writeUInt32LE(buf, value, at)
#### writeInt8(buf, value, at)
#### writeInt16LE(buf, value, at)
#### writeInt32LE(buf, value, at)
#### writeFloatLE(buf, value, at)
#### writeDoubleLE(buf, value, at)
#### writeUInt16BE(buf, value, at)
#### writeUInt32BE(buf, value, at)
#### writeInt16BE(buf, value, at)
#### writeInt32BE(buf, value, at)
#### writeFloatBE(buf, value, at)
#### writeDoubleBE(buf, value, at)

write a value to a buffer at a given byte offset.

# License

MIT
