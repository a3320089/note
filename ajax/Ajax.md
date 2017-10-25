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



#### get方式（安全性不是太高的，体积较小的）：

​            通过地址栏进行数据的传输。.php?user=leo&password=123456

​            ?user=leo&password=12345（open('get',url+字段拼接)）

​            相对不安全

​            体积较小，具体能传输多少，跟浏览器限制有关系

​            在写中文的时候，IE下会把中文转成URI编码，会引起报错。

​            通过encodeURI(转一下);

​            

#### post（跟用户信息相关的、较大体积的）

​            服务器进行传输(拼接的字段要在send中)

​            理论上来说是没有大小限制的（后端会做限制）

​            相对就安全一些

​            在send前加请求头

​            ajax.setRequestHeader('Content-Type','application/x-www-form-urlencoded');





## ajax的封装

   ```javascript
function ajax(json) {
    var setting = {
        url: '',
        method: 'get',
        data: {},
        dataType: 'string',
        success: function() {},
        error: function() {}
    }

    if (json) {
        for (var attr in json) {
            setting[attr] = json[attr];
        }
        var arr = [];
        for (var attr in setting.data) {
            arr.push(attr + '=' + setting.data[attr]);
        }
        arr.join("&");
    }
    var xhr = null;
    if (window.XMLHttpRequest) {
        xhr = new XMLHttpRequest;
    } else {
        xhr = new ActiveXObject("Mircosoft.XMLHTTP");
    }


    if (setting.method == 'get') {
        xhr.open(setting.method, setting.url + '?' + arr, true);
        xhr.send();
    } else {
        xhr.open(setting.method, setting.url);
        xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
        xhr.send(arr);
    }

    xhr.onreadystatechange = function() {

        if (xhr.readyState == 4) {
            if (xhr.status >= 200 && xhr.status <= 207 || xhr.status == 304) {

                if (setting.dataType == "json") {
                    setting.success(JSON.parse(xhr.responseText));
                } else if (setting.dataType == "xml") {
                    setting.success(xhr.responseXML);
                } else if (setting.dataType == "string") {
                    setting.success(xhr.responseText);
                } else {
                    alert("请检查配置参数")
                }
            } else {
                setting.error("error:" + xhr.status);
            }
        }


    };

}
   ```

