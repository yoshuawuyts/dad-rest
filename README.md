# dad-rest
[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][coveralls-image]][coveralls-url]

A restful wrapper around [`request`][request]. Best used as an adapter for
[dad][dad] data stores.

## Installation
```bash
$ npm i --save dad-rest
```

## Overview
```js
var rest = require('dad-rest');
var store = require('dad');
var food = store('food');

food.settings = {baseUrl: 'https://api.myurl.com'};
food.adapters = [rest];
// We can now use all methods in dad,
// and our data will be synchronized to
// the server whenever they're called.
```

## API
__Disclaimer__: You don't need to read through the API to use `dad-rest` as a
`dad` adapter. The api docs are here in case you want to do mad science.

Since `dad-rest` is just a thin wrapper around request, they behave mostly the
same. If you're looking for an overview of everything you can pass in the `opts`
object, you can find it [here][request-docs].

#### .create()
Send a `PUT` request to the server. Takes `{Object} opts` and
`{Function} cb` as arguments.
```js
var opts = {
  url: 'https://api.myurl.com',
  body: {foo: 'bar'}
};

rest.create(opts, function(err, res) {
  if (!error && 200 == res.statusCode) console.log(res.body);
});
```

#### .read()
Send a `GET` request to the server. Takes `{Object} opts` and
`{Function} cb` as arguments.
```js
var opts = {
  url: 'https://api.myurl.com/resource/12345'
};

rest.read(opts, function(err, res) {
  if (!error && 200 == res.statusCode) console.log(res.body);
});
```

#### .update
Send a `PATCH` request to the server. Takes `{Object} opts` and
`{Function} cb` as arguments. To complete
```js
var opts = {
  url: 'https://api.myurl.com',
  body: {foo: 'bar'}
};

rest.update(opts, function(err, res) {
  if (!error && 200 == res.statusCode) console.log(res.body);
});
```

#### .delete
```js
var opts = {
  url: 'https://api.myurl.com',
  body: {foo: 'bar'}
};

rest.delete(opts, function(err, res) {
  if (!error && 200 == res.statusCode) console.log(res.body);
});
```

## License
[MIT](https://tldrlegal.com/license/mit-license) ©
[Yoshua Wuyts](yoshuawuyts.com)

[npm-image]: https://img.shields.io/npm/v/dad-rest.svg?style=flat-square
[npm-url]: https://npmjs.org/package/dad-rest
[travis-image]: https://img.shields.io/travis/yoshuawuyts/dad-rest.svg?style=flat-square
[travis-url]: https://travis-ci.org/yoshuawuyts/dad-rest
[coveralls-image]: https://img.shields.io/coveralls/yoshuawuyts/dad-rest.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/yoshuawuyts/dad-rest?branch=master

[request]: https://github.com/mikeal/request
[dad]: https://github.com/yoshuawuyts/dad
[request-docs]: https://github.com/mikeal/request#requestoptions-callback
