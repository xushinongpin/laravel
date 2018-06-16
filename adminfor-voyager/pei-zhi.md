在config/voyager.php的配置文件

```
voyager.php
 <?php

'user' => [
    'add_default_role_on_register' => true,//指定是否要将默认角色添加到创建的任何新用户。
    'default_role'                 => 'user',//您还可以指定用户的default_role
    'admin_permission'             => 'browse_admin',//查看管理仪表板所需的权限
    'namespace'                    => App\User::class,//您的应用用户类的名称空间
    'redirect'                     => '/admin'//用户登录后重定向路径
],

'controllers' => [
    'namespace' => 'TCG\\Voyager\\Http\\Controllers',//指定Voyager的默认控制器名称空间
],
注：只想覆盖单个控制器，则可以考虑在注册方法中将以下代码片段添加到AppServiceProvider类中。
    app/Providers/AppServiceProvider.php
        注册
        $this->app->bind(VoyagerBreadController::class, MyBreadController::class);

```



