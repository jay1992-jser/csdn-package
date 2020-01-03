# Object.prototype.toString方法

在 JavaScript 里,常见的数据类型 “number”，”string”，”undefined”，”boolean”，”object”，“function”，

“symbol” 七种，其中：判断数据类型，要判断数据的具体类型，可调用：Object.prototype.toString.call()；

```
console.log(Object.prototype.toString.call(123));    //[object Number]
console.log(Object.prototype.toString.call('123'));    //[object String]
console.log(Object.prototype.toString.call(undefined));    //[object Undefined]
console.log(Object.prototype.toString.call(true));    //[object Boolean]
console.log(Object.prototype.toString.call({}));    //[object Object]
console.log(Object.prototype.toString.call([]));    //[object Array]
console.log(Object.prototype.toString.call(function(){}));    //[object Function]
console.log(Object.prototype.toString.call(null));    //[[object Null]]
```

详见：（<https://www.cnblogs.com/bq-med/p/8796836.html>）