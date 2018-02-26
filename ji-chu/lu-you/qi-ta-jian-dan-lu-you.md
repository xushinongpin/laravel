# 简单的路由【routes/web.php】

添加/foo的访问路径，地址直接访问即可查看'HelloWorld'的返回结果

```
Route::get('foo',function(){
     return 'Hello World';
});
```

**使用SQLite数据库的创建方法【建议使用mysql，**SQLite致力于为单个应用程序和设备提供本地数据存储，具体作用请浏览[官方解析](https://www.sqlite.org/whentouse.html)】

①touchdatabase/database.sqlite

②修改.env

```
DB_CONNECTION=sqlite

DB_DATABASE=/absolute/path/to/database.sqlite
```

### 301重定向 ：**从/here这个地址跳转到/there这个地址**

```
 Route::redirect('/here', '/there', 301);
```

### 

### **只需要视图不需要控制器可以使用**

```
Route::view('/welcome','welcome');
Route::view('/welcome','welcome',['name'=>'test']);//其中在视图中可以打印传来的值  {{ $name}}
```

##### //可以获取url传来的单个参数

```
Route::get('user/{id}',function($id){
    return view('test/csrf',['name' => 'User'.$id]);
});
```

##### //传递多个参数

```
Route::get('posts/{post}/comments/{comment}',function($postId,$commentId){
    return view('test/csrf',['name' => 'postId'.$postId.'-commentId'.$commentId]);
});
```

##### //传递可有可无的参数

```
Route::get('test/{name?}',function($name = 'John'){
    return time().'-'.$name;
});
```

##### //where方法-正则过滤传递的参数

```
Route::get('user/{id}',function($id){
     return view('test/csrf',['name' => 'User'.$id]);
})->where('id','[0-9]+');
```

```
Route::get('posts/{post}/comments/{comment}',function($postId,$commentId){
    return view('test/csrf',['name' => 'postId'.$postId.'-commentId'.$commentId]);
})->where(['post'=>'[0-9]+','comment'=>'[A-Za-z]+']);
```

##### //定义所有路由遵循这个规则，则在 /app/Providers/RouteServiceProvider.php 下修改 boot 的方法

比如：

```
public function boot()
{
  //
  Route::pattern('id', '[0-9]+');//新添加的规则
  parent::boot();
 }
    
//路由配置
Route::get('test/{id}',function($id){
	return view('test/csrf',['name' => 'User-'.$id]);
});
```



