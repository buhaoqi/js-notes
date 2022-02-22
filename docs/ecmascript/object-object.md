>In JavaScript, objects are king. If you understand objects, you understand JavaScript.

在JavaScript中几乎一切都是对象。


## 对象是什么
- 对象是JavaScript的基本数据类型。
    - 对象将很多值聚合在一起：字符串、数字、布尔值、undefined、null、object、function等
    - 每一个值都有一个名字：标识符、字符串
    - 可以通过名字访问这些值
- 对象是属性的无序集合
    - 每个属性都是一个名值对
    - 属性名是字符串、标识符
    - 属性值可以是任意数据类型。

## 创建对象

通过对象直接量创建
```javascript
let obj1 = {} //创建一个空对象
let obj2 = {a: 2, b: 2}//两个属性
let obj3 = {x:obj2.a, y: obj2.b} //复杂的值
let obj4 = {f: function(a,b){ return a*b }} 
let obj5 = { 
    "Main Title": "OBJECT",//属性名里有空格必须用字符串
    "sub-title" : "JavaScript",//属性名里有横线，必须用字符串
    "for": "all audience",//for是保留字，ES3中必须用字符串；ES5中不必
    author: { //复杂的值
        firstname: '张',  //属性名是标识符
        surname: '三'
    }
 }
```
ES6：增强的对象直接量写法

ES6允许直接写入 **变量** 和 **函数** 作为对象的属性和方法：

```javascript
const username = 'zhangsan'
const birth = '2000-01-01'
let obj6 = {
    username,
    birth,
    hello(){
        console.log('hi')
    }
}

```

通过关键字new + 构造函数创建
```javascript
const o = new Object()
const a = new Array()
const d = new Date()
const r = new RegExp()
```

通过Object.create()函数来创建对象
```javascript
//待补充

```

## 查询对象属性
通过点号查询

通过方括号查询

## 遍历对象属性

`for in`语句用于遍历对象属性。代码块内的代码将为每一个属性执行一次。

```javascript
const person = {
  fname:" John",
  lname:" Doe",
  age: 25
};

for (let x in person) {
  txt += person[x];
}
```

## 添加新属性

可以使用赋值表达式为一个对象添加新值
```javascript
person.nationality = "English";
```
## 删除属性

`delete`关键词用于删除对象属性

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

delete person.age;
```
或者使用方括号删除：

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

delete person["age"];
```
delete关键词既会删除属性值也会删除属性。

## 对象的方法

- 对象方法是指可在对象上执行的动作。
- JS方法指包含函数的属性。
- 方法是存储在对象属性中的函数。

访问对象的方法

```javascript
name = person.fullName()

name = person.fullName
```

## this关键词

- 在JS中，this关键词指的是一个对象
- this指向哪个对象取决于this如何被调用
    - In an object method, this refers to the object.
    - Alone, this refers to the global object.
    - In a function, this refers to the global object.
    - In a function, in strict mode, this is undefined.
    - In an event, this 指向接收事件的元素对象。
    - Methods like call(), apply(), and bind() can refer this to any object.
## 显示对象

```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

document.getElementById("demo").innerHTML = person;//[object object]
```
显示对象的方法：

- Displaying the Object Properties by name
- Displaying the Object Properties in a Loop
- Displaying the Object using Object.values()
- Displaying the Object using JSON.stringify()

方法1：显示对象的属性
```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

document.getElementById("demo").innerHTML =
person.name + "," + person.age + "," + person.city;
```

方法2：遍历对象属性
```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

let txt = "";
for (let x in person) {
txt += person[x] + " ";
};

document.getElementById("demo").innerHTML = txt;
```

方法3：Using Object.values()
Any JavaScript object can be converted to an array using Object.values():

```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

const myArray = Object.values(person);
document.getElementById("demo").innerHTML = myArray;
```
方法4：Using JSON.stringify()
```javascript
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

let myString = JSON.stringify(person);
document.getElementById("demo").innerHTML = myString
```

数组也可以应用stringify()
```javascript
const arr = ["John", "Peter", "Sally", "Jane"];

let myString = JSON.stringify(arr);
document.getElementById("demo").innerHTML = myString;
```

## getter和setter

- ECMAScript5引入了Getters和setters。
- Getters和setters允许你定义对象访问器(计算属性)
- get和set是两个关键词

语法格式：

getters
```javascript
// Create an object:
const person = {
  firstName: "John",
  lastName: "Doe",
  language: "en",
  get lang() {
    return this.language;
  }
};

// Display data from the object using a getter:
document.getElementById("demo").innerHTML = person.lang;
```
setters
```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  language: "",
  set lang(lang) {
    this.language = lang;
  }
};

// Set an object property using a setter:
person.lang = "en";

// Display data from the object:
document.getElementById("demo").innerHTML = person.language;
```
function和getters的区别

- function是作为对象的方法访问对象的属性。
- getters是作为对象的属性访问对象的属性。
- getters的语法更加简洁

使用函数
```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
};

// Display data from the object using a method:
document.getElementById("demo").innerHTML = person.fullName();
```
使用getters
```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  get fullName() {
    return this.firstName + " " + this.lastName;
  }
};

// Display data from the object using a getter:
document.getElementById("demo").innerHTML = person.fullName;
```

为什么使用getters和setters？

- 语法更简洁
- It allows equal syntax for properties and methods
- It can secure better data quality
- It is useful for doing things behind-the-scenes

## 构造函数
```javascript
function Person(first,last,age,eye){
    this.firstName = first
    this.lastName = last
    this.age = age
    this.eyeColor = eye
}

```
在学习构造函数之前，要认识到：

- 之前对对象的认识是有限的。
- 有限在于：我们一直都是在创建一个对象
- 有时，我们需要一个模型来创建多个同一对象类型的对象。
- 创建一个“对象类型”就是创建一个“对象构造函数”
- 在上面的例子中，`function Person()`就是一个`object constructor function`对象构造函数
- 通过使用new关键词调用构造器函数创建同一类型的多个对象。
- 在构造函数中的`this`没有指向，它在构造函数中是一个占位符，当构造函数被调用，新对象被创建时，this指向新对象。

使用new关键词调用构造函数创建对象
```javascript
const myFather = new Person("John", "Doe", 50, "blue");
const myMother = new Person("Sally", "Rally", 48, "green");
```

添加属性
```javascript
myFather.nationality = "English";

```
`nationality`属性只添加到了`myFather`上，并没有添加到其他对象上。

添加方法
```javascript
myFather.name = function () {
  return this.firstName + " " + this.lastName;
};
```
`name()`方法只添加到了`myFather`上，并没有添加到其他对象上。

向构造函数添加属性

```javascript
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
  this.nationality = "English";
}
```

向构造函数添加方法
```javascript
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
  this.name = function() {
    return this.firstName + " " + this.lastName;
  };
}
```

原生对象的内置构造函数

```javascript
new String()    // A new String object
new Number()    // A new Number object
new Boolean()   // A new Boolean object
new Object()    // A new Object object
new Array()     // A new Array object
new RegExp()    // A new RegExp object
new Function()  // A new Function object
new Date()      // A new Date object
```
- Math()对象是全局对象。
- new关键词不能用于Math()对象

## 原始数据类型的对象版本

JS有原始数据类型的对象版本，但是没有理由使用更复杂的对象版本，直接使用直接量创建就好。

- Use string literals "" instead of new String().
- Use number literals 50 instead of new Number().
- Use boolean literals true / false instead of new Boolean().
- Use object literals {} instead of new Object().
- Use array literals [] instead of new Array().
- Use pattern literals /()/ instead of new RegExp().
- Use function expressions () {} instead of new Function().

字符串

通常，字符串被创建为原始值

```javascript
let s = 'hello world'
```
但是字符串也能被创建为对象

```javascript
const s = new String()
```
原始值的比较

```javascript
let x = "John";        // x is a string
let y = new String("John");  // y is an object
let z = "John"
console.log(x===z) //ture
console.log(x===y) //false
```
对象值的比较

```javascript
let x = new String('hello')
let y = new String('hello')
console.log(x==y,x===y) // false false
```

数值

通常，数值被创建为原始值

```javascript
let n = 10
```
但是数值也能被创建为对象

```javascript
const n = new Number(10)
```

布尔

通常，布尔值被创建为原始值

```javascript
let b = ture
```
但是布尔值也能被创建为对象

```javascript
const b = new Boolean(true)
```




## 原型
每一个JS对象都有一个与之相关的原型对象。原型对象的名字叫`prototype`

- 通过直接量({})创建的对象具有同一个原型,即：`Object.prototype`。
- 通过new Array()创建的对象的原型是`Array.prototype`
- 通过new Date()创建的对象的原型是`Date.prototype`
- 通过new Object()创建的对象的原型是`Object.prototype`
- 所有通过自定义构造函数创建的对象都具有一个继承自Object.prototype的原型。





## 属性继承

从原型角度，对象可划分为：

- 普通对象：`Object.prototype`以外的原型对象都是普通对象。普通对象都具有原型。
- 特殊对象：`Object.prototype`是一个没有原型的对象。

原型链

- 每个普通对象都具有“自有属性”。
- 每一个普通对象都从原型继承属性。
    - Date对象的属性继承自`Date.prototype`
    - `Date.prototype`的属性继承自`Object.prototype`
    - Date objects inherit from Date.prototype
    - Array objects inherit from Array.prototype
    - Person objects inherit from Person.prototype
- `Object.prototype`不继承任何属性。位于原型继承链的顶部。

假设要查询对象o的属性x：

- 如果o中不存在x，name将会继续在o的原型对象中查询属性x。
- 如果原型对象中也没有属性x，那么继续在这个原型对象的原型上执行查询属性x。
- 直到找到属性x或者找到一个原型是null的对象为止。
- 可以看到：对象的原型属性构成了一个“链”，通过这个链，可实现属性的继承。



## 属性添加
The JavaScript prototype property allows you to add new properties to object constructors:

`prototype`属性允许你向构造函数添加新属性。

```javascript

function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

Person.prototype.nationality = "English";
Person.prototype.name = function() {
  return this.firstName + " " + this.lastName;
};
```
>Only modify your own prototypes. Never modify the prototypes of standard JavaScript objects.




## 原型链(prototype chain)


## 创建对象的弊端

```javascript
//创建对象user1
const user1 = {
    username: 'xiaoming',
    email: 'xiaoming@qq.com',
    login(){
        console.log(`${this.username}已登录`)
    },
    logout(){
        console.log(`${this.username}已注销`)
    }
}
//访问对象user1
console.log(user1.username, user1.email)
user1.login()

//创建对象user2
const user2 = {
    username: 'xiaohong',
    email: 'xiaohong@qq.com',
    login(){
        console.log(`${this.username}已登录`)
    },
    logout(){
        console.log(`${this.username}已注销`)
    }
}
//访问对象user2
console.log(user2.username, user2.email)
user2.login()
```
>问题：一个一个创建对象太麻烦了。我们需要一个对象模型来创建多个同一类型的多个对象。这个对象模型/类型就是“构造函数”。

## 构造函数

什么是构造函数

- 构造函数，就是构造对象的函数。
- 它提供模板，描述对象的基本结构。
- 构造函数，就是一个普通的函数，当我们用它来生成对象（new 构造函数）时，它就是一个构造函数；
- 通过构造函数构造的对象，我们称之为“对象实例”。
- 通过new关键词调用同一个构造函数构造出的对象实例具有相同的对象类型。
- 在构造函数中的this没有指向，它在构造函数中是一个占位符，当构造函数被调用，新对象被创建时，this指向新对象。

创建一个构造函数

```javascript
function User(name,email){
    this.username = name
    this.email = email
    this.login = function(){
        console.log(`${this.username}已登录`)
    }
    this.logout = function(){
        console.log(`${this.username}已注销`)
    }
}
```

调用构造函数

```javascript
const user1 = new User('zhangsan','zhangsan@qq.com')
const user2 = new User('xiaoming','xiaoming@qq.com')
console.log(user1,user2)
user1.login()
user2.login()
```

为user1实例添加私有方法

```javascript
user1.score = 0
user1.incScore = function(){
    this.score += 1
    return this.score
}
console.log(user1.incScore())//1
console.log(user1)
console.log(user2.incScore())//error
```

为构造函数添加属性和方法
```javascript
function User(name,email){
    this.username = name
    this.email = email
    this.score = 0
    this.login = function(){
        console.log(`${this.username}已登录`)
    }
    this.logout = function(){
        console.log(`${this.username}已注销`)
    }
    this.incScore = function(){
        this.score += 1
        return this.score
    }
}
```
>问题：创建太多的对象，和方法，消耗内存

## 构造函数的原型
- 当使用new关键词调用构造函数创建对象实例时，构造函数会自动为实例对象分配一个父级对象，这个父级对象就是实例对象的原型，
- 并且实例对象会拥有这个它的原型的所有属性和方法。
- 每一个构造函数都有一个prototype属性，这个属性就是实例对象的原型对象。

改造代码
```javascript
function User(name,email){
    this.username = name
    this.email = email
    this.score = 0
}
User.prototype.login = function(){
        console.log(`${this.username}已登录`)
    }
User.prototype.logout = function(){
    console.log(`${this.username}已注销`)
}
User.prototype.incScore = function(){
    this.score += 1
    console.log(this.score)
}
const user1 = new User('zhangsan','zhangsan@qq.com')
const user2 = new User('xiaoming','xiaoming@qq.com')
user1.login()
user2.incScore()
console.log(user1)
```

## 案例：选项卡的传统写法

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .tabs{
            border:1px solid red;
            width:300px;
            height:200px;
            position:relative;
        }
        .tab{
            border:none;
            outline: none;
            width:100px;
            height:40px;
            float:left;
        }
        .tab-content{
            height:calc(100% - 40px);
            position:absolute;
            left:0;
            top:40px;
            display: none;
            width:100%;
        }
        .tab-content:nth-child(2){
            background-color:pink;
            display: block;
        }
        .tab-content:nth-child(3){
            background-color:lightblue;
        }
        .tab-content:nth-child(4){
            background-color:lightgreen;
        }
        .active{
            background-color: gold;
        }
    </style>
    <script>
        window.onload = function(){
            const container = document.querySelector('.tabs')
            const tabs = document.querySelectorAll('.tab')
            const contents = document.querySelectorAll('.tab-content')
            let last = tabs[0]

            for(let i=0;i<tabs.length;i++){
                tabs[i].index = i
                tabs[i].onclick = function() {
                    last.classList.remove('active')
                    contents[last.index].style.display = 'none'
                    this.classList.add('active')
                    contents[this.index].style.display = 'block'
                    last = this
                }
            }
        }
    </script>
</head>
<body>
    <div class="tabs">
        <div class="tab-container">
            <button class="tab active">Tab1</button>
            <button class="tab">Tab2</button>
            <button class="tab">Tab3</button>
        </div>
        <div class="tab-content">Tab1 Content</div>
        <div class="tab-content">Tab2 Content</div>
        <div class="tab-content">Tab3 Content</div>
    </div>
</body>
</html>
```

## 案例：选项卡改写OOP的思路

```javascript
let container = null //2. 局部变量改成全局变量
let tabs = null
let contents = null
let last = null
window.onload = function(){
    container = document.querySelector('.tabs')
    tabs = document.querySelectorAll('.tab')
    contents = document.querySelectorAll('.tab-content')
    last = tabs[0]

    init()
}

function init(){ //3. 把Onload中不是赋值的语句放在单独的函数中
    for(let i=0;i<tabs.length;i++){
        tabs[i].index = i
        tabs[i].onclick = switchTab
    }
}

function switchTab(){ //1、不要出现函数嵌套函数
    last.classList.remove('active')
    contents[last.index].style.display = 'none'
    this.classList.add('active')
    contents[this.index].style.display = 'block'
    last = this
}

```

## 案例：选项卡的OOP写法

```javascript
window.onload = function(){
    const tab1 = new Tab()
    tab1.init()
}
function Tab(){
    this.container = document.querySelector('.tabs')
    this.tabs = document.querySelectorAll('.tab')
    this.contents = document.querySelectorAll('.tab-content')
    this.last = this.tabs[0]
}
Tab.prototype.init = function(){
    let This = this
    for(let i=0;i<this.tabs.length;i++){
        this.tabs[i].index = i
        this.tabs[i].onclick = function(){
            This.switchTab(this)
        }
    }
}
Tab.prototype.switchTab = function(obj){
    this.last.classList.remove('active')
    this.contents[this.last.index].style.display = 'none'
    obj.classList.add('active')
    this.contents[obj.index].style.display = 'block'
    this.last = obj
}
```
## 案例：多个选项卡

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .tabs{
            border:1px solid red;
            width:300px;
            height:200px;
            position:relative;
        }
        .tab{
            border:none;
            outline: none;
            width:100px;
            height:40px;
            float:left;
        }
        .tab-content{
            height:calc(100% - 40px);
            position:absolute;
            left:0;
            top:40px;
            display: none;
            width:100%;
        }
        .tab-content:nth-child(2){
            background-color:pink;
            display: block;
        }
        .tab-content:nth-child(3){
            background-color:lightblue;
        }
        .tab-content:nth-child(4){
            background-color:lightgreen;
        }
        .active{
            background-color: gold;
        }
    </style>
    <script>
        window.onload = function(){
            const tab1 = new Tab('#tabs1')
            tab1.init()
            const tab2 = new Tab('#tabs2')
            tab2.init()
        }
        function Tab(id){
            this.container = document.querySelector(id)
            this.tabs = this.container.querySelectorAll('.tab')
            this.contents = this.container.querySelectorAll('.tab-content')
            this.last = this.tabs[0]
            this.num = 0
        }
        Tab.prototype.init = function(){
            let This = this
            for(let i=0;i<this.tabs.length;i++){
                this.tabs[i].index = i
                this.tabs[i].onclick = function(){
                    This.switchTab(this)
                }
            }
        }
        Tab.prototype.switchTab = function(obj){
            this.last.classList.remove('active')
            this.contents[this.last.index].style.display = 'none'
            obj.classList.add('active')
            this.contents[obj.index].style.display = 'block'
            this.last = obj
        }
    </script>
</head>
<body>
    <div class="tabs" id="tabs1">
        <div class="tab-container">
            <button class="tab active">Tab1</button>
            <button class="tab">Tab2</button>
            <button class="tab">Tab3</button>
        </div>
        <div class="tab-content">Tab1 Content</div>
        <div class="tab-content">Tab2 Content</div>
        <div class="tab-content">Tab3 Content</div>
    </div>

    <div class="tabs" id="tabs2">
        <div class="tab-container">
            <button class="tab active">Tab1</button>
            <button class="tab">Tab2</button>
            <button class="tab">Tab3</button>
        </div>
        <div class="tab-content">Tab1 Content</div>
        <div class="tab-content">Tab2 Content</div>
        <div class="tab-content">Tab3 Content</div>
    </div>
</body>
</html>
```
## 案例：选项卡自动播放

```javascript
window.onload = function(){
    const tab1 = new Tab('#tabs1')
    const tab2 = new Tab('#tabs2')
    tab1.init()
    tab2.init()
    tab2.autoPlay()
}
function Tab(id){
    this.container = document.querySelector(id)
    this.tabs = this.container.querySelectorAll('.tab')
    this.contents = this.container.querySelectorAll('.tab-content')
    this.last = this.tabs[0]
    this.num = 0
}
Tab.prototype.init = function(){
    let This = this
    for(let i=0;i<this.tabs.length;i++){
        this.tabs[i].index = i
        this.tabs[i].onclick = function(){
            This.switchTab(this)
        }
    }
}
Tab.prototype.switchTab = function(obj){
    this.last.classList.remove('active')
    this.contents[this.last.index].style.display = 'none'
    obj.classList.add('active')
    this.contents[obj.index].style.display = 'block'
    this.last = obj
}
Tab.prototype.autoPlay = function(obj){
    let This = this
    setInterval(function(){
        if(This.num == 0){
            This.tabs[This.tabs.length-1].classList.remove('active')
            This.contents[This.tabs.length-1].style.display = 'none'
        } else {
            This.tabs[This.num-1].classList.remove('active')
            This.contents[This.num-1].style.display = 'none'
        }
        This.tabs[This.num].classList.add('active')
        This.contents[This.num].style.display = 'block'
        This.num++
        if(This.num == This.tabs.length){
            This.num = 0
        }
    },1000)
}
```
## 案例：拖拽传统

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
        }
    </style>
    <script>
window.onload = function(){
    const div = document.querySelector('.box')
    let x = y = 0
    div.onmousedown = function(ev){
        x = ev.clientX - div.offsetLeft
        y = ev.clientY - div.offsetTop
        document.onmousemove = function(ev){
            div.style.left = ev.clientX - x + 'px'
            div.style.top = ev.clientY - y + 'px'
        }
        document.onmouseup = function(){
            document.onmousemove = document.onmouseup = null
        }
        return false
    }
}
    </script>
</head>
<body>
    <div class="box"></div>
</body>
</html>

```

## 案例：改造拖拽

```javascript
let div = null
let x = 0
let y = 0
window.onload = function () {
    div = document.querySelector('.box')
    init( )
}
function init(){
    div.onmousedown = fnDown
}
function fnDown(ev) {
    x = ev.clientX - div.offsetLeft
    y = ev.clientY - div.offsetTop
    document.onmousemove = fnMove
    document.onmouseup = fnUp
    return false
}
function fnMove(ev) {
    div.style.left = ev.clientX - x + 'px'
    div.style.top = ev.clientY - y + 'px'
}
function fnUp() {
    document.onmousemove = document.onmouseup = null
}
```


## 案例：拖拽OOP

```javascript
window.onload = function(){
    const d1 = new Drag('#box1')
    d1.init()
    const d2 = new Drag('#box2')
    d2.init()
}
function Drag(id){
    this.div = document.querySelector(id)
    this.x = 0
    this.y = 0
}
Drag.prototype.init = function(){
    let This = this
    this.div.onmousedown = function(ev){
        This.fnDown(ev)
    }
}
Drag.prototype.fnDown = function(ev){
    this.x = ev.clientX - this.div.offsetLeft
    this.y = ev.clientY - this.div.offsetTop
    let This = this
    document.onmousemove = function(ev){
        This.fnMove(ev)
    }
    document.onmouseup = function(ev){
        This.fnUp(ev)
    }
    return false
}
Drag.prototype.fnMove = function(ev){
    this.div.style.left = ev.clientX - this.x + 'px'
    this.div.style.top = ev.clientY - this. y + 'px'
}
Drag.prototype.fnUp = function(ev){
    document.onmousemove = document.onmouseup = null
}
```

## 不要修改系统对象

```javascript
//不要修改系统对象下面的属性和方法，但是可以锻炼系统方法的写法
const arr = [1,2,3]
Array.prototype.push = function(){
    for(let i=0;i<arguments.length;i++){
        arr[this.length] = arguments[i]
    }
    return this.length
}
arr.push(4,5,6)
console.log(arr)
```

## 包装对象

思考：字符串为什么会有方法

```javascript
const str = 'hello world'
console.log(typeof str)
const r = str.charAt(0)
console.log(r)
const r2 = str.indexOf('e')
console.log(r2)
```

所有的基本数据类型都有自己的包装对象。

字符串类型
```javascript
const str = new String('hello world')
console.log(typeof str) // object

String.prototype.charAt = function(){
    //code
}

//返回最后一个字符的方法
String.prototype.lastChar = function(){
    return this.charAt(this.length - 1)
}

```

包装对象被销毁

```javascript
let str1 = 'aaa'
str1.number = 10
console.log(str.number)//undefined
```
字符串既然不是对象，为什么会有属性呢？

只要引用了字符串的属性，js就会将字符串值通过调用new String(s)的方式转换成对象，这个对象继承了字符串的方法和属性，一旦属性引用结束，这个新建的对象就会被销毁。


git config --global --unset https.proxy

## 案例：OOP书籍列表

HTML+CSS

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="container">
        <h1>添加书籍</h1>
        <form class="book-form" id="book-form">
            <div>
                <label for="title">标题</label>
                <input type="text" id="title" class="">
            </div>
            <div>
                <label for="author">作者</label>
                <input type="text" id="author" class="">
            </div>
            <div>
                <label for="isbn">ISBN</label>
                <input type="text" id="isbn" class="">
            </div>
            <div>
                <input type="submit" value="提交">
            </div>
        </form>
        <table>
            <thead>
                <tr>
                    <th>书籍</th>
                    <th>作者</th>
                    <th>ISBN</th>
                    <th>备注</th>
                </tr>
            </thead>
            <tbody class="book-list"></tbody>
        </table>
    </div>
    <script src="6-app.js"></script>
</body>
</html>
```

## 案例：书籍列表
app.js

```javascript
//创建Book构造函数
const Book = function(title,author,isbn){
    this.title = title
    this.author = author
    this.isbn = isbn
}
//创建UI构造函数
const UI = function(){}
UI.prototype.addBookToList = function(book){
    const list = document.querySelector('.book-list')
    const row = document.createElement('tr')
    row.innerHTML = `
        <td>${book.title}</td>
        <td>${book.author}</td>
        <td>${book.isbn}</td>
        <td><a href='' class='delete'>删除</a></td>
    `
    list.appendChild(row)
}
UI.prototype.showAlert = function(message,className){
    const div = document.createElement('div')
    div.className = `alert ${className}`
    div.appendChild(document.createTextNode(message))
    const container = document.querySelector('#container')
    const form = container.querySelector('#book-form')
    container.insertBefore(div,form)
    setTimeout(function(){
        document.querySelector('.alert').remove()
    },3000)
}
UI.prototype.deleteBook = function(target){
    if(target.className = 'delete'){
        target.parentElement.parentElement.remove()
    }
}
UI.prototype.clearFields = function(){
    document.querySelector('#title').value = ''
    document.querySelector('#author').value = ''
    document.querySelector('#isbn').value = ''
}

//form event listening
const bookForm = document.querySelector('#book-form')
bookForm.addEventListener('submit',function(e){
    //Get form value
    const title = document.querySelector('#title').value
    const author = document.querySelector('#author').value
    const isbn = document.querySelector('#isbn').value
    //validate
    const book = new Book(title,author,isbn)//instantiate book
    const ui = new UI()//instantiate UI
    if(title =='' || author == ''||isbn==''){
        ui.showAlert('请不要留空','error')
    } else {
        ui.addBookToList(book)//添加到dom
        ui.showAlert('书籍已添加','success')//
        ui.clearFields()//
    }
    e.preventDefault()
})
//click event listening
const bookList = document.querySelector('.book-list')
bookList.addEventListener('click',function(e){
    const ui = new UI()
    ui.deleteBook(e.target)
    ui.showAlert('书籍已删除','success')
    e.preventDefault()
})
```

## 案例：OOP测试题APP

html部分：
```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="quiz1"></div>
    <div id="quiz2"></div>
    <script src="app.js"></script>
</body>
</html>

```
js部分
```javascript
//Question构造函数
function Question(title,answers,correctAnswer){
    this.title = title
    this.answers = answers
    this.correctAnswer = correctAnswer
}
Question.prototype.isCorrectAnswer = function(myAnswer){
    return myAnswer === this.correctAnswer
}

const questions = [
        new Question('1下列哪一项不属于面向对象编程语言？',['Java','C#','C++','C'],'C'),
        new Question('2下列哪一项不属于面向对象编程语言？',['Java','C#','C++','C'],'C'),
        new Question('3下列哪一项不属于面向对象编程语言？',['Java','C#','C++','C'],'C'),
        new Question('4下列哪一项不属于面向对象编程语言？',['Java','C#','C++','C'],'C'),
        new Question('5下列哪一项不属于面向对象编程语言？',['Java','C#','C++','C'],'C'),
        new Question('6下列哪一项不属于面向对象编程语言？',['Java','C#','C++','C'],'C'),
        new Question('7下列哪一项不属于面向对象编程语言？',['Java','C#','C++','C'],'C'),
    ]  

//Quiz构造函数
function Quiz(id,questions){
    this.container = document.querySelector(id)
    this.score = 0
    this.questions = questions
    this.questionIndex = 0
}
Quiz.prototype.getQuestion = function(){
    return this.questions[this.questionIndex]
}
Quiz.prototype.createQuestion = function(i){
    if(this.isEnded()){
        this.showScore()
    } else {
        const p = document.createElement('p')
        p.innerHTML = this.getQuestion().title
        const ul = document.createElement('ul')
        const answers = this.getQuestion().answers
        for(let i=0;i<answers.length;i++){
            const li = document.createElement('li')
            li.innerHTML = answers[i]
            let This = this
            li.onclick = function(e){
                This.countScore(e.target.innerText)
                // This.questionIndex++
                This.container.innerHTML = ''
                This.createQuestion()
            }
            ul.appendChild(li)
        }
        this.container.appendChild(p)
        this.container.appendChild(ul)
    }
    
}

Quiz.prototype.countScore = function(answer){
    if(this.getQuestion().isCorrectAnswer(answer)){
        this.score++
    }
    this.questionIndex++
}

Quiz.prototype.isEnded = function(){
    return this.questions.length === this.questionIndex
}

Quiz.prototype.showScore = function(){
    let gameOverHtml = `<h1>Result</h1>`
    gameOverHtml += `<h2 id='score'>你的得分: ${this.score}</h2>`
    const element = document.querySelector('#quiz1')
    element.innerHTML = gameOverHtml
}

const quiz1 = new Quiz('#quiz1',questions)
quiz1.createQuestion()

const quiz2 = new Quiz('#quiz2',questions)
quiz2.createQuestion()

```