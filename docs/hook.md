# hook

<br>

[继承与原型链 - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

this 指向问题：[JS函数hook_愧怍小儿的博客-CSDN博客_hook js函数](https://blog.csdn.net/kuizuo12/article/details/121482173)

<br>

函数 hook

```js
let btoa_bk = btoa;
btoa = function(val){
    console.log(val)
    debugger;
    return btoa_bk
}
```

```js
(function () {
  function hook(object, attr) {
    var func = object[attr];
    object[attr] = function () {
      console.log("hooked", object, attr);
      var ret = func.apply(object, arguments);
      debugger;
      return ret;
    };
  }
  hook(window, "btoa");
})();
```

<br>

属性 hook

Object.defineProperty：[Object.defineProperty](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

`Object.defineProperty()`  方法会直接在一个对象上**定义**一个新属性，或者**修改**一个对象的现有属性，并返回此对象。

<br>

```js
// 例子
Object.defineProperty(docment, 'cookie', {
	set: function(val){
	debugger;
	return val	
 }
})
```

<br>

利用油猴脚本方式注入	TODO

<br>

利用控制台方式注入	TODO

