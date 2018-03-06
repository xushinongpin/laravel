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

##### ajax\(\)  确定请求是否是AJAX调用的结果

```
        $request->ajax();
        ajax访问返回true，否则返回false
```

##### pjax\(\) 确定请求是否是PJAX调用的结果

```
    $request->pjax();  
    pjax访问返回true，否则返回false

    相关使用资料：https://github.com/defunkt/jquery-pjax
```

##### secure\(\) 确定请求是否通过HTTPS

```
    $request->secure();
    https访问返回true，否则返回false
```

##### ip\(\) 或 ips\(\) 获取客户端IP地址

```
    $request->ip(); //返回单个ip
    $request->ips(); // 返回ip数组
```

##### userAgent\(\) 获取客户端用户代理

```
    $request->userAgent(); // 在客户端headers头可以查到 比如 User-Agent:Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.119 Safari/537.36 则返回 "Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.119 Safari/537.36"
```

##### merge\(array $input\) 将新输入合并到当前请求的输入数组中

```
    $array = array('a'=>'1');
    $request->merge($array); //传输过来的数据里面新添加了 a=1
```

##### replace\(array $input\)  替换当前请求的输入

```
    $array = array('a'=>'1');
    $request->replace($array); //无论传什么来，打印出来的只有$array数组里面的数据
```

##### createFromBase\(SymfonyRequest $request\) 从Symfony实例创建 Illuminate 请求

```
    $request->createFromBase($request);
```

##### function duplicate\(array $query = null, array $request = null, array $attributes = null, array $cookies = null, array $files = null, array $server = null\)  克隆请求并覆盖一些参数

```
    $query  =  array('a'=>'1');
    $attributes =  array('b'=>'1');
    $cookies =  array('c'=>'1');
    $server = array('f'=>'1');
    $request->duplicate($query,null,$attributes,$cookies,null,$server);
```

##### session\(\) 、getSession\(\) 获取与请求关联的session

```
    $request->session();
    $request->getSession();
```

##### setLaravelSession\($session\) 在请求上设置会话实例

```
    $session['text'] = array('abc');
    $request->setLaravelSession($session);
    $request->getSession();
```

##### user\($guard = null\) 获取发出请求的用户

```
    $request->user();
```

##### fingerprint\(\) 获取请求/路由/ IP地址的唯一指纹

```
    $request->fingerprint();
```

##### setJson\($json\) 设置JSON有效载荷的请求

```
    $json = array('1');
    $data =  $request->setJson($json);
```

##### getUserResolver\(\)  获取用户解析器回调

```
    $request->getUserResolver();
```

##### getRouteResolver\(\) 获取路由解析器回调

```
    $request->getRouteResolver();
```

##### toArray\(\)  获取请求的所有输入和文件

```
    $request->toArray();
```

##### offsetExists\($offset\) 确定给定的偏移量是否存在

```
    $request->offsetExists('key'); //带上参数key就返回true，否则 false
```

##### offsetGet\($offset\) 获取给定偏移量的值

```
    $request->offsetGet('key'); //key带上数据，返回就是该数据
```

##### offsetSet\($offset, $value\) 将值设置为给定的偏移量

```
        $request->offsetSet('test','250'); // 给test设置了250
        $request->offsetGet('test');  //打印出为250
```

##### offsetUnset\($offset\) 删除给定偏移量的值

```
        $request->offsetSet('test','250');// 给test设置了250
        $request->offsetUnset('test');// 删除test
        $request->offsetGet('test'); //打印出 null
```

##### \_\_isset\($key\) 检查请求上是否设置了输入元素

```
有

        $request->offsetSet('test','250');
        $request->__isset('test');
        或者传来test
没有

        $request->offsetSet('test','250');
        $request->offsetUnset('test');
        $request->__isset('test');
```

##### \_\_get\($key\) 从请求中获取输入元素

```
$request->__get('key'); //传入key或者自己设置key

```

##### 后续

```
    getInputSource()获取请求的输入源 
    createFrom(self $from, $to = null)根据给定的Laravel请求创建一个新的请求实例 
    json($key = null, $default = null) 获取请求的JSON负载
    filterFiles($files) 过滤给定的文件数组，删除所有空值
    $request->route(); 获取处理请求的路由
    setUserResolver(Closure $callback) 设置用户解析器回调
    setRouteResolver(Closure $callback) 设置路由解析器回调
```



