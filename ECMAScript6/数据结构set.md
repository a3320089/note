# 数据结构set



集合的基本概念：集合是由一组无序且唯一（即不能重复）的项组成的。这个数据结构使用了与有限集合相同的数学概念，应用在计算机的数据结构中。

​	特点：key和value相同，没有重复的value



ES6提供了数据结构中的Set。它类似于数组，但是成员的值是唯一的，没有重复的值。



## 创建一个Set

```javascript
const s = new Set([1,2,3]);
console.log(s);//Set{1,2,3}
```



## set类的属性

```javascript
console.log(s.size) // 3
```



## set类的方法