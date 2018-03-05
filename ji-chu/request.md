##### capture\(\) 从服务器变量创建一个新的 Illuminate HTTP 请求

```
可以使用 $request->capture();打印出来有什么东西，里面看到的都可以单独打印出来，比如
$request->capture()->server();
$request->capture()->cookie();
$request->capture()->header();
$request->capture()->file();
```



