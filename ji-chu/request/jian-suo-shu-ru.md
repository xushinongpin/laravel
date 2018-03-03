您也可以使用all方法以数组形式检索所有输入数据：

```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;

class UserController extends Controller
{
    public function c(Request  $request){
        dd($input = $request->all());
    }
}
```

无论HTTP谓词如何，input 可用于检索用户输入：

```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Http\Controllers\Controller;

class UserController extends Controller
{
    public function c(Request  $request){
        dd($input = $request->input('name'));
    }
}
```



