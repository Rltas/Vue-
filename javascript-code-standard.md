# javascript代码风格

## 缩进
* 缩进使用4个空格（sublime等IDE可配置1个tab等于几个空格）。不要混用空格和tab。

```javascript
let obj = {
    name: 'str'
}
```
* 方法的参数列表，逗号前不需空格，逗号后需空一格。

```javascript
function thisIsDemo(a, b) {

}
```
* "{"，"}" 前后需空一格;":"，","后面空一格，前面不需空格;if，for，方法名与"("之间不要空格;操作符(+，-等)与操作数间需要有一个空格。

```javascript
function thisIsDemo(a, b) {
    return a + b;
}
if() {

} else {

}
```
## 命名
* 文件命名,使用分割线。

```javascript
child_process.js
string_decoder.js
_linklist.js
```
* 变量命名，使用小驼峰式命名法。(尽量使用es6的let,避免使用var,以免造成不必要的全局污染。使用单引号` '' `包裹字符串。)。

```javascript
let thisIsDemo = 'str';
```
* 常量命名,全部大写，单词间用_分隔。

```javascript
const LOCALHOST = "http://localhost";
const REMORT_PORT = "8080";
```
* 方法命名，使用小驼峰式命名法。

```js
function thisIsDemo(params) {
  
}
```
* 类命名,使用大驼峰式命名法。

```js
class ThisISDemo {
    constructor(params) {
        
    }
}
```

## 风格
* 最后再声明未赋值的变量。当你需要引用前面的变量赋值时这将变的很有用。

```js
let items = getItems();
let goSportsTeam = true;
let dragonball;
let length;
let i;
```
* 使用大括号包裹所有的多行代码块。
* 把 else 放在 if 代码块关闭括号的同一行。
* 自增/自减运算符不需要隔开。
* 使用三元运算符时，保证他们在同一行或者`?`,`:`单独一行不分开。

```js
let location = env.development ? 'localhost' : 'www.api.com'
let location = env.development
    ? 'localhost'
    : 'www.api.com';
```
* 去除额外的尾部逗号。

```js

let obj = {
    firstName: 'Li',
    lastName: 'San',
    fullName: 'Li San'
}
let arr = ['a', 'b', 'c'];
```
* 在每一个语句后使用分号。（避免浏览器解析意外错误）

```js
a = b
(function(){

})();
会解析成 a = b(function() {})();
```
* 为了便于阅读每行字符建议小于数 80 个。如果一个 JavaScript 语句超过了 80 个字符，建议在 运算符或者逗号后换行。
* 
## 函数
* 函数体避免过大，可拆分成几个职责清晰的单一函数(单一职责原则)。

```js
//bad
function render() {
    //数据打包逻辑
    ....
    //业务处理逻辑
}

//good
function packageData() {
    //数据打包逻辑
}
function businessLogic() {
    //业务逻辑
}
function render() {
    packageData();
    businessLogic();
}
``` 
* 函数参数避免过多，当参数大于3个或参数中有`boolean`类型的值时，全部参数或可选参数使用配置对象代替。

```js
//bad 
function showDialog(el, data, target, className, isShowClose) {

}

//goods
function showDialog(option) {

}

showDialog({
    el: '#el',
    data: 'data',
    target: '#target',
    className: 'className',
    isShowClose: true
});
```
* 立即执行函数使用()来包裹，避免返回不必要的值。
* 如果属性是布尔值，使用 `is` 或 `has` 作为函数名的前缀。
```js
if(hasAge()) {

}
```
* 先执行false条件

```js
function thisIsDemo() {
    if(!false) return;
    ...
    ...
    //大量处理代码
}
```

## 循环
* 迭代数组对象时，缓存数组的长度大小。
```js
for(let i = 0, len = arr.length; i < len; i++) {

}
```
* 在聚合对象中查找单个对象时，及时退出循环。

```js
for(let i = 0, len = arr.length; i < len; i++) {
    if(arr[i].id) {
        ...
        break;
    }
}
```
* 保持循环体清晰明了。

```js
//bad
for(let i = 0, len = arr.length; i < len; i++) {
    if() {
      ....
      ....
      //一堆逻辑
    } else {
      ...
      ...
      //一堆逻辑
    }
}
//good
for(let i = 0, len = arr.length; i < len; i++) {
    if() {
      doSomeThing();
    } else {
      doOtherThing();
    }
}
```

## last
* 优先使用es6的方法，使代码显得更简短精简。
* 注释要尽量简单，清晰明了。着重注释的意思，对不太直观的部分进行注解。
* javascript放在页尾引入，减少重排与重绘。
* 使用 === 和 !== 取代 == 和 !=。