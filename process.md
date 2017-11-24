```js

process.on('uncaughtException', function (err) {
    console.error("uncaughtException error:", err);
});



var workerProcess = child_process.exec('node support.js '+i, function(){});

var workerProcess = child_process.fork("support.js", [i]);  
  
var workerProcess = child_process.spawn('node', ['support.js', i]);




```
