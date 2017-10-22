# Ajax



一个简单的ajax

```javascript
  var xhr = null;
      if (window.XMLHttpRequest) {
          xhr= new XMLHttpRequest();
      }else{
          xhr = new ActiveXObject('Microsoft.XMLHTTP');
      }

      xhr.open('get','1.txt',true);
      xhr.send();

      xhr.onreadystatechange =function(){
          if(xhr.readyState == 4){
              if(xhr.status == 200){
                    alert(xhr.responseText);
              }else{
                  alert("error："+xhr.status)
              }
          }
      }
```

