### 神奇的this

​	this会弹出的情况

​			window

​			事件触发元素

​			对象

​			undefined

​			父级

​			写啥是啥

先看是函数还是方法，如果是方法，那么this基本上是寄主。

如果是函数，那么基本上是window



window情况

```javascript
function fn(){
    //window
}
fn()//只要是前面什么都没加，都是window调用
```



事件触发元素情况

```javascript
document.onclick = function(){
    //document
}
```

对象情况

```javascript
function drap(){
    
}
drap.prototype.down = function(){
    //
}
var arr = new drap;
arr.down()//this是arr
```



undefined情况

```javascript
class p{
    eat(){
        function a(){
         //this是undefined,因为在严格模式下，直接调用函数都是undefined
        }
      a()
    }
}
```



父级

```javascript
function p(){
    var a = () =>{
        //this只想p{}
    }
    a();
}
new p
```



写啥是啥

```javascript
function p(){
    //this是document
}
p.call(document)
```

