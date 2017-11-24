```js

process.on('uncaughtException', function (err) {
    console.error("uncaughtException error:", err);
});



var workerProcess = child_process.exec('node support.js '+i, function(){});

var workerProcess = child_process.fork("support.js", [i]);  
  
var workerProcess = child_process.spawn('node', ['support.js', i]);


//---
main.js:
console.log(process.argv);

node main.js
输出： [ '/usr/local/bin/node', '/vagrant/www/test/simple/main.js' ]
  
```
