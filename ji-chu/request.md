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

##### root\(\) 获取跟url

```
$request->root(); //http://a.com
```

##### url\(\) 获取请求url（无查询字符串）

```
$request->url(); // http://a.com/b/c
```

##### fullUrl\(\) 获取请求完整的url

```
$request->fullUrl(); // http://a.com/b/c?d=e
```

##### fullUrlWithQuery\($array\)  往url追加参数

```
$array = array('b'=>'c','d'=>'e');
$data = $request->fullUrlWithQuery($array);

输出："http://laravel56.com/a/b?b=c&d=e"
```

##### path\(\) 获取当前路径信息

```
$request->path();

访问：http://a.com/b/c?key=1
输出："b/c"
```

##### decodedPath\(\) 获取请求的当前解码路径信息

```
$request->decodedPath();

访问：http://a.com/b/c?key=1
输出："b/c"
```

##### segment\($index, $default = null\) 从URI中获取一段（基于1的索引）

```
路径：http://a.com/b/c?key=1
访问：$request->segment(1,'Spare tire');
输出："b"
访问：$request->segment(3,'Spare tire');
输出："Spare tire"

```



