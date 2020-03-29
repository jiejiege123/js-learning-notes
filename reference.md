# 引用类型
对象是某个特定引用类型的**实例**。新对象是使用 `new` 操作符后跟一个**构造函数**来创建的。构造函数本身就是一个函数，只不过该函数是出于创建新对象的目的而定义的。
```js
var person = new Object();
```
这行代码创建了 `Object` 引用类型的一个新实例，然后把该实例保存在了变量 `person` 中。使用的构造函数是 `Object`，它只为新对象定义了默认的属性和方法ECMAScript提供了很多原生引用类型（例如 `Object`），以便开发人员用以实现常见的计算任务。

## Object类型
如果要通过变量访问属性，可以使用 `[]`。

## Array类型
数组的每一项可以保存任何类型的数据。
```js
var colors = new Array(20); // 创建一个包含 20 项的数组
var colors = new Array("red", "blue", "green"); // 创建一个包含 3项字符串的数组
var colors = ["red", "blue", "green"]; // 创建一个包含 3 个字符串的数组
```
`Array` 的 `length` 不是只读的，可以直接操作，没有具体值的下标的值是`undefined`。
`Array` 对象其他方法参见：：[JavaScript Array 对象](https://zemengzhou.top/welcome/detail?id=14)