##### 创建User控制器

```
php artisan make:controller UserController
备注：php artisan make:controller UserController --resource 将会创建 index,create,store,show,edit,update,destroy 包含每种可用资源操作的方法
```

##### 默认查找某用户的所有信息的方法

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

##### 添加路由 备注：控制器指定只需要指定 App\Http\Controllers 之后的路径就行了

```
Route::get('user/{id}', 'UserController@show');
```

##### 访问地址： user/1 【 没有用户会报404等错误，可以自己添加数据进去测试 】

### 

### 额外知识

##### 如果该控制器只有一个操作，就可以使用 \_\_invoke

```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\User;
use App\Http\Controllers\Controller;

class ShowProfile extends Controller
{
    /**
     * Show the profile for the given user.
     *
     * @param  int  $id
     * @return Response
     */
    public function __invoke($id)
    {
        return view('user.profile', ['user' => User::findOrFail($id)]);
    }
}

Route::get('user/{id}', 'ShowProfileController');
```



