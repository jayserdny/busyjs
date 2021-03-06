![](http://img.badgesize.io/busyorg/busy.js/master/dist/busy.min.js.svg)

# Busy.js

A lightweight JavaScript library for Busy

### Install
```
npm install busyjs --save
```

### Usage
```js
var busy = require('busyjs');

// Init WebSocket client
var client = new busy.Client('wss://gtg.steem.house:8090');

// Get accounts
client.call('get_accounts', ['fabien'], function(err, result) {
  console.log(err, result);
});
```
[See more examples](/test/test.js)

### Promises

You can also use Busy.js with promises by promisifying busy with
[bluebird](https://github.com/petkaantonov/bluebird) as in:

```js
var busy = require('busyjs');
bluebird.promisifyAll(busy.Client.prototype);
```

It'll add a *Async* to all busy functions (e.g. return client.callAsync().then())
```js
// So instead of writing client.request('get_accounts', ['fabien'], cb); you have to write:
return client.callAsync('get_accounts', ['fabien']).then(function(result) {
  console.log(result); // => [{ id: 26921, name: 'fabien' ...]
});
```

## License

[MIT](LICENSE).
