响应实例上的cookie方法允许您轻松地将cookie附加到响应中。例如，您可以使用cookie方法生成一个cookie并将其流畅地附加到响应实例，如下所示：

```
	Route::get('home', function () {
		$content = 1;
		$type = 'text/plain';
		$minutes = 0.1;
		return response($content)
			->header('Content-Type', $type)
			->cookie('name', 'value', $minutes);
	});
```



