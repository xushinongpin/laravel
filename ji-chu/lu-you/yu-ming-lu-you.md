配置子域名路由

```
Route::group(array('domain'=>'{account}.21cn.app'),function (){
    Route::get('/',function ($account){
        dd($account);
    });
});
```



