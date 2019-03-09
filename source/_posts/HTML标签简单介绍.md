---
title: HTML标签简单介绍
date: 2019-02-19 16:35:55
tags:
---

## HTML标签

----------


### 1. iframe标签

#### 定义：表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中。

e.g. 
```
<iframe src="https://www.baidu.com" name="xxx" frameborder="0"></iframe>
```

iframe 一般会加上 frameborder="0" 取值为1时（默认值），告诉浏览器在当前 iframe 与其他 iframe 之间绘制边框，取0时则无需绘制此边框。

iframe 的name属性往往和 a 的target属性一起用

e.g. 
```
<iframe src="https://www.baidu.com" name="跳转" frameborder="0"></iframe>
<a href="https://www.sohu.com" target="跳转">搜狐网</a>
```

在网页点击带下划线的“搜狐网”，则iframe会从百度首页跳转到搜狐首页

----------


### 2. a标签 

#### 定义：可以创建一个到其他网页、文件、同一页面内的位置、电子邮件地址或任何其他URL的超链接。
#### 跳转页面（HTTP GET请求）

##### a标签的href属性
e.g.
```
<a href="//qq.com">QQ</a>                <!-- 会用当前的协议打开，不会使用HTTP协议 -->
<a href="#xxx">123</a>                   <!-- 不会发起请求和页面跳转 -->
<a href="?name=xxx">123</a>              <!-- 会发起请求 -->
<a href="javascript:alert(1);">123</a>   <!-- 伪协议，会执行alert(1) -->
<a href="javascript:;">123</a>           <!-- 伪协议，点击之后不会跳转 -->
<a href="">123</a>                       <!-- 会跳转自身（刷新） -->
<a href="#">123</a>                      <!-- 跳转到本页面顶部 -->
```
##### a标签的target属性
e.g.
```
<a href="https//www.qq.com" target="_blank">QQ</a>   <!-- 点击QQ后在新窗口打开QQ首页 -->
<a href="https//www.qq.com" target="_self">QQ</a>    <!-- 不写target属性时默认使用_self；点击QQ后在当前页面打开QQ首页 -->
<a href="https//www.qq.com" target="_top">QQ</a>     <!-- 点击QQ后在顶层打开QQ首页 -->
<a href="https//www.qq.com" target="_parent">QQ</a>  <!-- 点击QQ后在父级打开QQ首页 -->
```

----------


### 3. form标签和input标签

#### 定义：表示了文档中的一个区域，这个区域包含有交互控制元件，用来向web服务器提交信息。（提交表单）
#### 跳转页面 （HTTP POST请求）

#### form表单里面没有提交按钮就无法提交，除非用JS

e.g.
```
<form action="xxx.html" method="POST">
    <input type="submit" value="提交">
</form>
```

点击了提交按钮后会跳转到xxx.html，HTTP请求的动词为POST（在Chrome中可查看）
#### method属性一般只写POST,基本不写GET

e.g.
```
<form action="users" method="POST">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit" value="提交">
</form>
```

根据不同的 type 属性值，输入字段拥有很多种形式。
如不输入，则默认为text 单行字段
password 一个值被遮盖的单行文本字段。
submit 用于提交表单的按钮。

在页面中输入表单后，点击提交，HTTP请求会多处第四部分From Data

<input>中的name会被带到第四部分作为HTTP请求的key

如果method="post",在页面输入并提交的内容会在第四部分

e.g.
```
<form action="users" method="GET">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit" value="提交">
</form>
```

method="GET",在页面输入并提交的内容会在请求头的查询参数位置

e.g.
```
<form action="users?xxx=1" method="POST">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit" value="提交">
</form>
```
这样的话POST请求也会有查询参数

####  form 的target属性和 a 的target属性一样

#### form 里面只有一个<button> ，它会自动升级为提交按钮（没有type属性的前提）

e.g.
```
<form action="users" method="POST">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="button" value="button">
    <input type="submit" value="提交">
</form>
```

input的type为button时，是一个普通按钮，不会提交
input的type为sumit时，会提交

e.g.
```
<form action="users" method="POST">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="checkbox">喜欢女
    <input type="submit" value="提交">
</form>
```

在页面中能勾选“喜欢女”这个复选框，但是无法点击“喜欢你”勾选

e.g.
```
<label><input type="checkbox">喜欢女</label>
```

这样点击“喜欢女”也呢个勾选
<label></label>也能包住其他type的input标签

e.g.
```
<label><input type="radio" name="color">红</label>
<label><input type="radio" name="color">黄</label>
```

单选框，加上同样的name属性则能单选


----------


### 4. select标签
#### 定义：表示一个控件，提供一个选项菜单

e.g.
```
<select>
    <option value="">-</option>
    <option value="1">第一组</option>
    <option value="2" disabled>第二组</option>
    <option value="3" selected>第三组</option>
</select>
```

下拉选框 disabled为不能选 selected为默认选中

e.g.
```
<select mltiple>
    <option value="">-</option>
    <option value="1">第一组</option>
    <option value="2" disabled>第二组</option>
    <option value="3" selected>第三组</option>
    <option value="4" >第四组</option>
</select>
```

mltiple 可多选


----------


### 5. textarea标签
### 定义：表示一个多行纯文本编辑控件

e.g.
```
<textarea>Write something here</textarea>
```

无法控制输入框大小，用户能随意拉动

e.g.
```
<textarea style="resize=none"></textarea>
```
用户无法拉动输入框来改变大小

### 6. table标签
### 定义：表示表格数据 — 即通过二维数据表表示的信息

e.g.
```
<table>
    <thead>
        <tr>
            <th>Header content 1</th>
            <th>Header content 2</th>
            </tr>
    </thead>
    <tbody>
        <tr>
            <td>Body content 1</td>
            <td>Body content 2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Footer content 1</td>
            <td>Footer content 2</td>
        </tr>
    </tfoot>        
</table>
```

tr： table row
th： table header
td： table data

e.g.
```
<table border=1>
    <colgroup>
        <col width=100>
        <col width=200 bgcolor=red>
    </colgroup>
    <thead>
        <tr>
            <th>Header content 1</th>
            <th>Header content 2</th>
            </tr>
    </thead>
    <tbody>
        <tr>
            <td>Body content 1</td>
            <td>Body content 2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Footer content 1</td>
            <td>Footer content 2</td>
        </tr>
    </tfoot>        
</table>
```

border=1 边框不会重叠
col width=100 第一列的宽度为100
col width=200 bgcolor=red 第二列的宽度200，背景颜色为红色

e.g.
```
<style>
    table{border-collapse:collapse;}
</style>
```

能把边框重叠
