# JS 作用域

- var 定义的变量，没有块级作用域的概念，但是有函数和全局作用域的区别。
- let 定义的变量，只能在块作用域里访问，不能跨块访问，也不能跨函数访问。
- const 用来定义常量，使用时必须初始化(即必须赋值)，只能在块作用域里访问，而且不能修改。

执行上下文

- 范围：一段 `<script>` 或者一个函数
- 全局：变量定义、函数声明
- 函数：变量定义、函数声明、this、arguments

在 var 和 function 中，会有变量提升的概念，变量定义和函数的声明会在实际代码运行中被提前。（只针对 var 与 function）

作用域链 - 一个自由变量不断往上，从父级作用域去寻找定义。 // 自由变量就是当前作用域中没有定义的变量

function 有两种定义方式，一种是声明式，一种是表达式。区别就在于变量提升。
当在声明之前就调用的话，声明式会正常工作，而表达式则会报错

```js
a(); // aaa
function a() {
  // 声明式
  console.log('aaa');
}
t(); // error
var t = function() {
  // 表达式
  console.log('ttt');
};

console.log(x); // undefined而不会报error
var x = 1;
```

# 闭包

闭包就是能够读取其他函数内部变量的函数，或者子函数在外调用，子函数所在的父函数的作用域不会被释放。

1. 函数作为返回值
2. 函数作为参数来传递

```js
function a() {
  let b = 100;
  return function() {
    console.log(b++); // b是自由变量，也就是在当前作用域没有声明的变量，会沿着作用域链网上从父作用域去寻找
  };
}
```
