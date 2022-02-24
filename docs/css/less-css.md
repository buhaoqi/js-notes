## 安装less

```bash
$ npm install -g less

```
## 手动编译less
第一步：创建style.less
```bash
$ mkdir less-basic
$ cd less-basic
$ touch style.less #less文件不能引入HTML文档，我们需要对它编译成常规css才可以
```
第二步：less文件内容：
```less
@background-color:#f4f4f4;

body{
    background-color: @background-color;
}
```
第三步：编译命令
```bash
$ lessc styles.less # less的编译器 编译到屏幕
$ lessc style.less style.css # 编译到指定文件中

```
## 自动编译less
```less
$ npm install -g less-watch-compiler

# 自动监控文件夹
$ less-watch-compiler less css
```
语法：
```bash
$ less-watch-compiler [options] <source_dir> <destination_dir>
```

## 配置文件
```
$ touch less-watch-compiler.config.json

{
    "watchFolder": "src",
    "outputFolder": "dist",
    "mainFile": "main.less"
}
```
## variable
1. 变量使用@定义，用于存储常用值。
2. 变量可以存储颜色值、尺寸值等任意类型的值。
3. 变量值支持运算。
4. 变量值可以是变量。
5. 变量值支持函数。

```less
@black:#010400;
@gray:#30332E;
@light-gray:#f4f4f4;
@white:#FFFBFC;
@cyan:#62BBC1;
@purple:#EC058E;
@line-height:1em + 1em;

@primary-color:@cyan;
@secondary-color:@gray;

@link-color-dark:@primary-color; 
@link-color-dark-hover:  darken(@link-color-dark, 10%);
@link-color-light:@white; 
@link-color-light-hover:  darken(@link-color-light, 20%);

@full-width:100%;
@fixed-width:1200px;
```

## extend()

```less
.btn{
  padding:15px 65px;
  border:0;
}

button:extend(.btn){
    color:@white;
    background-color:@primary-color;
    .border-radius(10px)
}
```


## mixin
1. no perameters: 

```less
img{
  .bordered()
}
.bordered{
  border:1px solid red;
}
```

2. with perameters: 

```less
button:extend(.btn){
    color:@white;
    background-color:@primary-color;
    .border-radius(10px)
}

.border-radius(@radius){
  border-radius:@radius;
}
```

## 嵌套元素
1. 普通嵌套
```less
d
```
2. &表示平级，可设置伪类和兄弟元素

伪类：
```less
a {
  color: blue;
  &:hover {
    color: green;
  }
}
```

多类

```less
.box {
  color: blue;
  &.box1 {
    color: green;
  }
}
```

## 函数
```less
lighter(@primary-color, 50%)
darken()
```
## 条件语句
```less
.text-color(@a) when (lightness(@a)>=50%){
  color:black;
}
.text-color(@a) when (lightness(@a)<50%){
  color:white;
}
.primary-btn:extend(.btn){
background-color:@primary-color;
.text-color(@primary-color);

}
```
## 注释的写法

```less
//不会被编译  
/*会被编译*/
```
## 变量名的组合

```less
@width:1px; 
@style:solid; 
@color:red; 
@red:red; 
@blue:blue;
.box{
    border:@width @style @color;
}
```

## 作用域
```less
.box1{
    @red:red;
    .title{
        color:@red;
    }
}
.box2{
    .title{
        color:@red;
    }
}
```

## HTML

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <h1>一级标题</h1>
    <p>Lorem ipsum dolor sit amet <a href='#' class='primary-text'>consectetur adipisicing</a> elit. Eligendi quasi soluta nam ea nulla necessitatibus deserunt asperiores aperiam. Reiciendis corporis molestiae quasi porro quas ratione cupiditate soluta, totam aspernatur nobis!Lorem ipsum dolor sit amet consectetur adipisicing elit. Eligendi quasi soluta nam ea nulla necessitatibus deserunt asperiores aperiam. Reiciendis corporis molestiae quasi porro quas ratione cupiditate soluta, totam aspernatur nobis!Lorem ipsum dolor is!</p>
    <button class="primary-btn">Read More</button>
    <h3>Hello world</h3>
    <ul id="menu">
        <li><a href="">link 1</a></li>
        <li><a href="">link 2</a></li>
        <li><a href="">link3</a></li>
    </ul>
</body>
</html>
```

CSS文件
```css
@background-color:pink;
@font-family:"苹方";
@primary-color:#3b5998;
@secondary-color:#20b2aa;
@line-height: 1em + 1em;
body{
    background-color: @background-color;
    font-family: @font-family;
    line-height: @line-height;
}
h1,h3{
    .bordered
}
.primary-color{
    color:@primary-color;
}

.primary-btn:extend(.btn){
    background-color: @primary-color;
    color:#fff;
}
.btn{
    padding:10px 15px;
    border:0;
    .border-radius(10px)
}
.border-radius(@radius){
    border-radius: @radius;
}

.bordered{
    border-top:dotted 1px #000;
    border-bottom:dotted 2px #000;
}
ul#menu{
    list-style:none;
    li{
        padding:10px 0; 
        a{
            color:@secondary-color;  
            text-decoration: none;
        }
    }
}
```




## Variables

在单个位置控制常用值。

Overview

在样式表中看到相同的值重复数十次甚至数百次的情况并不少见


变量通过为您提供一种从单个位置控制这些值的方法，使您的代码更易于维护

### 变量插值

上面的例子集中在使用变量来控制 CSS 规则中的值.但它们也可以在其他地方使用，例如选择器名称、属性名称、URL 和 @import 语句
