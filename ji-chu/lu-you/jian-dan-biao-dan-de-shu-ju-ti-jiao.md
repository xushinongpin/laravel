### 在控制器添加两个方法，一个用于显示，一个用于提交获取数据【 没有这个控制器自己创建 php artisan make:controller Home/TestController】

```
<?php
namespace App\Http\Controllers\Home;
use Illuminate\Http\Request;
use App\Http\Controllers\Controller;
class TestController extends Controller
{
public function csrf(){

    return view('test/csrf');

}



public function tocsrf(Request $request){

    var_dump($request['text']);

    dd($request);

}
}
```

### **创建模板【在/resources/views/ 里面创建test 目录 并在 test创建 csrf.blade.php 文件】**

**input提交csrf**

```
方法一：
<!DOCTYPE html>
<html>
<head>
<title>test csrf submitted</title>
</head>
<body>
<form method="POST" action="/csrf">

    {{csrf_field()}}

    <input type="text" name="text" value="text">

    <input type="submit" value="submit">

</form>
</body>
</html>

方法二：
<!DOCTYPE html>
<html>
<head>
<title>test csrf submitted</title>
</head>
<body>
<form method="POST" action="/csrf">

    @csrf

    <input type="text" name="text" value="text">

    <input type="submit" value="submit">

</form>
</body>
</html>
```

### **添加路由**

```
Route::get('/csrf','\App\Http\Controllers\Home\TestController@csrf');
Route::post('/csrf','\App\Http\Controllers\Home\TestController@tocsrf');
```

访问 /csrf 尝试提交测试





表单提交需要的csrf验证，如果在某情况下不需要csrf的验证，那么就需要另外的授权了

```
打开 /app/Http/Middleware/VerifyCsrfToken.php 添加到 $except，
比如：

    protected $except = [
        'a',
        'b',
    ];
```









