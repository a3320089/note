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



