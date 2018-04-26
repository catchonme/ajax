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

