路径方法返回请求的路径信息。

```
$uri = $request->path();
```

如果路由是

```
Route::get('/a/b','UserController@c');
```

则可以打印出路径 /a/b

备注

前提是控制器要引入

```
use Illuminate\Http\Request;
```

request可以这样传入

```

    public function c(Request $request){
        dd($request->path());
    }
```

其中 dd 是 dump and die

