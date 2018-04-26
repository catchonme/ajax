### AJAX 封装组件

#### 用法

```javascript
var url = '';
var params = {
  name: ''
}
new Ajax(url, {
  method: 'post',
  data:  params,
  onSuccess: function (transport) {
    var response = transport.responseText || "no response text";
    console.log(response);
  },
  onFailure: function () {
    console.log('Something went wrong')
  }
})
```



#### 原生 `Ajax` 简单封装用法

```javascript
var url = '';
var options = {
  method: 'post',
  data: {name:'jack'}
}

function ajax(url, options) {
  var xhr = new XMLHttpRequest();
  var data = [];
  Object.keys(options.data).forEach(function(value, key) {
    var key = value, values = options.data[value];
    data.push(key +'='+ values);
  })

  var afterData = data.join('&');

  if (options.method.toUpperCase() == 'GET') {
    url = url + '?' + afterData;
    xhr.open('GET', url);
    xhr.send();
  } else {
    xhr.open('POST', url);
    xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
    xhr.send(afterData);
  }
  xhr.onload = function(){
    console.log(xhr.status);
    console.log(xhr.statusText);
    console.log(xhr.responseText);
  }
}

ajax(url, options);
```

