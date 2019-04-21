## javascript 数据类型检测

### JavaScript 数据类型

##### 基本数据类型

* Undefined
* Null
* Boolean
* Number
* String
* Symbol (ES6新增)



##### 引用数据类型

* Object

* Function

* Array

* RegExp

* Date

  ​

---



### 检测数据类型

#### 1.typeof

语法：

```js

typeof A

// or 

typeof(A)

```

可能的返回值：

```js

"number"、"string"、"boolean"、"object"、"function" 和 “undefined”、”symbol"

```



eg：

```js


typeof Symbol(); // symbol 准确

typeof ''; // string 准确

typeof 1; // number 准确

typeof true; //boolean 准确

typeof undefined; //undefined 准确

typeof new Function(); // function 准确

typeof null; // object 不准确

typeof []; // object 不准确

typeof new Date(); // object 不准确

typeof new RegExp(); // object 不准确


```



**总结：**

```js
1.对于基本类型，除 null 以外，均可以返回正确的结果。

2.对于引用类型，除 function 以外，一律返回 object 类型。

3.不能判断null、array等
```



判断某个变量是否存在：

````js


if(!a) { console.log('error’)} // 控制台会报错：Uncaught ReferenceError: a is not defined

if(typeof a === 'undefined') {
console.log('error');
}

````





#### 2.instanceof

`instanceof` 是用来判断A是否为B的实例;

语法：

```js
object instanceof constructor
```

如果 `object` 是 `constructor` 的实例，则返回 true,否则返回 false

参数：

* `object` 要检测的对象
* `constructor` 某个构造函数

`instanceof `运算符用来检测 `constructor.prototype `是否存在于参数 `object` 的原型链;

```
A instanceof B, 在A的原型链中层层查找，是否有原型等于B.prototype，如果一直找到A的原型链的顶端(null;即Object.prototype.__proto__),仍然不等于B.prototype，那么返回false，否则返回true.
```



eg:

```js
[] instanceof Array; // true

{} instanceof Object; // true

new Date() instanceof Date; // true

new RegExp() instanceof RegExp; // true

var arr = [1,2,3,4]
arr instanceof Array; // true
arr instanceof Object; // true

var simpleStr = "This is a simple string"; 
simpleStr instanceof String; // 返回 false, 检查原型链会找到 undefined


1 instanceof Number; // false

new Number(1) instanceof Number; // false
```

**总结：**

```js

1.instanceof可以准确的判断复杂数据类型，但是不能正确判断基本数据类型。

2.只要在当前实例的原型链上，我们用其检测出来的结果都是true。在类的原型继承中，我们最后检测出来的结果未必准确。

3.不能检测 null 和 undefined
(对于特殊的数据类型null和undefined，他们的所属类是Null和Undefined，但是浏览器把这两个类保护起来了，不允许我们在外面访问使用。)

4.不可以判断字面量方式创建

```



#### 3.constructor

`constructor`作用和`instanceof`非常相似。**但`constructor`检测 `Object`与`instanceof`不一样，还可以处理基本数据类型的检测。**

eg:

```js

var arr = [1,2]
arr.constructor === Array; // true
arr.constructor === RegExp; // false
(1).constructor === Number; // true
('aaa').constructor === String; // true


function Fn() {};
Fn.prototype = new Array();
var f = new Fn();
f.constructor // Array
```

**总结：**

```js

1.null 和 undefined 是无效的对象，因此是不会有 constructor 存在的，这两种类型的数据需要通过其他方式来判断。

2.函数的 constructor 是不稳定的，这个主要体现在把类的原型进行重写，在重写的过程中很有可能出现把之前的constructor给覆盖了，这样检测出来的结果就是不准确的


```



#### 4.**Object.prototype.toString.call()**

**Object.prototype.toString.call() 最准确最常用的方式**。

`Object`上的`toString`它的作用是返回当前方法执行的主体（方法中的this）所属类的详细信息即"[object Object]",其中第一个object代表当前实例是对象数据类型的(这个是固定死的)，第二个`Object`代表的是this所属的类是`Object`。



eg:

```js

Object.prototype.toString.call('string');       //"[object String]"
Object.prototype.toString.call(1111);           //"[object Number]"
Object.prototype.toString.call(true);           //"[object Boolean]"
Object.prototype.toString.call(null);           //"[object Null]"
Object.prototype.toString.call(undefined);      //"[object Undefined]"
Object.prototype.toString.call(Symbol('111'));  //"[object Symbol]"
Object.prototype.toString.call({});             //"[object Object]"
Object.prototype.toString.call(new Function()); //"[object Function]"
Object.prototype.toString.call(function(){});   //"[object Function]"
Object.prototype.toString.call([]);             //"[object Array]"
Object.prototype.toString.call(document);       //"[object HTMLDocument]"
Object.prototype.toString.call(window);         //"[object global]"  window是全局对象global的引用

```



---



如何判断是不是数组？

- 使用 Array.isArray 判断，如果返回 true, 说明是数组
- 使用 instanceof Array 判断，如果返回true, 说明是数组
- 使用 Object.prototype.toString.call 判断，如果值是 [object Array], 说明是数组
- 通过 constructor 来判断，如果是数组，那么 `arr.constructor === Array`. (不准确，因为我们可以指定 `obj.constructor = Array`)







----

参考：

[JavaScript的数据类型及其检测](https://github.com/ljianshu/Blog/issues/4)

[MDN-instanceof](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/instanceof)