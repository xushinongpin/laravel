创建User控制器

```
php artisan make:controller UserController
```

默认查找某用户的所有信息的方法

```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\User;
use App\Http\Controllers\Controller;

class UserController extends Controller
{
    /**
     * Show the profile for the given user.
     *
     * @param  int  $id
     * @return Response
     */
    public function show($id)
    {
	return view('user.profile', ['user' => User::findOrFail($id)]);
    }
}

```

添加路由

```
Route::get('user/{id}', 'UserController@show');
```

访问地址： user/1 【 没有用户会报404等错误，可以自己添加数据进去测试 】

