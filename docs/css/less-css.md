## 安装

```bash
$ npm install -g less
$ npm install -g less-watch-compiler
$ mkdir less-basic
$ cd less-basic
$ touch style.less #less文件不能引入HTML文档，我们需要对它编译成常规css才可以
$ lessc styles.less # less的编译器 编译到屏幕
$ lessc style.less style.css # 编译到指定文件中

```
less文件：
```less
@background-color:#f4f4f4;

body{
    background-color: @background-color;
}
```

自动监控编译
```less
less-watch-compiler [options] <source_dir> <destination_dir>

less-watch-compiler less css
```

配置文件
```
$ touch less-watch-compiler.config.json

{
    "watchFolder": "src",
    "outputFolder": "dist",
    "mainFile": "main.less"
}

HTML

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

