##### 控制器中间件可以在你操作时判断你是否已经登录，没有登录将会跳转到登录界面

```
Route::get('profile', 'UserController@show')->middleware('auth');
```

控制器的里面

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



