请记住，大多数响应方法都是可链接的，从而可以流畅地构建响应实例。例如，您可以使用header方法在将响应发回给用户之前将一系列标题添加到响应中

```
 Route::get('home', function () {
     $content = 1;
     $type = 'text/plain';
     return response($content)
             ->header('Content-Type', $type)
             ->header('X-Header-One', 'fulk')
             ->header('X-Header-Two', 'what');
 });
```



