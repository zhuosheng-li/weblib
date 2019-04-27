# 常用 String api

### 截取类的方法：

##### 1.substring()

语法：

```js
str.substring(indexStart, indexEnd)
```

参数：

* indexStart 需要截取的第一个字符的索引，该字符作为返回的字符串的首字母。

* indexEnd  可选。一个 0 到字符串长度之间的整数，以该数字为索引的字符不包含在截取的字符串内。

返回：

包含给定字符串的指定部分的新字符串。



`substring` 接收两个参数(参数不能为负值)，分别是要截取的开始位置和结束位置，它将返回一个新的字符串，其内容是从start处到end-1处的所有字符。若结束参数(end)省略，则表示从start位置一直截取到最后。(传负值则视为0) ;



##### 2.slice()

语法：

```js
str.slice(start, end);
```

slice()方法与substring()方法非常类似，它传入的两个参数也分别对应着开始位置和结束位置。而区别在于，slice()中的参数可以为负值，如果参数是负数，则该参数规定的是从字符串的尾部开始算起的位置。也就是说，-1 指字符串的最后一个字符。



eg:

```js
 		let str = ‘www.jeffjade.com’;
    console.log(str.slice(0, 3)) // www;
    console.log(str.slice(-3, -1)) // co;
    console.log(str.slice(1, -1)) // www.jeffjade.co;
    console.log(str.slice(2, 1)) // '' (返回空字符串,start须小于end);
    console.log(str.slice(-3, 0)) // '' (返回空字符串,start须小于end);

```



##### 3.substr()

语法：

```js
str.substr(start,length);
```

substr()方法可在字符串中抽取从start下标开始的指定数目的字符。其返回值为一个字符串，包含从 str 的start（包括start所指的字符）处开始的 length 个字符。如果没有指定 length，那么返回的字符串包含从start到str 的结尾的字符。另外如果start为负数，则表示从字符串尾部开始算起。

eg:

```js
 		let str = 'www.jeffjade.com'
    console.log(webStr.substr(1, 3)) // ww.
    console.log(webStr.substr(0)) // www.jeffjade.com
    console.log(webStr.substr(-3, 3)) // com
    console.log(webStr.substr(-1, 5)) // m (目标长度较大的话，以实际截取的长度为准)

```



##### 4.split()

语法：

```js
str.split([separator], [limit]);
```

参数：

* separator 指定用来分割字符串的字符（串）。separator 可以是一个字符串或正则表达式。 如果忽略 separator，则返回整个字符串的数组形式。如果 separator 是一个空字符串，则 str 将会把原字符串中每个字符的数组形式返回。 

* limit 一个整数，限定返回的分割片段数量。split 方法仍然分割每一个匹配的 separator，但是返回的数组只会截取最多 limit 个元素。 

返回：

返回源字符串以分隔符出现位置分隔而成的一个 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array) 

eg：

```js
let str = 'www.jeffjade.com'
str.split('.') // ["www", "jeffjade", "com"]
str.split('.', 1) // ["www"]
str.split('.').join('') // wwwjeffjadecom;

```



##### 5.replace()

方法返回一个由替换值（`replacement`）替换一些或所有匹配的模式（`pattern`）后的新字符串。模式可以是一个字符串或者一个[正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/RegExp)，替换值可以是一个字符串或者一个每次匹配都要调用的回调函数

语法：

```js
str.replace(regexp|substr, newSubStr|function)
```

参数：

- `regexp `(pattern)

  一个[`RegExp`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/RegExp) 对象或者其字面量。该正则所匹配的内容会被第二个参数的返回值替换掉。

- `substr `(pattern)

  一个将被 `newSubStr` 替换的 [`字符串`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String)。其被视为一整个字符串，而不是一个正则表达式。仅第一个匹配项会被替换。

- `newSubStr` (replacement)

  用于替换掉第一个参数在原字符串中的匹配部分的[`字符串`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String)。该字符串中可以内插一些特殊的变量名。参考下面的[使用字符串作为参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace#使用字符串作为参数)。

- `function` (replacement)

  一个用来创建新子字符串的函数，该函数的返回值将替换掉第一个参数匹配到的结果。参考下面的[指定一个函数作为参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace#指定一个函数作为参数)。

返回：

一个部分或全部匹配由替代模式所取代的新的字符串。

eg：

```js
let str = 'jeff@nice&jade'
str.replace(/@[\s\S]*/g, '') // "jeff"
str.replace(/@[\s\S]*&/g, '') // “jeffjade"

```



### 查找类方法：

##### 1.indexOf()

indexOf()用来检索指定的字符串值在字符串中首次出现的位置。

语法：

```js
str.indexOf(searchValue,fromIndex); 
```

参数:

* searchValue 表示要查找的子字符串，

* fromIndex 表示查找的开始位置，省略的话则从开始位置进行检索。 

eg：

```js
let str = 'www.jeffjade.com'
console.log(str.indexOf('.')) // 3
console.log(str.indexOf('.', 1)) // 3
console.log(str.indexOf('.', 5)) // 12
console.log(str.indexOf('.', 12)) // -1

```



##### 2.lastIndexOf()

lastIndexOf()语法与indexOf()类似，它返回的是一个指定的子字符串值最后出现的位置，其检索顺序是从后向前。



eg:

```js
let str = 'www.jeffjade.com'
console.log(str.lastIndexOf('.')) // 12
console.log(str.lastIndexOf('.', 1)) // -1
console.log(str.lastIndexOf('.', 5)) // 3
console.log(str.lastIndexOf('.', 12)) // 12

```



##### 3.includes()

方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回 true 或 false。

语法：

```js
str.includes(searchString[, position])
```

参数：

* searchString 将要搜寻的子字符串。
* position 可选。从当前字符串的哪个索引位置开始搜寻子字符串；默认为0。需要注意的是，includes() 是区分大小写的。

eg:

```js
var str = 'To be, or not to be, that is the question.';

console.log(str.includes('To be'));       // true
console.log(str.includes('question'));    // true
console.log(str.includes('nonexistent')); // false
console.log(str.includes('To be', 1));    // false
console.log(str.includes('TO BE'));       // false
```



##### 4.search()

**search()** 方法执行正则表达式和 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String) 对象之间的一个搜索匹配。

语法：

```js
str.search(regexp)
```

参数：

* regexp 一个[`正则表达式（regular expression）`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/RegExp)对象。如果传入一个非正则表达式对象 `obj`，则会使用 `new RegExp(obj)` 隐式地将其转换为正则表达式对象。

返回值：

如果匹配成功，则 `search()` 返回正则表达式在字符串中首次匹配项的索引;否则，返回 **-1**。

eg:

```js

let str = ‘www.jeffjade.com'
console.log(str.search('w')) // 0
console.log(str.search(/j/g)) // 4
console.log(str.search(/\./g)) // 3


```



##### 5.match()

 **match()** 方法检索返回一个字符串匹配正则表达式的的结果。

语法：

```js
str.match(regexp)
```

参数：

* regexp一个[正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)对象。如果传入一个非正则表达式对象，则会隐式地使用 `new RegExp(obj)` 将其转换为一个 [`RegExp`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/RegExp) 。如果你没有给出任何参数并直接使用match() 方法 ，你将会得到一 个包含空字符串的 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array) ：[""] 。

返回值：

- 如果使用g标志，则将返回与完整正则表达式匹配的所有结果（`Array`），但不会返回捕获组，或者未匹配 `null`。
- 如果未使用g标志，则仅返回第一个完整匹配及其相关的捕获组（`Array`）。 在这种情况下，返回的项目将具有如下所述的其他属性，或者未匹配 `null`。
- 该数组的第0个元素存放的是匹配文本，除此之外，返回的数组还含有两个对象属性index和input，分别表示匹配文本的起始字符索引和stringObject 的引用(即原字符串)。

eg：

```js
let str = '#1a2b3c4d5e#’; 
console.log(str.match('A')); //返回null 
console.log(str.match('b')); //返回["b", index: 4, input: "#1a2b3c4d5e#”] 
console.log(str.match(/b/)); //返回["b", index: 4, input: "#1a2b3c4d5e#”]

```

```js
如果参数传入的是具有全局匹配的正则表达式，那么match()从开始位置进行多次匹配，直到最后。如果没有匹配到结果，则返回null。否则则会返回一个数组，数组中存放所有符合要求的子字符串，并且没有index和input属性。

let str = '#1a2b3c4d5e#’
console.log(str.match(/h/g)) //返回null
console.log(str.match(/\d/g)) //返回["1", "2", "3", "4", "5”]

```



##### 6.charAt()

**charAt()** 方法从一个字符串中返回指定的字符。

语法：

```js
str.charAt(index)
```

参数：

* index 一个介于0 和字符串长度减1之间的整数。 (0~length-1)

  如果没有提供索引，charAt() 将使用0。

eg：

```js
var myStr = "I,love,you,Do,you,love,me”;
var theChar = myStr.charAt(8);// "o",同样从0开始

```



##### 7.charCodeAt()

可返回指定位置的字符的Unicode编码。charCodeAt()方法与charAt()方法类似，都需要传入一个索引值作为参数，区别是前者返回指定位置的字符的编码，而后者返回的是字符子串。



eg:

```js
var myStr = "I,love,you,Do,you,love,me";
var theChar = myStr.charCodeAt(8); //111

```



### 字符串连接

##### 1.concat()

**concat()** 方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。

语法：

```js
str.concat(string2, string3[, ..., stringN])
```

参数：

```
string2...string*N*
```

和原字符串连接的多个字符串

eg：

```js
var hello = "Hello, ";
console.log(hello.concat("Kevin", " have a nice day.")); /* Hello, Kevin have a nice day. */
```



##### 2. + 号连接



性能：

强烈建议使用 [赋值操作符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Assignment_Operators)（+, +=）代替 `concat` 方法。参看 [性能测试（perfomance test）](http://jsperf.com/concat-vs-plus-vs-join)。



### 其他

##### 1.**localeCompare()**

**localeCompare()** 方法返回一个数字来指示一个参考字符串是否在排序顺序前面或之后或与给定字符串相同。



eg：

```js
var myStr = "chicken";
var myStrTwo = "egg";
var first = myStr.localeCompare(myStrTwo); // -1
first = myStr.localeCompare("chicken"); // 0
first = myStr.localeCompare("apple"); // 1

```



##### 大小写：

toLowerCase() & toUpperCase() 

toLowerCase()方法可以把字符串中的大写字母转换为小写，toUpperCase()方法可以把字符串中的小写字母转换为大写。 

stringObject.toLowerCase() stringObject.toUpperCase() 



---

### 常用方法：

##### 1.统计字符串中相同字符出现的次数:

```js
var str = 'aaabbbccc66aabbc6';

var strInfo = str.split('').reduce((p, c) => (p[c]++ || (p[c] = 1), p), {});

console.log(strInfo); // {6: 3, a: 5, b: 5, c: 4}

```

##### 2.字符串去重

```js
1.先实现字符串去重
2.然后对去重后的数组用for循环操作，分别与原始数组中各个值进行比较，如果相等则count++,循环结束将count保存在sum数组中，然后将count重置为0
3.这样一来去重后的数组中的元素在原数组中出现的次数与sum数组中的元素是一一对应的
   */
    var str="aacccbbeeeddd";
    var sum=[];
    var res=[];
    var count=0;
    var arr=str.split("");
    for(var i=0;i<arr.length;i++){
      if(res.indexOf(arr[i])==-1){
        res.push(arr[i]);
      }
    }
    for(var i=0;i<res.length;i++){
      for(var j=0;j<arr.length;j++){
        if(arr[j]==res[i]){
          count++;
        }
      }
      sum.push(count);
      count=0;
    }
    console.log(res);//["a", "c", "b", "e", "d"]
    for(var i=0;i<res.length;i++){
      var str=(sum[i]%2==0)?"偶数":"奇数";
      console.log(res[i]+"出现了"+sum[i]+"次");
      console.log(res[i]+"出现了"+str+"次");
    }

```

##### 3.获取url 上的参数：

```js

//返回的是对象形式的参数
  function getUrlArgObject() {
    var args = new Object();// 创建对象
    var query = location.search.substring(1);// 获取查询串
    var pairs = query.split("&");// 在&处断开
    for (var i = 0; i < pairs.length; i++) {
      var pos = pairs[i].indexOf('=');//查找name=value
      if (pos == -1) {//如果没有找到就跳过
        continue;
      }
      var argname = pairs[i].substring(0, pos);//提取name
      var value = pairs[i].substring(pos + 1);//提取value
      args[argname] = unescape(value);//存为属性
    }
    return args;//返回对象
  }
  //返回的是字符串形式的参数，例如：class_id=3&id=2&
  function getUrlArgStr() {
    var q = location.search.substr(1);
    var qs = q.split('&');
    var argStr = '';
    if (qs) {
      for (var i = 0; i < qs.length; i++) {
        argStr += qs[i].substring(0, qs[i].indexOf('=')) + '=' + qs[i].substring(qs[i].indexOf('=') + 1) + '&';
      }
    }
    return argStr;
  }


```

