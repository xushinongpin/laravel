如果您需要将其他路由添加到超出默认资源路由集的资源控制器，则应在调用Route :: resource之前定义这些路由;否则，资源方法定义的路由可能会无意中优先于您的补充路由：

例如：

```
正确写法
    Route::get('photos/popular', 'PhotoController@method');
    Route::resource('photos', 'PhotoController');
错误写法
    Route::resource('photos', 'PhotoController');
    Route::get('photos/popular', 'PhotoController@method');
    Route::resource('photos', 'PhotoController');
```



