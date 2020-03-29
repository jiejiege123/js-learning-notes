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
从数组的指定位置拷贝元素到数组的另一个指定位置中。**(es6)** 很少用 

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

## 