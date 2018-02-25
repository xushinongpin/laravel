**创建默认的数据库**

去到项目根目录执行下面命令

```
 php artisan migrate
```

**创建控制器【 User控制器 】**

```
 php artisan make:controller Home/UserController
```

**添加路由**

```
 Route::get('/user', '\App\Http\Controllers\Home\UserController@index');
```



