# 阻止PC默认事件的好处

### 移动端的点透：

​            当上层元素发生点击的时候，下层元素也有点击（焦点）特性, 在300ms之后，如果上层元素消失或者隐藏，目标点就会“漂移”到下层元素身上，就会触发点击行为。          

​        解决：

​            1.下层不要使用有点击（焦点）特性的元素。

​			例如用其他标签代替A标签。然后在标签身上添加点击事件跳转。

​            2.阻止pc事件。

       ```javascript
document.addEventListener('touchstart',function(ev){
	ev.preventDefault();
});
a.addEventListener('touchstart',function(){
	window.location.href = 'http://www.baidu.com';
});
       ```



#### 1、IOS10下设置meta禁止用户缩放是不可行的。（使用阻止pc事件就可以在IOS10下禁止用户缩放）

```javascript
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> //user-scalable=no无效
```

#### 2、阻止橡皮筋效果。

#### 3、禁止长按选中文字、选中图片、系统默认菜单

#### 4、也阻止了焦点元素的焦点行为(要正常使用：ev.stopPropagation()阻止冒泡)

