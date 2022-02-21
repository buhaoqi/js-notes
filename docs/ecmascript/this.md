
- In JavaScript, the this keyword refers to an object.

- Which object depends on how this is being invoked (used or called).

- The this keyword refers to different objects depending on how it is used:

    - In an object method, this refers to the object.
    - Alone, this refers to the global object.
    - In a function, this refers to the global object.
    - In a function, in strict mode, this is undefined.
    - In an event, this refers to the element that received the event.
    - Methods like call(), apply(), and bind() can refer this to any object.


## 全局对象中的this

全局变量中的this指向window对象
```javascript
    var x = this
    console.log(this) //window
 ```   
全局函数中的this指向window对象
```javascript
    var fn = function(){
        console.log(this)//window
    }
    fn()
```
## 局部对象中的this
方法中的this指向局部对象
```javascript
    var obj = {
        a:this,
        sum(){
            console.log(this)
        }
    }
    console.log(obj.a)//window
    obj.sum()//obj
```  
## 事件处理函数中的this

在事件处理函数中，this指向接收事件的元素对象
```javascript
document.body.onclick = function(){
    console.log(this)//body
}
```
或
```javascript
document.body.onclick = fn //body
fn()//window
function fn(){
    console.log(this)
}
```
事件处理函数参数中的this指向window

```javascript
document.body.onclick = this.obj.sum //undefined
document.body.onclick = obj.sum //undefined
```
解决办法
```javascript
This = this
document.body.onclick = function(){
    This.obj.sum()
}
```
测试

```javascript
    var a = 100
    var obj = {
        a:1,
        sum(){
            console.log(this.a)
        }
    }
    obj.sum()//1
    console.log(this.a)//100

    const fn = function(){
        console.log(this.a)
    }
    fn()


    document.body.onclick = this.obj.sum //undefined
    document.body.onclick = obj.sum //undefined
    This = this
    document.body.onclick = function(){
        This.obj.sum()
    }

```