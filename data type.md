# 数据类型
## 基本类型和引用类型
1.ECMAScript 中有 5 种简单数据类型（也称为基本数据类型）：`Undefined`、`Null`、`Boolean`、`Number`
和 `String`。还有 1种复杂数据类型——`Object`  
2.使用 `typeof` 操作符，出现如下结果
```
 "undefined"——如果这个值未定义；
 "boolean"——如果这个值是布尔值；
 "string"——如果这个值是字符串；
 "number"——如果这个值是数值；
 "object"——如果这个值是对象或 null；
 "function"——如果这个值是函数。
```
> 注意：typeof是一个操作符,不是函数  

比较特殊的是 `null` 会返回 **`object`** 。函数会返回 **`function`**

## Underfined
意思就是声明了，但是没赋值

## Null
就是没有的，连声明都没有的，比较特殊的就是 `typeof null` 会返回 `object`

## Boolean

`true` 和 `false`就这么简单  
使用 `Boolean()`函数或者在if判断中直接写入，会返回布尔值。 

比较重要的是布尔转换  

1.转换为true的值的有

* 任何非空字符串
* 任何非0数字
* 任何object
  
2.转换为false的值的有
* 空字符串" "
* 0
* null
* undefined

## Number
整数和浮点数不提   
`NAN` 比较特殊
首先 `NAN` 是数值
```js
typeof NAN // "number"
```
使用 `isNAN` 判断是否‘不是数值’，`isNaN()` 在接收到一个值之后，会尝试将这个值转换为数值。某些不是数值的值会直接转换为数值，而任何不能被转换为数值的值都会导致这个函数返回  `true`
```js
isNaN(NaN)         //true 
isNaN(10)         //false（10 是一个数值） 
isNaN("10")        //false（可以被转换成数值 10） 
isNaN("blue")       //true（不能转换成数值） 
isNaN(true))        //false（true可以被转换成数值 1）
```
### 数值转换
有3个函数可以把非数值转换为数值：`Number()`、`parseInt()`、`parseFloat()` 。转型函数 `Number()` 可以用于任何数据类型，而另外两个函数专门用于转换字符串。
`Number()` 用得比较少， 主要还是用后面两个。后面两个得区别主要在于小数得保留。
```js
Number("Hello world!"); //NaN 
Number(""); //0 
Number("000011"); //11 
Number(true); //1
```
`parseInt()` 会把所有不能转换成数值的全部转化成 `NaN`
```js
parseInt('') // NaN
parseInt('asfsfd') // NaN
parseInt(null) // NaN
parseInt(true) // NaN
```

## String 类型
1. 字符字面量
```
\n 换行
\t 制表
\b 空格
\r 回车
\f 进纸
\\ 斜杠
\' 单引号（'），在用单引号表示的字符串中使用。例如：'He said, \'hey.\''
\" 双引号（"），在用双引号表示的字符串中使用。例如："He said, \"hey.\""
\xnn 以十六进制代码nn表示的一个字符（其中n为0～F）。例如，\x41表示"A"
\unnnn 以十六进制代码nnnn表示的一个Unicode字符（其中n为0～F）。例如，\u03a3表示希腊字符Σ
```
1. 转换为字符串
- `toString()`
  除了 `null` 和 `undefined` ，其他数据类型都有 `toString()` 方法，也都会直接转换成字符串。可以带参数，表示转换成什么进制类型，默认是10进制。
  ```js
  true.toString() // 'true'
  null.toString() // Uncaught TypeError: Cannot read property 'toString' of null at
  ```
- 转型函数 `String()`
  当不知道是否会有 `null` 和 `undefined` 被转换时，就要用 `String()`
  ```js
  String(10) // "10" 
  String(true) // "true" 
  String(null) // "null" 
  String(undefined) // "undefined"
  ```
- 简单方法   
  把它与一个字符串（""）加在一起 ` + ''`

## Object 类型
`object` 是很重要的一个数据类型了。 `Object` 是所有对象的基础，每个实例都有下列的属性和方法。
- `constructor`：保存着用于创建当前对象的函数。对于前面的例子而言，构造函数（constructor）
就是 Object()。
- `hasOwnProperty(propertyName)`：用于检查给定的属性在当前对象实例中（而不是在实例
的原型中）是否存在。其中，作为参数的属性名（propertyName）必须以字符串形式指定（例
如：o.hasOwnProperty("name")）。
- `isPrototypeOf(object)`：用于检查传入的对象是否是传入对象的原型。
- `propertyIsEnumerable(propertyName)`：用于检查给定的属性是否能够使用 for-in 语句，作为参数的属性名必须以字符
串形式指定。
- `toLocaleString()`：返回对象的字符串表示，该字符串与执行环境的地区对应。
- `toString()`：返回对象的字符串表示。
- `valueOf()`：返回对象的字符串、数值或布尔值表示。通常与 toString()方法的返回值
相同。

# 操作符
## 一元操作符
1. 前置操作符
```js
var age = 29; 
++age; // 30
// 等效于
var age = 29; 
age = age + 1; // 30
```
**执行前置递增和递减操作时，变量的值都是在语句被求值以前改变的, 而后置递增和递减操作是在包含它们的语句被求值之后才执行的**，例子：
```js
// 前置
var num1 = 2; 
var num2 = 20; 
var num3 = --num1 + num2; // 等于 21  等效于 num1 = num1 - 1; var num3 = num1 + num2
var num4 = num1 + num2; // 等于 21

// 后置
var num1 = 2; 
var num2 = 20; 
var num3 = num1-- + num2; // 等于 22  等效于 var num3 = num1 + num2; num1 = num1 - 1; 
var num4 = num1 + num2; // 等于 21
```
`num3` 的值不同，前置是先执行了 `--num1`，再 `+ num2`，而后置先执行 `+ num2`，并赋值给 `num3`，然后再执行 `num1--` 
## 其他操作符
略

# 语句
## if语句
`if (condition) statement1 else statement2`   
先自动调用 Boolean()转换函数将 `condition` 的结果转换为一个布尔值。
## do-while语句
```js
do { 
 statement 
} while (expression);

// 示例
var i = 0; 
do { 
 i += 2; 
} while (i < 10); 
alert(i);
```
`do-while` 语句是一种后测试循环语句，意思就是要先执行一次 `do` 中的语句，然后判断 `while` 中的 `expression` 条件， 如果条件满足，就再执行一次 `do` 中的语句，直到 `expression` 条件不满足。

## while语句
```js
while(expression) statement

// 示例
var i = 0; 
while (i < 10) {
  i += 2; // i = i + 2
}
```
`while` 语句属于前测试循环语句，也就是说，在循环体内的代码被执行之前，就会对出口条件求值。

## for语句
`for` 语句也是一种前测试循环语句，但它具有在执行循环之前初始化变量和定义循环后要执行的代码的能力。
```js
for (initialization; expression; post-loop-expression) statement
// for (定义变量; 执行条件; 循环完成后执行的语句){执行语句}

// 示例
var count = 10; 
for (var i = 0; i < count; i++){ 
 console.log(i); 
}
```
实际上 `for` 语句就像是 `while` 语句的代码简写： 
```js
var count = 10; 
var i = 0; // 定义变量
while (i < count){ // 执行条件
 console.log(i); // 执行语句
 i++; // 循环完成后执行的语句
}

```
值得注意的是在es5中，没有块级作用域，所以 
```js
for (var i = 0; i < count; i++){ 
  console.log(i) // 0 1 2 3 ...
}
console.log(i) // 10
```
中的 `i` 实际是个全局变量，有时候这个样写会有麻烦。但是es6中，有了块级作用域，这个时候的变量定义使用 `let` 就可以解决问题了。
```js
var count = 10; 
var i = 0; 
for (let i = 0; i < count; i++){ 
console.log(i); // 0 1 2 3 ...
}
console.log(i); // 0
```

## for-in语句
`for-in` 用于遍历对象的属性
```js
for (property in expression) statement
for (var propName in window) { 
 document.write(propName); 
}
```
如果对象是 `null` 或者 `undefined` 则不会执行循环体。

## break和continue语句
`break` 会立即退出循环体，而 `continue` 只是退出当前循环，而循环体会继续执行。
```js
var num = 0; 
for (var i=1; i < 10; i++) { 
  if (i % 5 == 0) { 
    break; 
  } 
  num++; 
} 
console.log(num); //4

var num = 0; 
for (var i=1; i < 10; i++) { 
  if (i % 5 == 0) { 
    continue; 
  } 
  num++; 
} 
console.log(num); //8
```
## label语句
略
## with语句
with 语句的作用是将代码的作用域设置到一个特定的对象中。with 语句的语法如下：
```js
with (expression) statement;
```
定义 with 语句的目的主要是为了简化多次编写同一个对象的工作，如:
```js
var qs = location.search.substring(1); 
var hostName = location.hostname; 
var url = location.href;

with(location){ 
 var qs = search.substring(1); 
 var hostName = hostname; 
 var url = href; 
}

```
`with` 语句的代码块内部，每个变量首先被认为是一个局部变量，而如果在局部环境中找不到该变量的定义，就会查询 `location` 对象中是否有同名的属性。如果发现了同名属性，则以 `location` 对象属性的值作为变量的值。
严格模式下不允许使用 with 语句，否则将视为语法错误。
> 由于大量使用 with 语句会导致性能下降，同时也会给调试代码造成困难，因此
在开发大型应用程序时，不建议使用 with 语句。
## switch语句
没什么好讲的，值得注意的是 如果 `case` 不写 `break`，就不会跳出，会继续向下执行 `case`。

# 函数
函数对任何语言来说都是一个核心的概念。
对于一个函数，先声明，然后执行就可。   
执行函数，会执行函数体内的语句。如果有 `return`，那么执行了 `return` 后，函数将立即退出，并返回相应的值或者 `undefined`，后面的语句不会被执行
函数申明：
```js
function functionName(arg0, arg1,...,argN) { 
 statements 
}

// 示例
function sayHi(name, message) { 
 console.log("Hello " + name + "," + message); 
}
```
执行函数：函数名（）
```js
sayHi("Nicholas", "how are you today?");
```
## 参数
js函数的参数比较开放，可以随便传，哪怕定义的时候，只定义了两个参数，在调用的时也未必一定要传递两个参数。可以传递一个、三个甚至不传递参数。  
在函数体内可以通过 `arguments` 对象来访问这个参数数组，从而获取传递给函数的每一个参数。
`arguments` 类似数值，但不是 `Array` 实例。在函数体内，可以直接使用 `arguments`：
```js
function howManyArgs() { 
 console.log(arguments.length, arguments[0], arguments[1]); 
} 
howManyArgs("string", 45); //2 "string" 45
howManyArgs(); //0 undefined undefined 
howManyArgs(12); //1 12 undefined


function howManyArgs(a, b) { 
 console.log(arguments.length, arguments[0], arguments[1], a); 
} 
howManyArgs("string", 45); //2 "string" 45 "string"
howManyArgs(); //0 undefined undefined undefined
howManyArgs(12); //1 12 undefined 12
```
`arguments` 的值和命名参数的值是保持同步的。但是，它们的内存空间是独立的。严格模式下，`arguments` 不能被重写的，但是参数值可以改变就很好的说明了这点。
```js
var a = 1
function howManyArgs(b) { 
	console.log(b, arguments[0]) // 1 1
	b = 13
	console.log(b, arguments[0]) // 13 13(严格模式下：1)
} 
howManyArgs(a)
console.log(a) // 1
```
由上示例，我们还可以验证，js中的参数传递的都是值（有各自的内存空间），不可能通过引用传递参数。
那么问题就来了，如果 `a` 是对象呢？
```js
"use strict"
var a = {c: 1, d: 11}
function howManyArgs(b) { 
	console.log(b, arguments[0]) // { c: 1, d: 11 } { c: 1, d: 11 }
	b.c = 13
	console.log(b, arguments[0]) // { c: 13, d: 11 } { c: 13, d: 11 }
} 
howManyArgs(a)
console.log(a) // { c: 13, d: 11 }
```
为什么 `a` 的值变化了呢？而且`arguments[0]`也发生了变化， 接下来再看：
```js
"use strict"
var a = {c: 1, d: 11}
function howManyArgs(b) { 
	console.log(b, arguments[0]) // { c: 1, d: 11 } { c: 1, d: 11 }
	b = 13
	console.log(b, arguments[0]) // 13 { c: 1, d: 11 }
} 
howManyArgs(a)
console.log(a) // { c: 1, d: 11 }
```
当参数是引用类型时，传递的是指向地址，而不是对象本身。对函数内参数的对象的改变，并没有改变指向，所以 `a` 和 `arguments` 的值跟着变了，但是如果指向改变了（`b = 13`），对原来的对象并没有影响。

## 重载
没有重载。简单来说，就是相同的函数名，只认最后一个，前面的写翻天了，也不执行。