```js
var request = require('request');
var iconv = require('iconv-lite');

var opt = {
    url:u,
    gzip: true
};
request.get(opt)
    .pipe(iconv.decodeStream('utf8'))
    .collect(function (err, body) {
        cb(null, {});
});

request(url, function(err, response, body){
    if (err) {
        console.log(err);
        return cb(err, this);
    }

    var dataList = JSON.parse(body).data;

    cb(null, this);
});
```
