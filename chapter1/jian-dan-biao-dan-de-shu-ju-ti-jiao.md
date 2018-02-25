在控制器添加两个方法，一个用于显示，一个用于提交获取数据【 没有这个控制器自己创建 php artisan make:controller Home/TestController】

&lt;?php

namespace App\Http\Controllers\Home;

use Illuminate\Http\Request;

use App\Http\Controllers\Controller;

class TestController extends Controller

{

```php
public function csrf(){

    return view('test/csrf');

}



public function tocsrf(Request $request){

    var_dump($request['text']);

    dd($request);

}
```

}

创建模板【在/resources/views/ 里面创建test 目录 并在 test创建 csrf.blade.php 文件】

方法一：input提交csrf

&lt;!DOCTYPE html&gt;

&lt;html&gt;

&lt;head&gt;

```
<title>test csrf submitted</title>
```

&lt;/head&gt;

&lt;body&gt;

```
<form method="POST" action="/csrf">

    {{csrf_field()}}

    <input type="text" name="text" value="text">

    <input type="submit" value="submit">

</form>
```

&lt;/body&gt;

&lt;/html&gt;

方法二：协议头填写csrf

&lt;!DOCTYPE html&gt;

&lt;html&gt;

&lt;head&gt;

```
<title>test csrf submitted</title>

<meta name="csrf-token" content="{{ csrf_token() }}">
```

&lt;/head&gt;

&lt;body&gt;

```
<form method="POST" action="/csrf">

    <input type="text" name="text" value="text">

    <input type="submit" value="submit">

</form>
```

&lt;/body&gt;

&lt;/html&gt;

