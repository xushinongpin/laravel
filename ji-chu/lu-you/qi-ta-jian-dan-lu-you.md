# 简单的路由【routes/web.php】

添加/foo的访问路径，地址直接访问即可查看'HelloWorld'的返回结果

Route::get\('foo',function\(\){

```
return 'Hello World';
```

}\);

**使用SQLite数据库的创建方法【建议使用mysql，**SQLite致力于为单个应用程序和设备提供本地数据存储，具体作用请浏览[官方解析](https://www.sqlite.org/whentouse.html)】

①touchdatabase/database.sqlite

②修改.env

```
 DB\_CONNECTION=sqlite

 DB\_DATABASE=/absolute/path/to/database.sqlite
```

### 

### 301重定向 ：**从/here这个地址跳转到/there这个地址**

```
 Route::redirect('/here', '/there', 301);
```

### 

### **只需要视图不需要控制器可以使用**

Route::view\('/welcome','welcome'\);

Route::view\('/welcome','welcome',\['name'=&gt;'test'\]\);//其中在视图中可以打印传来的值  { { $name} } 【括号之间没有空格，本手册不支持，我才使用空格隔开】

Route::get\('user/{id}',function\($id\){

```
return view('test/csrf',['name' => 'User'.$id]);//可以获取url传来的单个参数
```

}\);

Route::get\('posts/{post}/comments/{comment}',function\($postId,$commentId\){

```
return view('test/csrf',['name' => 'postId'.$postId.'-commentId'.$commentId]);
```

//传递多个参数

}\);

