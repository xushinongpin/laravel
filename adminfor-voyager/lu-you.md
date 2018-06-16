添加到 routes/web.php

这是旅行者路线将被渲染的地方。您可以根据需要更改 `admin `前缀，或设置任何其他需要的路由配置，例如`middleware`或 domain。

```
Route::group(['prefix' => 'admin'], function () {
    Voyager::routes();
});
```



