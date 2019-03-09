---
title: CSS布局
date: 2019-03-09 14:09:09
tags:
---

## CSS布局
### 1. 左右布局的实现
HTML部分
```
<body>
    <div class="box clearfix">
        <div class="left" style="width: 100px; height: 100px; background: red;"></div>
        <div class="right" style="width: 100px; height: 100px; background: blue;"></div>
    </div>
</body>
```

#### （1）使用margin

CSS部分
```
.right{
    margin-top: -100px;
    margin-left: 100px;
}
```
#### （2）使用float浮动

CSS部分
```
.left{
    float: left;
}
.right{
    float: left;
}
.clearfix{
    content: '';
    display: block;
    clear: both;
}
```
#### （3）使用inline-block

CSS部分
```
.left{
    display: inline-block;
}
.right{
    display: inline-block;
}
```
#### （4）绝对定位

CSS部分
```
body{
    margin: 0;
    padding: 0;
}
.box{
    position: relative;
}
.left{
    position: absolute;
    top: 0;
    left: 0;
}
.right{
    position: absolute;
    top: 0;
    left: 100px;
}

```
#### （5）flex布局

CSS部分
```
.box{
    display: flex;
    flex-direction: row;
}
```

### 2. 左中右布局的实现
HTML部分
```
<body>
    <div class="box">
        <div class="left" style="width: 100px; height: 100px; background: red;"></div>
        <div class="middle" style="width: 100px; height: 100px; background: blue;"></div>
        <div class="right" style="width: 100px; height: 100px; background: green;"></div>
    </div>
</body>
```

#### （1）使用margin
#### （2）使用float浮动
#### （3）绝对定位
#### （4）使用inline-block
#### （5）flex布局

### 3. 水平居中

#### （1）块级元素
    
    （a）定宽
        
        1. margin: 0 auto;
        
        2. 绝对定位+外边距
        
        3. 父元素样式属性display:flex;子元素使用margin:auto;未知子元素高度的时候依然可以使用。
    
    （b）无定宽
        
        1. 子元素加display: inline-block; vertical-align: top; 父元素加text-align: center;
        
        2.加入 table 标签
        
        3.通过给父元素设置 float，然后给父元素设置 position:relative 和 left:50%，子元素设置 position:relative 和 left: -50% 来实现水平居中。

#### （2）行内元素
        
        1.如果被设置元素为文本、图片等行内元素时，水平居中是通过给父元素设置 text-align:center 来实现的。

#### （3）flex布局

#### （4）绝对定位

### 4. 垂直居中

#### （1）父元素高度确定的单行文本
    
        1. 设置父元素的 height 和 line-height 高度一致来实现的
        height: 该元素的高度，line-height: 顾名思义，行高（行间距），指在文本中，行与行之间的 基线间的距离 )。
        line-height 与 font-size 的计算值之差，在 CSS 中成为“行间距”。分为两半，分别加到一个文本行内容的顶部和底部。这种文字行高与块高一致带来了一个弊端：当文字内容的长度大于块的宽时，就有内容脱离了块。

#### （2）父元素高度确定的多行文本
    
        1. 使用插入 table  (包括tbody、tr、td)标签，同时设置 vertical-align：middle。
        因为 td 标签默认情况下就默认设置了 vertical-align 为 middle，所以我们不需要设置了。

#### （3）flex布局

#### （4）绝对定位

### 5.其他小技巧

#### （1）背景水平垂直居中
        background-position: center center;

#### （2）背景自适应
        background-size: cover;
