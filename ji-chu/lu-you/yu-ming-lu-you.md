配置子域名路由

```
Route::group(array('domain'=>'{account}.21cn.app'),function (){
    Route::get('/',function ($account){
        dd($account);
    });
});

----------------------------------------------
define('DOMAIN','21cn.app');
//定义泛指域名跳转
Route::group(array('domain'=>'{account}.'.DOMAIN),function (){
    Route::get('/',function ($account){
        return redirect('http://'.DOMAIN.'?shopname='.$account,302);
        //dd($account);
    });
});
```



