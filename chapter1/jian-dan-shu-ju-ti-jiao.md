### 在控制器**添加两个方法，一个用于显示，一个用于提交获取数据【 没有这个控制器自己创建 php artisan make:controller Home/TestController】**

&lt;?php

namespace App\Http\Controllers\Home;

use Illuminate\Http\Request;

use App\Http\Controllers\Controller;

class TestController extends Controller

{

```
public function csrf(){

    return view('test/csrf');

}



public function tocsrf(Request $request){

    dd($request);//dd 是dump and die 的简写

}
```

**}**

### **创建模板【在/resources/views/ 里面创建test 目录 并在 test创建 csrf.blade.php 文件】**

**方法一：input提交csrf**

&lt;!DOCTYPE html&gt;



&lt;html&gt;



&lt;head&gt;



&lt;title&gt;test csrf submitted&lt;/title&gt;

&lt;/head&gt;



&lt;body&gt;



&lt;form method="POST" action="/csrf"&gt;



    {{csrf\_field\(\)}}

//csrf填写方法①



    &lt;input type="text" name="text" value="text"&gt;



    &lt;input type="submit" value="submit"&gt;



&lt;/form&gt;

&lt;/body&gt;



&lt;/html&gt;

**方法二：协议头填写csrf**

&lt;!DOCTYPE html&gt;



&lt;html&gt;



&lt;head&gt;



&lt;title&gt;test csrf submitted&lt;/title&gt;



&lt;meta name="csrf-token" content="{{ csrf\_token\(\) }}"&gt;//csrf填写方法①

&lt;/head&gt;



&lt;body&gt;



&lt;form method="POST" action="/csrf"&gt;



    &lt;input type="text" name="text" value="text"&gt;



    &lt;input type="submit" value="submit"&gt;



&lt;/form&gt;

&lt;/body&gt;



&lt;/html&gt;

