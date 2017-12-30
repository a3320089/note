# 移动端meta设置

```javascript
<meta name="viewport" content="width=device-width,user-scalable=no"/>
  <script>
  (function(){
  var html = document.documentElement;
  var htmlWidth = html.getBoundingClientRect().width;
  html.style.fontSize = htmlWidth/15 +"px";
})()
</script>
```

