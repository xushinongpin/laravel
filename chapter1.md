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

### 

### 301重定向 ： **从 /here 这个地址跳转到 /there 这个地址**

```
 Route::redirect('/here', '/there', 301);
```

### 

### **只需要视图不需要控制器可以使用**

Route::view\('/welcome', 'welcome'\);



Route::view\('/welcome', 'welcome', \['name' =&gt; 'test'\]\);//其中 在视图中可以 {{$name}} 打印传来的值

