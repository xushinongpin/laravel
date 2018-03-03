先安装

```
composer require symfony/psr-http-message-bridge
composer require zendframework/zend-diactoros
```

一旦你安装了这些库，你可以通过在你的路由封闭或控制器方法中键入请求接口来获得PSR-7请求：

```
用法一：路由中
<?php
/*
|--------------------------------------------------------------------------
| Web Routes
|--------------------------------------------------------------------------
|
| Here is where you can register web routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| contains the "web" middleware group. Now create something great!
|
*/

use Psr\Http\Message\ServerRequestInterface;
Route::get('/', function (ServerRequestInterface $request){
	dd($request->getCookieParams());
	// return view('welcome');
});
备注：具体调用的方法查阅内核-/vendor/psr/http-message/src/ServerRequestInterface.php

用法二：控制器中
<?php

namespace App\Http\Controllers;

use Psr\Http\Message\ServerRequestInterface;
use App\Http\Controllers\Controller;

class UserController extends Controller
{
    public function c(ServerRequestInterface  $request){
        dd($request->getCookieParams());
    }
}
```



