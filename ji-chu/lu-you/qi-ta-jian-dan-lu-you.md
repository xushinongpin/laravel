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

##### 同时支持post与get提交的路由

```
Route::match(['get','post'],'run', function () {
    return 'get and post';
});
```

资源控制器

```
Route::resource('photos', 'PhotoController');

<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class PhotoController extends Controller
{
    /**
     * Display a listing of the resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function index()
    {
        return 'index';
    }

    /**
     * Show the form for creating a new resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function create()
    {
        return 'create';
    }

    /**
     * Store a newly created resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @return \Illuminate\Http\Response
     */
    public function store(Request $request)
    {
        //
    }

    /**
     * Display the specified resource.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function show($id)
    {
        //
    }

    /**
     * Show the form for editing the specified resource.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function edit($id)
    {
        //
    }

    /**
     * Update the specified resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function update(Request $request, $id)
    {
        //
    }

    /**
     * Remove the specified resource from storage.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function destroy($id)
    {
        //
    }
}

则可以访问
/photos 【默认指向index】
/photos/create 【 指向create方法 】
```



