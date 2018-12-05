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



