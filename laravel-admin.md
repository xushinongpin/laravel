命令

```
composer require encore/laravel-admin  //下载
php artisan vendor:publish --provider="Encore\Admin\AdminServiceProvider"   //发布资产和配置
php artisan admin:install   //安装
```

目录结构

```
app/Admin
├── Controllers  //存储所有控制器
│   ├── ExampleController.php  //控制器示例
│   └── HomeController.php   //用于处理admin的home请求
├── bootstrap.php  //laravel-admin的bootstrapper
└── routes.php  //定义路线
```

前端静态文件位于 /public/packages/admin

## **安装扩展**

① laravel-admin-ext/helpers

```
$ composer require laravel-admin-ext/helpers

$ php artisan admin:import helpers
```

② laravel-admin-ext/log-viewer

```
$ composer require laravel-admin-ext/log-viewer -vvv

$ php artisan admin:import log-viewer
```

③ laravel-admin-ext/backup

```
$ composer require laravel-admin-ext/backup -vvv

$ php artisan admin:import backup
```

④ laravel-admin-ext/config

```
$ composer require laravel-admin-ext/config

$ php artisan migrate

修改
app/Providers/AppServiceProvider.php
    <?php

    namespace App\Providers;

    use Encore\Admin\Config\Config;
    use Illuminate\Support\ServiceProvider;

    class AppServiceProvider extends ServiceProvider
    {
        public function boot()
        {
            Config::load();
        }
    }

$  php artisan admin:import config
```

⑤ laravel-admin-ext/api-tester

```
$ composer require laravel-admin-ext/api-tester -vvv

$ php artisan vendor:publish --tag=api-tester

$ php artisan admin:import api-tester

config/admin.php
    'extensions' => [

        'api-tester' => [

            // route prefix for APIs
            'prefix' => 'api',

            // auth guard for api
            'guard'  => 'api',

            // If you are not using the default user model as the authentication model, set it up
            'user_retriever' => function ($id) {
                return \App\User::find($id);
            },
        ]
    ]
```

⑥ laravel-admin-ext/media-manager

    $ composer require laravel-admin-ext/media-manager -vvv

    $ php artisan admin:import media-manager

    config/admin.php
        'extensions' => [
            'media-manager' => [
                // Select a local disk that you configured in `config/filesystem.php`
                'disk' => 'public'
            ],
        ],

⑦ laravel-admin-ext/scheduling

```
$ composer require laravel-admin-ext/scheduling
$ php artisan admin:import scheduling

app/Console/Kernel.php
    class Kernel extends ConsoleKernel
    {
        protected function schedule(Schedule $schedule)
        {
            $schedule->command('inspire')->everyTenMinutes();

            $schedule->command('route:list')->dailyAt('02:00');
        }
    }
```

⑧ laravel-admin-ext/reporter

```
$ composer require laravel-admin-ext/reporter -vvv

$ php artisan vendor:publish --tag=laravel-admin-reporter

$ php artisan migrate --path=vendor/laravel-admin-ext/reporter/database/migrations

$ php artisan admin:import reporter

app/Exceptions/Handler.php
    <?php
        namespace App\Exceptions;
        
        use Encore\Admin\Reporter\Reporter;
        use Exception;
        use Illuminate\Auth\AuthenticationException;
        use Illuminate\Validation\ValidationException;
        use Illuminate\Foundation\Exceptions\Handler as ExceptionHandler;
        
        class Handler extends ExceptionHandler
        {
            ...
        
            public function report(Exception $exception)
            {
                if ($this->shouldReport($exception)) {
                    Reporter::report($exception);
                }
        
        //        parent::report($exception);
            }
            
            ...
        
        }
```



