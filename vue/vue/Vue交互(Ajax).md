# Vue交互(Ajax)

需要引入 vue-resouce库

### 使用方法

```javascript
this.$http.方法(url,data,其他配置).then(成功,失败)
```

### get方法



```javascript


获取一个普通文本数据:
this.$http.get('aa.txt').then(function(res){
  alert(res.data); //成功
},function(res){
  alert(res.status);//失败
});
给服务发送数据:√
this.$http.get('get.php',{ 
  params:{
    a:1,
    b:2
  }
}).then(function(res){
  alert(res.data);
},function(res){
  alert(res.status);
});
```

### post方法

```javascript
this.$http.post('post.php',{
  a:1,
  b:20
},{
  emulateJSON:true //post方法的请求头
}).then(function(res){
  alert(res.data);
},function(res){
  alert(res.status);
});
```

### jsonp

```javascript
this.$http.jsonp("https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su",{
  params:{
    wd:this.iptVal
  },
  jsonp:"cb"
}).then(res=>{
  this.myLi = res.data.s;
},res=>{
  
})
```



### 引入axios

```
一、安装
1、 利用npm安装npm install axios --save

2、 利用bower安装bower install axios --save

3、 直接利用cdn引入<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```



## GET

```javascript
//通过给定的ID来发送请求
axios.get('/user?ID=12345')
  .then(function(response){
    console.log(response);
  })
  .catch(function(err){
    console.log(err);
  });
//以上请求也可以通过这种方式来发送
axios.get('/user',{
  params:{
    ID:12345
  }
})
.then(function(response){
  console.log(response);
})
.catch(function(err){
  console.log(err);
});

作者：FunnySeeker
链接：http://www.jianshu.com/p/df464b26ae58
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```



### POST

```javascript
axios.post('/user',{
  firstName:'Fred',
  lastName:'Flintstone'
})
.then(function(res){
  console.log(res);
})
.catch(function(err){
  console.log(err);
});

```

### 多个请求

```javascript
function getUserAccount(){
  return axios.get('/user/12345');
}
function getUserPermissions(){
  return axios.get('/user/12345/permissions');
}
axios.all([getUserAccount(),getUserPermissions()])
  .then(axios.spread(function(acct,perms){
    //当这两个请求都完成的时候会触发这个函数，两个参数分别代表返回的结果
  }))

```

