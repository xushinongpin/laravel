##### capture\(\) 从服务器变量创建一个新的 Illuminate HTTP 请求

```
可以使用 $request->capture();打印出来有什么东西，里面看到的都可以单独打印出来，比如
$request->capture()->server();
$request->capture()->cookie();
$request->capture()->header();
```

##### instance\(\) 返回请求实例

```
$request->instance();
```

##### method\(\)  获取请求方法

```
$request->method();//打印出 GET 或者 POST 等 该操作的请求方法
```

获取跟url

```
$request->root(); //http://a.com
```

获取请求url（无查询字符串）

```
$request->url(); // http://a.com/b/c
```



