添加到 routes/web.php

这是旅行者路线将被渲染的地方。您可以根据需要更改 `admin`前缀，或设置任何其他需要的路由配置，例如`middleware`或 domain。

```
Route::group(['prefix' => 'admin'], function () {
    Voyager::routes();
});
```

当创建一个新的BREAD类型并为该BREAD指定一个slug时，您可以从以下链接访问该路线

```
URL/admin/slug-name
```

例如，如果我们有一个产品表，并且我们将slug指定为产品。您现在可以访问以下URL

```
URL/admin/products
```



