```js
/*
http://nodejs.cn/api/modules.html#modules_exports_shortcut

exports 是一个对于 module.exports 的更简短的引用形式 (exports 是对 module.exports 的引用)
module.exports 用于指定一个模块所导出的内容，即可以通过 require() 访问的内容。
注意，就像任何变量，如果一个新的值被赋值给 exports，它就不再绑定到 module.exports
每一个node.js执行文件，都自动创建一个module对象，同时，module对象会创建一个叫exports的属性，初始化的值是 {}

module.exports 被改变的时候，exports不会被改变，而模块导出的时候，真正导出的执行是module.exports，而不是exports
*/


/********************************************************************************/

//-----
module.exports = {foo:'bar'};
exports.a = {};
// 导出{ foo: 'bar' }

//-----
exports.a = {};
module.exports = {foo:'bar'};
// 导出{ foo: 'bar' }

//-----
exports = { foo: 'bar' }
// 导出{} ;;  宣相当于执行 module.exports ；默认 module.exports 就是空对象

//-----
exports.a = {};
// 导出 { a: {} }

/********************************************************************************/
// hello.js
exports.world = function() {        // 导出一个world对象 ： { world: [Function] }
    console.log('Hello World');
};

// main.js
var hello = require('./hello');
hello.world();

/********************************************************************************/
// common.js
module.exports.user = {'name':'meinvbingyue'};   // 推荐使用
或 
exports.user = {'name':'meinvbingyue'};
 
// main.js
var common = require('./common.js');
console.log(common.user.name);


/********************************************************************************/
/*
javascript里面有一句话，函数即对象，Hello 是对象，module.export = Hello, 即相当于导出整个 Hello 对象。
外面模块调用它的时候，能够调用Hello的所有方法。不过需要注意，只有是Hello的静态方法的时候，才能够被调用
，prototype创建的方法，则属于Hello的私有方法。（就是说要new出来后才能调用）
*/
// hello.js
function Hello() {
    var name;
    this.setName = function(thyName) {
        name = thyName;
    };
    this.sayHello = function() {
        console.log('Hello ' + name);
    };
};
module.exports = Hello;

// main.js
var Hello = require('./hello');
hello = new Hello();
hello.setName('BYVoid');
hello.sayHello();

/********************************************************************************/

// test.js
function View(){

}

View.prototype.test = function(){
    console.log('test')
}

View.test1 = function(){
    console.log('test1')
}

module.exports = View  // 导出View对象

// main.js
var x = require('./test');

console.log(x) //{ [Function: View] test1: [Function] }
console.log(x.test) //undefined
console.log(x.test1) //[Function]
x.test1() //test1


/********************************************************************************/

// test.js
var test = module.exports = function () {
    this.sayHello = function() {
        console.log('Hello World!');
    };
}

test.nowString = function(){
    return new Date()
}

test.prototype.proFunTest = function()
{
    console.log('测试prototype方法的调用');
}

// main.js
var test_module = require('./test.js')
var test = new test_module()
test.sayHello()

test.proFunTest();

var cur_time = test_module.nowString()
console.log(cur_time)

```
