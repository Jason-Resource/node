- console.log(require);
```js
{ [Function: require]
  resolve: [Function: resolve],
  main:
   Module {
     id: '.',
     exports: {},
     parent: null,
     filename: '/home/node/test/main.js',
     loaded: false,
     children: [],
     paths:
      [ '/home/node/test/node_modules',
        '/home/node/node_modules',
        '/home/node_modules',
        '/node_modules' ] },
  extensions: { '.js': [Function], '.json': [Function], '.node': [Function] },
  cache:
   { '/home/node/test/main.js':
      Module {
        id: '.',
        exports: {},
        parent: null,
        filename: '/home/node/test/main.js',
        loaded: false,
        children: [],
        paths: [Array] } } }

```

- console.log(module)
```js
Module {
  id: '.',
  exports: {},
  parent: null,
  filename: '/home/node/test/main.js',
  loaded: false,
  children: [],
  paths:
   [ '/home/node/test/node_modules',
     '/home/node/node_modules',
     '/home/node_modules',
     '/node_modules' ] }

```
