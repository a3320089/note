

# Vue

​	vue到底是什么?	

​	一个mvvm框架(库)、和angular类似	比较容易上手、小巧

mvc:	

​	mvp	

​	mvvm	

​	mv*	

​	mvx

官网:http://cn.vuejs.org/	

手册： http://cn.vuejs.org/api/



vue——简单、易学

		指令以 v-xxx
		一片html代码配合上json，在new出来vue实例
		个人维护项目
	
		适合: 移动端项目,小巧
#### 第一个Vue

```javascript
<div id="box">
	{{msg}}
</div>

var c=new Vue({
	el:'#box',	//选择器  class tagName
	data:{
	 msg:'welcome vue'
	}
});
```



### Vue循环

```javascript
<div v-for="(item, index) in items"></div> //数组
<div v-for="(val, key) in object"></div> //对象
<div v-for="(val, key, index) in object"></div>
```

### Vue事件

```javascript
v-on:click="函数"

v-on:click/mouseout/mouseover/dblclick/mousedown.....

new Vue({
  el:'#box',
  data:{ //数据
    arr:['apple','banana','orange','pear'],
    json:{a:'apple',b:'banana',c:'orange'}
  },
  methods:{
    show:function(){	//方法
      alert(1);
    }
  }
});
```

事件进阶：	

	v-on:click/mouseover......
	简写的:
	@click=""		推荐
	
	事件对象:
		@click="show($event)"
	事件冒泡:
		阻止冒泡:  
			a). ev.cancelBubble=true;
			b). @click.stop	推荐
	默认行为(默认事件):
		阻止默认行为:
			a). ev.preventDefault();
			b). @contextmenu.prevent	推荐
	键盘:
		@keydown	$event	ev.keyCode
		@keyup
	
		常用键:
			回车
				a). @keyup.13
				b). @keyup.enter
			上、下、左、右
				@keyup/keydown.left
				@keyup/keydown.right
				@keyup/keydown.up
				@keyup/keydown.down
			.....


### Vue属性


	v-bind:src=""
			width/height/title....
	简写:
	:src=""	推荐
	
	<img src="{{url}}" alt="">	效果能出来，但是会报一个404错误
	<img v-bind:src="url" alt="">	效果可以出来，不会发404请求
style和class

	:class=""	v-bind:class=""  //要用这种写法
	:style=""	v-bind:style=""
	
	:class="[red]"	//red是data数据
	:class="[red,b,c,d]"//多个数据
	
	:class="{red:a, blue:false}"//直接写对象
	
	:class="json" //数据里面写json
		
		data:{
			json:{red:a, blue:false}
		}
	--------------------------
	style:
	:style="[c]"
	:style="[c,d]"
		注意:  复合样式，采用驼峰命名法
	:style="json"
### Vue模板

```
{{msg}}		数据更新模板变化
{{*msg}}	数据只绑定一次
{{{msg}}}	HTML转意输出
```

### Vue过滤器

```
系统提供一些过滤器:
	
	{{msg| filterA}}
	{{msg| filterA | filterB}}

	uppercase	eg:	{{'welcome'| uppercase}} //大写
	lowercase	//小写
	capitalize//首字母大写

	currency	钱

	{{msg| filterA 参数}}
```

