##### 控制器中间件可以在你操作时判断你是否已经登录，没有登录将会跳转到登录界面

```
Route::get('profile', 'UserController@show')->middleware('auth');
```

```
class UserController extends Controller
{
    /**
     * Instantiate a new controller instance.
     *
     * @return void
     */
    public function __construct()
    {
        $this->middleware('auth');

        $this->middleware('log')->only('index');

        $this->middleware('subscribed')->except('store');
    }
}
```

##### 错误提示解决方法

```
错误提示： InvalidArgumentException Route [login] not defined.
解决方法：路由添加：Auth::routes();

错误提示：InvalidArgumentException View [auth.login] not found.
解决方法：创建 auth/login.blade.php
```



