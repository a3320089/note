## let 和const

let命令：用来声明一个变量，和var非常类似。

const命令：用来声明一个常量，常量就是不可以变化的量。



1.使用let声明的变量，所声明的变量只能在命令所在的代码块内有效

```javascript
{
    let a = 1;
  	var b = 2;
  console.log(a)//1
}
console.log(a) //报错
console.log(b)//2
```



2.使用let命令声明的变量在预解析的时候不会被提升

```javascript
console.log(a) //undefined
var a = 1;

console.log(b)//报错
let b = ;
```



```javascript
let f = 10;
function fn(){
    f = 7; //报错,暂时性死去
  let f = 2;
}
fn();
```



3.let不允许在同一个作用域下声明已经存在的变量

```javascript
var a = 1;
let a;//报错

let b = 1;
let b = 2;//报错
```

let在for循环中的应用

```javascript
var btn = document.getElementsByTagName('button');
for(let i=0;i<btn.length;i++){
    btn[i].onclick = function(){
        console.log(i) //点哪个弹哪个
    }
}
```



## const

   const命令同样有上面let的前3条特点，第一、所声明的常量只在其所在的代码块内有效，第二、声明的常量不会被提升，第三、不能声明已经被声明过的常量或者变量。除了这些，在使用const声明常量的时候需要注意两点。

1、声明的时候必须赋值

```javascript
const a;//报错
const a=10;//ok
```

2、声明的常量储存简单的数据类型时候不可以改变其值，如果储存的是对象，那么引用不可以被改变，至于对象里面的数据如何变化，是没有关系的。

```javascript
const a=1;
a = {}//报错

const obj = {a:10};
obj.a = 20;//OK，没有修改obj这个名字
```

