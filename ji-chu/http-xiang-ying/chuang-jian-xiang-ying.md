字符串或者数组

```
字符串
        Route::get('/', function () {
        return 'Hello World';
    });
    
数组
    Route::get('/', function () {
        return [1, 2, 3];
    });
```

响应对象

```
    Route::get('home', function () {
        return response('Hello World', 200)
                      ->header('Content-Type', 'text/plain');
    });
```



