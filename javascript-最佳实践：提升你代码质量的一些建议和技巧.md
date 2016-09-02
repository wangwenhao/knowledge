# JavaScript 最佳实践：提升你代码质量的一些建议和技巧

[原文地址](https://www.codementor.io/javascript/tutorial/javascript-best-practices)

一个理性的人每天学习一点新事物来让自己变得更强大。作为一个开发者，不断地学习新事物是我们工作的一部分，无论这些新事物是否是从积极的学习经验而来的。

在这个教程里，我会指出一些 JavaScript 中重要的最佳实践，所以你不用学得很艰难。准备好提升你的代码吧！

## 1. 避免污染全局作用域

定义变量是十分有趣的一件事。有些时候你可能会无意识的定义全局变量。在当今的浏览器中，全局变量储存在`window`对象中。所以，哪里有一堆数据，而你可能会覆盖掉它们的默认值。

假设你有一个HTML文件包含一个`<script>`标签（或者从某处加载了一个JavaScript文件）：
``` javascript
var foo = 42;
console.log(foo);
```
显而易见，这段代码会将42输出在控制台。但是由于这段代码没有在函数里运行，它的运行上下文就是全局。所以，变量就会附加在`window`对象上。也就等同于`window.foo`的值是42。

由于这样可以覆盖现有的全局变量，所以很危险：
``` javascript
function print () {
  // do something
}

print();
```
当执行`window.print()`（或者`print`），这时不会打开打印对话框，因为我们已经覆盖了原生的打印对话框。