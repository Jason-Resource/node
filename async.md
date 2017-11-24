```js
async.setImmediate(function(){
    setTimeout(function(){
        callback();
    }, 10*1000);
});

// *************************************************************************************

// 串行且无关联 async.series

async.series({
    flag1:function(done){ //flag1 是一个流程标识,用户自定义
        //逻辑处理
        done(null,返回结果)// 第一个参数是异常错误,第二个参数的返回结果
    },
    flag2:function(done){
        //逻辑处理
        done('error info',null) //如果返回错误信息,
                                //下面的流程控制将会被中断,直接跳到最后结果函数
    },
},function(error,result){
    //最后结果
    //result是返回结果总集,包含了所有的流程控制 ,
    //result.flag1 可以获取标识1中处理的结果
});

// *************************************************************************************

// 并行且无关联 async.parallel

var async = require('async');
console.time('parallel');
async.parallel({
    one: function (done) {
        //处理逻辑
        done(null, 'one');
    },
    two: function (done) {
        //处理逻辑
        done(null, 'tow');
    },
    three: function (done) {
        //处理逻辑
        done(null, 'three');
    },
    four: function (done) {
        //处理逻辑
        done(null, 'four');
    }
}, function (error, result) {
    console.log('one:', result.one);
    console.log('two:', result.two);
    console.log('three:', result.three);
    console.log('four:', result.four);
    console.timeEnd('parallel');
})

// *************************************************************************************

// 串行且有关联 async.waterfall

console.time('waterfall');
async.waterfall([
    function (done) {

        done(null, 'one');
    },
    function (onearg, done) {

        done(null, onearg + '| two');
    },
    function (twoarg, done) {

        done(null, twoarg + '| three');
    },
    function (threearg, done) {

        done(null, threearg + '| four');
    }
], function (error, result) {
    console.log(result);
    console.timeEnd('waterfall');
})

// *************************************************************************************

// while循环 async.whilst

var i = 0;
async.whilst(
    function () {
        return i<100;
    },
    function (whileCb) {
        i++;
        console.log(i);
        whileCb();
    },
    function (err) {
        if (err) {
            console.log(err)
        }
    }
);
```
