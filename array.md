除了 `Object` 之外，`Array` 类型恐怕是 ECMAScript 中最常用的类型了。`Array` 有很多方法，下面一一介绍。
## prototype 属性
允许向数组对象添加属性或方法。
一个新的数组的方法，将数组值转为大写：
```js
Array.prototype.myUcase=function()
{
    for (i=0;i<this.length;i++)
    {
        this[i]=this[i].toUpperCase();
    }
}

var fruits=["Banana","Orange","Apple","Mango"];
fruits.myUcase(); 
// BANANA,ORANGE,APPLE,MANGO
```
## concat()
连接两个或更多的数组，并返回结果。

concat() 方法用于连接两个或多个数组。   
该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。
```js
var hege = ["Cecilie", "Lone"];
var stale = ["Emil", "Tobias", "Linus"];
var kai = "Robin";
var children = hege.concat(stale,kai); 
console.log(children); // ["Cecilie", "Lone", "Emil", "Tobias", "Linus", "Robin"]
```
**语法**
```js
array1.concat(array2,array3,...,arrayX)
```
**参数**
|参数|描述|
|-|-|
|array2, array3, ..., arrayX|必需。该参数可以是具体的值，也可以是数组对象。可以是任意多个。|
**返回值**
|Type|描述|
|-|-|
|`Array` 对象|返回一个新的数组。该数组是通过把所有 `arrayX` 参数添加到 `arrayObject` 中生成的。如果要进行 `concat()` 操作的参数是数组，那么添加的是数组中的元素，而不是数组。|

**场景示例**
一道面试题：传递两个参数m，n，返回长度为m，所有元素都为n的数组，要求不能用循环。利用函数的递归和 concat() 方法可以实现，代码如下：
```js
function fn(m, n) {
  return m ? fn(m - 1, n).concat(n) : [];
}
```

## copyWithin() 
从数组的指定位置拷贝元素到数组的另一个指定位置中。==(es6)== 很少用 

copyWithin() 方法用于从数组的指定位置拷贝元素到数组的另一个指定位置中。==会覆盖原来的值==。
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.copyWithin(2, 0);
console.log(fruits); // ["Banana", "Orange", "Banana", "Orange"]

var fruits = ["Banana", "Orange", "Apple", "Mango", "Kiwi", "Papaya"];
fruits.copyWithin(2, 0, 2);
console.log(fruits); // [Banana,Orange,Banana,Orange,Kiwi,Papaya]
```
**语法**
```js
array.copyWithin(target, start, end)
```
**参数**
|参数|描述|
|-|-|
|target|必需。复制到指定目标索引位置。|
|start|	可选。元素复制的起始位置。|
|end|可选。停止复制的索引位置 (默认为 array.length)。如果为负值，表示倒数。|

## every()
检测数值元素的每个元素是否都符合条件。

`every()` 方法用于检测数组所有元素是否都符合指定条件（通过函数提供）。

`every() `方法使用指定函数检测数组中的所有元素：
- 如果数组中检测到有一个元素不满足，则整个表达式返回 `false` ，且剩余的元素不会再进行检测。
- 如果所有元素都满足条件，则返回 `true` 。  

注意： every() 不会对空数组进行检测。
注意： every() 不会改变原始数组。
```js
var ages = [32, 33, 16, 40];
let isEvery = ages.every((n) => n > 18);

console.log(isEvery) // false 16 < 18
```
**语法**
```js
array.every(function(currentValue,index,arr), thisValue)
```
**参数**
|参数|描述|
|-|-|
|function(currentValue, index,arr)|必须。函数，数组中的每个元素都会执行这个函数|
|thisValue|	可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。
如果省略了 thisValue ，"this" 的值为 "undefined" |

## fill()
使用一个固定值来填充数组。==(es6)== 很少用，毕竟使用场景太少。

`fill()` 方法用于将一个固定值替换数组的元素。
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.fill("Runoob", 2, 4);
console.log(fruits) // ["Banana", "Orange", "Runoob", "Runoob"]
```
**语法**
```js
array.fill(value, start, end)
```
**参数**
|参数|描述|
|-|-|
|value|必需。填充的值。|
|start|可选。开始填充位置。|
|end|可选。停止填充位置 (默认为 array.length)|

## filter() 方法
检测数值元素，并返回符合条件所有元素的数组。

`filter()` 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

**注意**： `filter()` 不会对空数组进行检测。    
**注意**： `filter()` 不会改变原始数组。
```js
var ages = [32, 33, 16, 40];
let ageUp18 = ages.filter(n => n > 18);
console.log(ageUp18) // [32, 33, 40]
```
**语法**   
略   
**参数**   
略

## find() 方法
返回符合传入测试（函数）条件的数组元素。==(es6)==

`find()` 方法返回通过测试（函数内判断）的数组的==第一个元素==的值。

`find()` 方法为数组中的每个元素都调用一次函数执行：
- 当数组中的元素在测试条件时返回 `true` 时, `find()` 返回符合条件的元素，之后的值不会再调用执行函数。
- 如果没有符合条件的元素返回 `undefined`

注意: `find()` 对于空数组，函数是不会执行的。   
注意: `find()` 并没有改变数组的原始值。
```js
var ages = [12, 33, 16, 40];
let ageUp18 = ages.find(n => n > 18);
console.log(ageUp18) // 33
```
**语法**   
略    
**参数**    
略

## findIndex() 方法
返回符合传入测试（函数）条件的数组元素索引 ==(es6)==

`findIndex()` 方法返回传入一个测试条件（函数）符合条件的数组==第一个元素位置==。

`findIndex()` 方法为数组中的每个元素都调用一次函数执行：   
- 当数组中的元素在测试条件时返回 true 时, `findIndex()` 返回符合条件的元素的索引位置，之后的值不会再调用执行函数。
- 如果没有符合条件的元素返回 -1    

注意: `findIndex()` 对于空数组，函数是不会执行的。   
注意: `findIndex()` 并没有改变数组的原始值。
```js
var ages = [3, 10, 18, 20];

let index = ages.findIndex(n => n >= 18)
console.log(index) // 2
```
**语法**   
略    
**参数**    
略

## forEach() 方法
数组每个元素都执行一次回调函数。

forEach() 方法用于调用数组的每个元素，并将元素传递给回调函数。  
注意: forEach() 对于空数组是不会执行回调函数的。
```js
var ages = [3, 10, 18, 20];

ages.forEach(n => {
  n = n + 1
})
console.log(ages) // [4, 11, 19, 21]
```
**语法**   
略   
**参数**    
略

## from() 方法
通过给定的对象中创建一个数组。==es6==   
`from()` 方法用于通过拥有 `length` 属性的对象或可迭代的对象来返回一个数组。
```js
var setObj = new Set(["a", "b", "c"]);
var objArr = Array.from(setObj);
objArr[1] == "b";  // true

var arr = Array.from([1, 2, 3], x => x * 10);
// arr[0] == 10;
// arr[1] == 20;
// arr[2] == 30;
```
**语法**
```js
Array.from(object, mapFunction, thisValue)
```
**参数**
|参数|描述|
|-|-|
|object|必需，要转换为数组的对象。 可以是任何类型|
|mapFunction|可选，数组中每个元素要调用的函数。|
|thisValue|可选，映射函数(mapFunction)中的 this 对象。|

## includes() 方法
判断一个数组是否包含一个指定的值。 ==es6==   

`includes()` 方法用来判断一个数组是否包含一个指定的值，如果是返回 `true`，否则 `false`。
```js
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```
**语法**
```js
arr.includes(searchElement, fromIndex)
```
**参数**
|参数|描述|
|-|-|
|searchElement|必须。需要查找的元素值。|
|fromIndex|可选。从该索引处开始查找 searchElement。如果为负值，则按升序从 array.length + fromIndex 的索引开始搜索。默认为 0。|

如果 `fromIndex` 大于等于数组长度 ，则返回 `false` 。该数组不会被搜索。
如果 `fromIndex` 为负值，计算出的索引将作为开始搜索 `searchElement` 的位置。如果计算出的索引小于 0，则整个数组都会被搜索。

## indexOf()
搜索数组中的元素，并返回它所在的位置。

`indexOf()` 方法可返回数组中某个指定的元素位置。

该方法将从头到尾地检索数组，看它是否含有对应的元素。开始检索的位置在数组 `start` 处或数组的开头（没有指定 `start` 参数时）。如果找到一个 `item`，则返回 `item` 的第一次出现的位置。开始位置的索引为 0。

如果在数组中没找到指定元素则返回 -1。

**提示**：如果你想查找字符串最后出现的位置，请使用 lastIndexOf() 方法。
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple"); // 2

var fruits=["Banana","Orange","Apple","Mango","Banana","Orange","Apple"];
var a = fruits.indexOf("Apple",4);  // 6
```
**语法**
```js
array.indexOf(item,start)
```
**参数**
|参数|描述|
|-|-|
|item|必须。查找的元素。|
|start|可选的整数参数。规定在数组中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的首字符开始检索。|

## isArray()
`isArray()` 方法用于判断一个对象是否为数组，比较靠实得检查方法。   
如果对象是数组返回 true，否则返回 false。
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var isarray = Array.isArray(fruits); // true
```
**语法**   
略   
**参数**    
略

## join()
`join()` 方法用于把数组中的所有元素转换一个字符串。   
元素是通过指定的分隔符进行分隔的。
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var energy = fruits.join();
```
**语法**   
略   
**参数**    
略

## keys()
## lastIndexOf() 
