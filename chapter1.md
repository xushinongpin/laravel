# 简单的路由【 routes/web.php 】

添加 /foo 的访问路径，地址直接访问即可查看'Hello World'的返回结果

Route::get\('foo', function \(\) {

```
return 'Hello World';
```

}\);

**使用SQLite数据库的创建方法【 建议使用mysql，**SQLite致力于为单个应用程序和设备提供本地数据存储，具体作用请浏览 [官方解析](https://www.sqlite.org/whentouse.html)】

①touch database/database.sqlite

②修改.env

```
 DB\_CONNECTION=sqlite

 DB\_DATABASE=/absolute/path/to/database.sqlite
```

## **实现第一个读取数据库信息的方法**

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



