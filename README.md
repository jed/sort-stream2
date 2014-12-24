sort-stream2
============

[![Build Status](https://travis-ci.org/jed/sort-stream2.svg)](https://travis-ci.org/jed/sort-stream2)

Array.prototype.sort for streams, a refresh of [@dominictarr](//github.com/dominictarr)'s [sort-stream](//github.com/dominictarr/sort-stream). Use carefully, as sorting requires the whole stream to be buffered.

Example
-------

```javascript
var sort = require("sort-stream2")
var through = require("through2")

var objs = through.obj()
objs.write({id: 3})
objs.write({id: 2})
objs.write({id: 1})
objs.end()

objs
  .pipe(sort(function(a, b){ return a.id - b.id }))
  .on("data", console.log)

// {id: 1}
// {id: 2}
// {id: 3}
```
