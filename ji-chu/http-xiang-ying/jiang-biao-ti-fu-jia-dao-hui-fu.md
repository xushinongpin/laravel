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

或者，您可以使用withHeaders方法指定要添加到响应中的标题数组

```

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



