**创建默认的数据库**

命令行 去到项目根目录执行下面命令

     php artisan migrate

     添加一条或多条数据尝试查找
     insert into users (`name`,`email`,`password`,`remember_token`,`created_at`,`updated_at`) values ('test','test@qq.com','werwerw','111','2018-02-20 22:45:19','2018-02-20 22:45:19');

**创建控制器【 User控制器 】**

```
 php artisan make:controller Home/UserController

 尝试
<?php

namespace App\Http\Controllers\Home;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\DB;
use App\Http\Controllers\Controller;

class UserController extends Controller
{
    public function index(){
        $users = DB::select('select * from users');
        return $users;
    }
}
```

**添加路由**

```
 Route::get('/user', '\App\Http\Controllers\Home\UserController@index');
```



