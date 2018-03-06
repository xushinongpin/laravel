##### 字符串或者数组

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

##### 响应对象

```
    Route::get('home', function () {
        return response('Hello World', 200)
                      ->header('Content-Type', 'text/plain');
    });
```

##### 将标题附加到回复

```
    Route::get('home', function () {
        $content = 1;
        $type = 'text/plain';
        return response($content)
        ->header('Content-Type', $type)
        ->header('X-Header-One', 'fulk')
        ->header('X-Header-Two', 'what');
    });

    或者withHeaders数组形式

    Route::get('home', function () {
        $content = 1;
        $type = 'text/plain';
        return response($content)
        ->withHeaders([
        'Content-Type' => $type,
        'X-Header-One' => 'Header Value',
        'X-Header-Two' => 'Header Value',
        ]);
    });
```

##### 将Cookie附加到回复中

```
    Route::get('home', function () {
        $content = 1;
        $type = 'text/plain';
        $minutes = 0.1;
        return response($content)
            ->header('Content-Type', $type)
            ->cookie('name', 'value', $minutes);
    });
    
    详细参考setcookie ： https://secure.php.net/manual/en/function.setcookie.php
    Route::get('home', function () {
    	$content = 1;
    	$type = 'text/plain';
    	$minutes = 0.1;
    	$path = '/home';
    	$damain = 'laravel56.com';
    	$secure = false;
    	$httpOnly = true;
    	return response($content)
    		->header('Content-Type', $type)
    		->cookie('name', 'value', $minutes,$path,$damain,$secure,$httpOnly);
    });
```



