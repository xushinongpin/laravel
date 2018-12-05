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

⑨ laravel-admin-ext/redis-manager

```
$ composer require laravel-admin-ext/redis-manager

$ php artisan admin:import redis-manager
```

⑩  laravel-admin-ext/wang-editor [wangEditor文档](https://www.kancloud.cn/wangfupeng/wangeditor3/335776) 与 [上传图片](https://www.kancloud.cn/wangfupeng/wangeditor3/335782)

```
composer require laravel-admin-ext/wang-editor
php artisan vendor:publish --tag=laravel-admin-wangEditor

config/admin.php
    'extensions' => [

        'wang-editor' => [

            // 如果要关掉这个扩展，设置为false
            'enable' => true,

            // 编辑器的配置
            'config' => [

            ]
        ]
    ]

编辑器的配置可以到wangEditor文档找到，比如配置上传图片的地址上传图片
    'config' => [
        'uploadImgServer' => '/upload'
    ]

在form表单中使用它：
    $form->editor('content');
```

十一：

```
composer require jxlwqq/quill

php artisan vendor:publish --tag=laravel-admin-quill

config/admin.php
    'extensions' => [
        'quill' => [
            // If the value is set to false, this extension will be disabled
            'enable' => true,
            'config' => [
                'modules' => [
                    'syntax' => true,
                    'toolbar' =>
                        [
                            ['size' => []],
                            ['header' => []],
                            'bold',
                            'italic',
                            'underline',
                            'strike',
                            ['script' => 'super'],
                            ['script' => 'sub'],
                            ['color' => []],
                            ['background' => []],
                            'blockquote',
                            'code-block',
                            ['list' => 'ordered'],
                            ['list' => 'bullet'],
                            ['indent' => '-1'],
                            ['indent' => '+1'],
                            'direction',
                            ['align' => []],
                            'link',
                            'image',
                            'video',
                            'formula',
                            'clean'
                        ],
                ],
                'theme' => 'snow',
                'height' => '200px',
            ]
        ]
    ]

from表单使用：  
    $form->quill('content');
```

十二：  laravel-admin-ext/china-distpicker

```
composer require laravel-admin-ext/china-distpicker
php artisan vendor:publish --tag=laravel-admin-china-distpicker

config/admin.php
    'china-distpicker' => [
            // 如果要关掉这个扩展，设置为false
            'enable' => true,
        ]

form中使用：
    $form->distpicker(['province_id', 'city_id', 'district_id']);
可以设置每个字段的placeholder
    $form->distpicker([
        'province_id' => '省',
        'city_id'     => '市',
        'district_id' => '区'
    ]);
设置label
    $form->distpicker(['province_id', 'city_id', 'district_id'], '请选择区域');
设置自动选择, 可以设置1,2,3 表示自动选择到第几级
    $form->distpicker(['province_id', 'city_id', 'district_id'])->autoselect(1);
表单提交的时候，默认是使用地域名称作为表单值提交，如果你要提交地域编码，使用下面的方法：
    $form->distpicker(['province_id', 'city_id', 'district_id'])->attribute('data-value-type', 'code');
```

十三：  laravel-admin-ext/lock-screen

    composer require laravel-admin-ext/lock-screen

    config/admin.php
        'route' => [
            'prefix' => 'demo',
            'namespace'     => 'App\\Admin\\Controllers',
            // add middleware `admin.lock` into this array.
            'middleware'    => ['web', 'admin', 'admin.lock'],
        ],

十四：  laravel-admin-ext/media-player

```
composer require laravel-admin-ext/media-player
php artisan vendor:publish --tag=laravel-admin-media-player

网页上输出
    // Add a play button to the current field column. After clicking it will open a modal to play the video file.
    $grid->foo()->video();

    // Add an audio player to the current field column
    $grid->foo()->audio();

    // This field will be displayed as a video player
    $show->foo()->video();

    // this field will be displayed as an audio player
    $show->foo()->audio();

    //If the field foo is another path or a file path under another server, you can use the following settings.
    $grid->foo()->video(['server' => 'http:www.foo.com/']);

    //This player feature of this extension is based on mediaelement and can be referenced API and Configuration Add more settings to the player.For example, set the size of the player:
    $grid->foo()->video(['videoWidth' => 720, 'videoHeight' => 480]);
```

十五： laravel-admin-ext/simplemde  [config更多配置](https://github.com/sparksuite/simplemde-markdown-editor#configuration)

```
composer require laravel-admin-ext/simplemde
php artisan vendor:publish --tag=laravel-admin-simplemde

config/admin.php

    'extensions' => [

        'simplemde' => [

            // Set to false if you want to disable this extension
            'enable' => true,

            // If you want to set an alias for the calling method
            //'alias' => 'markdown',

            // Editor configuration
            'config' => [

            ]
        ]
    ]
config配置如： 
    'config' => [
        'autofocus'   => true,
        'placeholder' => 'xxxx',
        ....
    ]

form表单中使用： 
    $form->simplemde('content');
    $form->simplemde('content')->height(500);
    $form->markdown('content');
```

十六：  laravel-admin-ext/file-browser

    composer require laravel-admin-ext/file-browser
    php artisan admin:import media-manager  //发布media-manager的文件(如已发布，可跳过),否则会报错

    config/admin.php
        'extensions' => [
            'media-manager' => [
                // Select a local disk that you configured in `config/filesystem.php`
                'disk' => 'public'
            ],
        ],

    app/Admin/bootstrap.php
        Encore\Admin\Form::extend('media', \Encore\FileBrowser\FileBrowserField::class);

    直接调用就可以了,path选项可以指定目录,否则将使用默认根目录。
        $form->media('ColumnName', 'LabelName')->path('uploads');
        $form->media('ColumnName', 'LabelName')->path('uploads/images');


    本扩展不支持识别目录(即文件夹)，仅识别path设定的一级目录下的所有文件； 2，本扩展默认可多选，字段存为json字符串，模型文件需添加如下修改器：
        public function getImagesAttribute($v)
        {
            return json_decode($v, true);
        }

十七： 身份证验证laravel-admin-ext/id-validator

```
composer require laravel-admin-ext/id-validator
php artisan admin:import id-validator
```

十八：   laravel-admin-ext/ckeditor  [config更多配置](https://ckeditor.com/docs/ckeditor4/latest/guide/)

```
composer require laravel-admin-ext/ckeditor
php artisan vendor:publish --tag=laravel-admin-ckeditor

config/admin.php
    'extensions' => [

        'ckeditor' => [
        
            //Set to false if you want to disable this extension
            'enable' => true,
            
            // Editor configuration
            'config' => [
                
            ]
        ]
    ]
The configuration of the editor can be found in CKEditor Documentation, such as configuration language and height.
    'config' => [
        'lang'   => 'zh-CN',
        'height' => 500,
    ]
```



