**创建默认的数据库**

命令行 去到项目根目录执行下面命令

```
 php artisan migrate

 添加一条或多条数据尝试查找【 命令行或者 】
```

**创建控制器【 User控制器 】**

     php artisan make:controller Home/UserController

     尝试
    <?php

    namespace App\Http\Controllers\Home;

    use Illuminate\Http\Request;
    use Illuminate\Support\Facades\DB;//这个需要添加，用于连接数据库
    use App\Http\Controllers\Controller;

    class UserController extends Controller
    {
        public function index(){
            $time = time();
            $date = date("Y-m-d H:i:s",$time);
            $users = DB::insert("insert into users (`name`,`email`,`password`,`remember_token`,`created_at`,`updated_at`) values ('{$time}','{$time}@qq.com','{$time}','{$time}','{$date}','{$date}');");//随时生成一条数据用于判断会否已写入
            $users = DB::select('select * from users');//查询数据
            return $users;
        }
    }

**添加路由**

```
 Route::get('/user', '\App\Http\Controllers\Home\UserController@index');
```



http://domain/user  你的访问路径访问【 domain是你的访问地址 】



