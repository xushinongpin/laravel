重定向到控制器的同时必须已经有访问该控制器的请求方法

```

	Route::get('/home', 'UserController@index');
	
	Route::get('/redirect',function(){
		return redirect()->action('UserController@index');
	});
```



