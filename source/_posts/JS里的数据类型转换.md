---
title: JS里的数据类型转换
date: 2019-04-11 14:25:08
tags:
---

>## JS有7种数据类型，分别是
number string boolean symbol null undefined object

### 某些数据类型之间可以转换

>## 一、数据类型转成字符串
### 1. toString()
```
(1).toString()
//"1"
```


```
true.toString()
//"true"
```


#### null和undefined使用toString会报错，因为它们没有toString属性
#### 对象的toString会得到"[object Object]"

![图示1](JS里的数据类型转换/toString.png)


### 2. String
![图示2](JS里的数据类型转换/String.png)

>### 3. + ''
    使用加号和空字符串

```
1 + ''
//"1"
```


```
true + ''
//"true"
```


### 4. window.String
![图示3](JS里的数据类型转换/window.String.png)


>## 二、数据类型转成布尔值
### 1. Boolean
```
Boolean(1)
//true
```


```
Boolean(0)
//false
```


>### 2. !!
```
!! 1
//true
```


```
!! 0
//false
```


```
!! 'x'
//true 
```

    
#### 注意： 5个falsy值，0，空字符串，null，undefined，NaN
#### 注意： 容易被认作是falsy值，但不是，空格字符串，（空）对象


>## 三、数据类型转成数字
### 1. Number
```
Number('1')
//1
```


### 2. parseInt
```
parseInt('1',10)
//1
```


```
parseInt('2')
//2
```


### 3. parseFloat
```
parseFloat('1.23')
//1.23
```


### 4. x - 0
```
'1' - 0
//1
```

![图示4](JS里的数据类型转换/-0.png)


### 4. + x
```
+ '1'
//1
```

![图示5](JS里的数据类型转换/+.png)


>## 四、内存图

#### JS 引擎将内存分为代码区和数据区

#### 数据区分为 Stack（栈内存） 和 Heap（堆内存）

#### 简单类型的数据直接存在 Stack 里

#### 复杂类型的数据是把 Heap 地址存在 Stack 里

![图示6](JS里的数据类型转换/内存图.jpg)


![图示7](JS里的数据类型转换/垃圾回收及深拷贝浅拷贝.jpg)