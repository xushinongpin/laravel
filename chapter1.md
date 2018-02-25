# 简单的路由【 routes/web.php 】

添加 /foo 的访问路径，地址直接访问即可查看'Hello World'的返回结果

Route::get\('foo', function \(\) {

```
return 'Hello World';
```

}\);

**使用SQLite数据库的创建方法**

①touch database/database.sqlite

②修改.env

     DB\_CONNECTION=sqlite

     DB\_DATABASE=/absolute/path/to/database.sqlite

