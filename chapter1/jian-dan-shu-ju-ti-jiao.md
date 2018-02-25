在控制器**添加两个方法，一个用于显示，一个用于提交获取数据**

&lt;?php

namespace App\Http\Controllers\Home;

use Illuminate\Http\Request;

use Illuminate\Support\Facades\DB;

use App\Http\Controllers\Controller;

class UserController extends Controller

{

```
public function csrf\(\){

    return view\('test/csrf'\);

}



public function tocsrf\(Request $request\){

    dd\($request\);

}
```

}

