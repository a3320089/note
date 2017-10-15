#### 字符串新特性

​	

字符串换行可以直接用``扩起来。代替以前的字符串拼接。例如：

```javascript
var str = `我是
	字符串
			`
```



字符串拼接变量时。可以在``中使用${}来拼接

```javascript
var name = "小明"
var str = `我是${name}`;
```



申明变量时可以定义变量的类型，在变量后添加 :string等;要想什么类型都可以，要用:any类型

```javascript
var name:string = "小明";
var age:number = 13;
```



#### 参数新特性



函数申明类型，即返回值是什么类型

```javascript
function t():string{
    return ''
}
```





参数可以设置类型

```javascript
function fn(str:string){
    
}
```



参数可以设置默认值

注意：要设置默认值的参数只能放在后面。

```javascript
function fn(str:string = "小明"){
    
}

```



可选参数，在要设置可选参数的后面添加？必须放在正常参数后面，默认值参数前面

```javascript
function r(str:string,b?){
    
}
```



#### 函数新特性



#####  Rest and Spread操作符：

​		用来申明任意数量的方法参数

...就是 Rest and Spread操作符，等同于arguments

```javascript
function fn (...args){
    console.log(args);
}
fn(1,2,3,4,5)
```



##### generator函数：

​	控制函数的执行过程，手工暂停和恢复代码执行

申明方法在函数后面加*号，yield是断点。用来控制停止和恢复的位置，要调用函数必须申明一个变量，然后调用变量的next()方法;函数执行后会停在yield上，再执行next方法就会执行yield后面的函数

```javascript
function* dosomething(){
    console.log("statr");
  	yield;
  	console.log("finish");
}
var fn1 = dosomething();
fn1.next();
fn1.next();
```



通过next().value可以获取yield后的值

```javascript
function* fn(){
    yield Math.random()*100;
}
var p = fn().next().value;
console.log(p)
```



##### destructuring析构表达式:

​		通过表达式将对象或数组拆解成任意数量的变量

注意：下面申明的变量大括号里面的变量必须要和函数里面返回值的名字一样；即return里的a,b名字要和{a,b}的命名一样。

如果必须要用自定义的变量名，可以使用{a:code,b}=fn();在变量后面加上冒号+要命名的名字

```javascript
function fn(){
    return {
        a:1,
      	b:2
    }
}
var {a,b} = fn();
//var {a:code,b}=fn();
//console.log(code) // 1
```

如果返回值嵌套对象，需要获取对象里的值，则需嵌套析构表达式

```javascript
function fn(){
    return {
        a:1,
      	b:{
            b1:12,
          	b2:13
        }
    }
}
var {a,b:{b1}} = fn();
console.log(b1);//12
```

如果返回函数里还有其他的值，是不影响你的析构表达式，即你可获取你想要的值；



##### 数组中的析构表达式：

```javascript
var arr = [1,2,3,4,5]
var [a,b] = arr;
console.log(a)//1
//获取第三第四个值
var [,,a,b] = arr;
console.log(a)//3
```



析构表达式和Rest操作符共同使用

```javascript
var array1 = [1,2,3,4];
var [num1,num2,...num] = array1;
console.log(num)//[3,4]
```



析构表达式和函数参数

```javascript
var array1 = [1,2,3,4];
function fn( [num1,num2,...num]){
    console.log(num1);//1
  	console.log(num2);//2
 	console.log(num);//[3,4]
}
fn(array1)
```

