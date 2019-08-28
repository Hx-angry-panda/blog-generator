---
title: 实现一个jQuery的API
date: 2019-05-14 17:42:54
tags:
---

### jQuery介绍
jQuery 是一个高效、精简并且功能丰富的 JavaScript 工具库。

它提供的 API 易于使用且兼容众多浏览器，这让诸如 HTML 文档遍历和操作、事件处理、动画和 Ajax 操作更加简单。
 
### 为什么要学习jQuery
1. DOM语法繁琐、兼容性差等问题
2. jQuery容易上手，强大的选择器，节约开发时间，丰富的UI，完善的事件机制，Ajax的封装等等优点

### 利用DOM仿写一个jQuery的API
要求：
1. 能给所有div添加样式
2. 能将所有div的textContent替换

---
思路：
1. 创建一个函数 window.jQuery = function() {}

    获取所有div
    创建一个空对象来放置获取的所有div
    遍历这个对象，给所有div都加class
    遍历这个对象，给所有的div设置文本内容
    返回这个对象

2. 仿照jQuery的写法

    window.$ = jQuery
    
3. 创建变量

    var $div = $('div')

4. 调用函数

    $div.addClass('red')
    
    $div.setText('hi')


HTML
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
</head>
<body>
  <div>1</div>
  <div>2</div>
  <div>3</div>
</body>
</html>
```

CSS
```
.red{
  color: red;
}
```

JavaScript
```
//指定选择器
window.jQuery = function(nodeOrSelector) {
  let nodes = {}
  if (typeof nodeOrSelector === 'string') {
    let temp = document.querySelectorAll(nodeOrSelector)
    for (let i = 0; i < temp.length; i++) {
      nodes[i] = temp[i]
    }
    nodes.length = temp.length
  } else if (nodeOrSelector instanceof Node) {
    nodes = {
      0: nodeOrSelector,
      length: 1
    }
  }
  
  //添加样式
  nodes.addClass = function(classes) {
    for (let i = 0; i < nodes.length; i++) {
      nodes[i].classList.add(classes)
    }
  }
  
  //设置文本内容
  nodes.setText = function(text) {
    for (let i = 0; i < nodes.length; i++) {
      nodes[i].textContent = text
    }
  }
  return nodes
}

window.$ = jQuery
var $div = $('div')
$div.addClass('red')
$div.setText('hi')
```

### 总结
jQuery是包装DOM后的产物，实质上是函数

像调用函数一样，来使用jQuery