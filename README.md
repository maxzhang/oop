javascript-oop
==============
> JavaScript面向对象编程，类声明、继承……

声明类
------
```js
var MyCls = Klass.define({
    constructor: function(name) { // 构造函数
        this.name = name;
    },
    method1: function() {
        console.log('hello ' + this.name);
    },
    method2: function(x, y) {
        console.log(x + y);
    },
    method3: function(x, y) {
        console.log(x * y);
    }
});

new MyCls('max').method1(); // print 'hello world'
```

继承类
------
```js
var SubCls1 = Klass.define(MyCls, {
    method1: function() { // 重写父类方法
        console.log('hi ' + this.name);
    },
    method4: function() { // 新方法
    }
});

new SubCls1('max').method1(); // print 'hi world'
```

调用父类方法
------------
```js
var SubCls2 = Klass.define(MyCls, {
    method1: function() {
        this.callParent(); // 调用父类方法
        console.log('hi ' + this.name);
    },
    method2: function(x, y) {
        this.callParent([++x, y]); // 传入参数集合
    },
    method2: function() {
        this.callParent(arguments); // 也可以直接传入arguments
    }
});

var s2 = new SubCls2('max');
s2.method1(); // print 'hi world'
s2.method2(1, 1); // print 3, not 2
s2.method3(1, 1); // print 1
```

声明静态属性和方法
-----------------
```js
var SubCls3 = Klass.define(MyCls, {
    statics: { // 静态属性和方法
        prop1: 'static property',
        fn1: function() {
            console.log('this is a ' + SubCls3.prop1);
        }
    }
});

SubCls3.fn1();
```

### 安装Node模块

```shell
npm install javascript-oop --save-dev
```

在Node中调用：
```js
var Klass = require('javascript-oop');
var MyCls = Klass.define({
    // ...
});
```
