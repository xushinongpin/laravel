

重定向响应是Illuminate \ Http \ RedirectResponse类的实例，并包含将用户重定向到另一个URL所需的正确头。

```

	Route::get('/', function () {
		return redirect('home');
	});
	Route::get('home', function () {
		return "End of the World everywhere, and now, students are you, death is your ghost ";
	});
```



