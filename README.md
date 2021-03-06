# Model.js [![Build Status](https://travis-ci.org/shannonmoeller/model.js.png)](https://travis-ci.org/shannonmoeller/model.js)

> A basic JavaScript model.

## Installation

Server-side ([Node.js](http://nodejs.org)):

    $ npm install shannonmoeller/model.js

Client-side ([component(1)](https://github.com/component)):

    $ component install shannonmoeller/model.js

## API

### `Model(object)`

Create a new model which wraps around `object`. Context is enforced. Calling `new Model`, `Model.apply`, and `Model.call` will not affect the value of `this` in the constructor.

```js
var Model = require('model');
var foo = Model({ foo: 'bar' });
```

### `.get(key):Any` <br /> `.get(array):Object`

Gets one or more values.

```js
var foo = Model({ a: 1, b: 2 });

foo.get('a');             // 1
foo.get('b');             // 2
foo.get('c');             // undefined
foo.get(['a', 'b', 'c']); // { a: 1, b: 2, c: undefined }
```

### `.set(key, value):this` <br /> `.set(object):this`

Sets one or more values.

```js
var foo = Model();

foo.toJSON(); // { }

foo.set('a', 1);
foo.toJSON(); // { a: 1 }

foo.set('b', 2);
foo.toJSON(); // { a: 1, b: 2 }

foo.set({ b: 3, c: 4 });
foo.toJSON(); // { a: 1, b: 3, c: 4 }

```

### `.toJSON()`

Returns the current state of the internal data as a plain object.

```js
var foo = Model({ a: 1, b: 2, c: 3 });

foo.toJSON(); // { a: 1, b: 2, c: 3 }
```

## Testing

```sh
$ npm test
```

[![browser support](http://ci.testling.com/shannonmoeller/model.js.png)](http://ci.testling.com/shannonmoeller/model.js)

## License

MIT
