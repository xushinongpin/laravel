##### 资源控制器 【 php artisan make:controller PhotoController --resource  】

```
路由
写法一：
Route::resource('photos', 'PhotoController');
只允许哪几个方法使用资源路由
Route::resource('photos', 'PhotoController', ['only' => [
    'index', 'show'
]]);
处了哪几个方法之外可以使用资源路由
Route::resource('photos', 'PhotoController', ['except' => [
    'create', 'store', 'update', 'destroy'
]]);
apiResource 会自动排除 create 和edit 两个方法
Route::apiResource('photos', 'PhotoController');
写法二：
还可以用数组形式
Route::resources([
'photos' => 'PhotoController',
'posts' => 'PostController'
]);
//官方 'only' => ['index', 'show', 'store', 'update', 'destroy'], 具体需要亲测
Route::apiResources([
    'photos' => 'PhotoController',
    'posts' => 'PostController'
]);

控制器
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

访问
/photos 【默认指向index 访问 /photos/index 是无效的 】
/photos/create 【 指向create方法 】
```

#### Actions Handled By Resource Controller

| Verb | URI | Action | Route Name |
| :--- | :--- | :--- | :--- |
| GET | `/photos` | index | photos.index |
| GET | `/photos/create` | create | photos.create |
| POST | `/photos` | store | photos.store |
| GET | `/photos/{photo}` | show | photos.show |
| GET | `/photos/{photo}/edit` | edit | photos.edit |
| PUT/PATCH | `/photos/{photo}` | update | photos.update |
| DELETE | `/photos/{photo}` | destroy | photos.destroy |



