# Cookie

 cookie:

​            其实是后端的技术，用来记录匹配后端的sessionID的从而保证用户只要在当前浏览器访问页面，登录信息不会被丢失。

​	cookie是在服务器下运行的。

​	前端使用一般用来数据存储（配合后端进行一些用户优化）

 设置cookie

​            **每个域名**下一般就多少条（多少个、多少k）

​            document.cookie = 'key=value';

​        生命周期:

​            默认的生命周期就是当前的浏览器彻底关闭，生命结束



以下是封装的Cookie封装

```javascript

function setCookie(key,value,t) {
	if (t) {
		var oDate = new Date();
		oDate.setDate(oDate.getDate()+t);
		document.cookie = key+'='+ encodeURI(value) + ';expires='+ oDate.toGMTString();
	}else{
		document.cookie = key+'='+ encodeURI(value);
	}
	
}

function getCookie(key) {
	var arr1 = document.cookie.split('; ');
	for (var i =0;i<arr1.length;i++) {
		var arr2 = arr1[i].split('=');
		if (arr2[0] == key) {
			return decodeURI(arr2[1]);
		}
	}
}

function removeCookie(key) {
	setCookie(key,'',-1)
}
```

