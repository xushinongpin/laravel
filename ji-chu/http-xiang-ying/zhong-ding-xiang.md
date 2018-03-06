重定向响应是Illuminate  Http  RedirectResponse类的实例，并包含将用户重定向到另一个URL所需的正确头。

```
    Route::get('/', function () {
        return redirect('home');
    });
    Route::get('home', function () {
        return "End of the World everywhere, and now, students are you, death is your ghost ";
    });
```

有时您可能希望将用户重定向到他们以前的位置，例如提交的表单无效时

```
路由
	Route::post('/home', function () {
		return back()->withInput();
	});
页面
	<!DOCTYPE html>
	<html>
		<head>
			<title>user</title>
			<meta name="csrf-token" content="{{ csrf_token() }}">
		</head>
		<body>
			<form action="/home" method="post">
				@csrf
				<input type="text" name="a" value="1">
				<input type="submit" value="submit">
			</form>
		</body>
	</html>
```



