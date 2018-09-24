# process global object
It provides a bridge between node application and running environment. Following are few good functions.
## process.versions
It reads version of current node and its dependencies.
```
 node -p process.versions

{ http_parser: '2.8.0',
  node: '9.11.1',
  v8: '6.2.414.46-node.23',
  uv: '1.19.2',
  zlib: '1.2.11',
  ares: '1.13.0',
  modules: '59',
  nghttp2: '1.29.0',
  napi: '3',
  openssl: '1.0.2o',
  icu: '61.1',
  unicode: '10.0',
  cldr: '33.0',
  tz: '2018c' }
```

## process.env
It reads environment variable. It exposes cpy of user's environment. If you modify `process.env` then you are not modifying actual environment.
This is helpful to keep the local modified version dedicated for node.js process.

# process and event emitter
`process` object is an instance of event emitter. It means, we can emit events on `process` and listen for certain events on `process`.

## process.on('exit') event
If node.js process is getting exit, we can not control to stop it. However we can log it or send some email/alert to let someone to do something.
```
process.on('exit', (code) =>{
// Do final synchronous operation before the node process terminates
});
```
Note: It only supports synchronous operations. We cannot use event loop here.

## process.on('uncaughtException') event
`uncaughtException` event is emitted whenever javasript exception is not caught and it bubbled all the way to event loop. In this case, node will simply print stack trace and exit.
If you handle this event then node will not exit. In general, we should avoid to listen for this event.
If needed, we can listen for this event but make sure we exit the process.
```
process.on('uncaughtException', (error) =>{
// Do any cleanup and exit
// Force exit
process.exit(1);

});




