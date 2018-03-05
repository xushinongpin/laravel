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

##### segment\($index, $default = null\) 从URI中获取一段（基于1的索引）路径

```
    路径：http://a.com/b/c?key=1
    访问：$request->segment(1,'Spare tire');
    输出："b"
    访问：$request->segment(3,'Spare tire');
    输出："Spare tire"
```

##### segments\(\)  获取请求路径的所有段

```
        $request->segments();
        访问：http://a.com/b/c?key=1
        输出：array:2 [▼
                0 => "b"
                1 => "c"
              ]
```

##### $request-&gt;is\($array\) 确定当前的请求URI是否与模式匹配

```
        $array = array('b/c','c/d');
        $request->is($array);
        访问：http://a.com/b/c
        输出：true
        访问：http://a.com/b/d
        输出：false
```

##### routeIs\(...$patterns\) 确定路由名称是否与给模式匹配

```

```

##### fullUrlIs\(...$patterns\) 确定当前请求URL和查询字符串是否与模式匹配

```

        $array = array('http://a.com/a/b','http://a.com/a/b?c=1');
        $request->fullUrlIs($array);
        访问：http://a.com/a/b?c=1  返回：true
        访问：http://a.com/a/b?d=1  返回false
```

##### 1



