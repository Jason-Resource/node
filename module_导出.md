```js

//---- package.js
var test = module.exports = function () {
    this.sayHello = function() { // new出来调用
        console.log('Hello World!');
    };
}

test.nowString = function(){  // 直接调用
    return new Date()
}

test.prototype.proFunTest = function()  // new出来调用
{
    console.log('测试prototype方法的调用');
}

//---- main.js

var test_module = require('./test.js')

var test = new test_module()
test.sayHello()

console.log(test_module.nowString())

test.proFunTest();
```
