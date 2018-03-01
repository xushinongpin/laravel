```
修改文件  /app/Providers/RouteServiceProvider.php

    public function boot()
    {
        //
        Route::resourceVerbs([
            'create' => 'crear',
            'edit' => 'editar',
        ]);
        parent::boot();
    }

    路由配置
    Route::resource('fotos', 'PhotoController');

    访问路径
    /fotos/crear
    /fotos/{foto}/editar
```



