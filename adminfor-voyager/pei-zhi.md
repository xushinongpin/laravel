在config/voyager.php的配置文件

```
'user' => [
    'add_default_role_on_register' => true,//指定是否要将默认角色添加到创建的任何新用户。
    'default_role'                 => 'user',//您还可以指定用户的default_role
    'admin_permission'             => 'browse_admin',//查看管理仪表板所需的权限
    'namespace'                    => App\User::class,//您的应用用户类的名称空间
    'redirect'                     => '/admin'//用户登录后重定向路径
],
```

指定Voyager的默认控制器名称空间

```
'controllers' => [
    'namespace' => 'TCG\\Voyager\\Http\\Controllers',//
],
注：只想覆盖单个控制器，则可以考虑在注册方法中将以下代码片段添加到AppServiceProvider类中。
    app/Providers/AppServiceProvider.php
        注册
        $this->app->bind(VoyagerBreadController::class, MyBreadController::class);
```

指定模型的名称空间或位置。这是在从Voyager的数据库部分创建模型时使用的。如果未定义，则将使用默认的应用程序名称空间

```
'models' => [
    //'namespace' => 'App\\', //
],
```

希望指定不同的资产路径【如果您的网站位于子文件夹中，则可能需要将该目录包含到路径的开头。如果您希望复制已发布的资产并自定义您的资产，也可以使用此功能。】

```
'assets_path' => '/vendor/tcg/voyager/assets',//
```

默认情况下，Voyager将使用公共本地存储。你还可以在config/filesystems.php里面使用任何驱动。这意味着您可以使用S3，Google云端存储或任何其他文件存储系统。

```
'storage' => [
    'disk' => 'public',//
],
```

您可能希望在Voyager数据库部分隐藏一些数据库表。在数据库配置中，您可以选择要隐藏哪些表。

```
'database' => [
    'tables' => [
        'hidden' => ['migrations', 'data_rows', 'data_types', 'menu_items', 'password_resets', 'permission_role', 'settings'],
    ],
],
```

指定访问Voyager的备用前缀。而不是访问/admin，也许你想访问/backend Voyager管理员

```
'prefix' => 'admin',
```

可以指定是否要启用多语言。然后，您可以指定默认语言和所有支持语言（语言环境）【al,ar,cz,de,en,es,fa,fi,fr,gl,id,it,nl,pl,pt,pt\_br,ro,ru,sv,tr,uk,zh\_CN】

```
'multilingual' => [
    'enabled' => false,
    'default' => 'en',
    'locales' => [
        'en',
        //'pt',
    ],
],
```

在 dashboard 配置中，您可以添加navbar\_items，使data\_tables响应并管理仪表板**widgets**

```
'dashboard' => [
    'navbar_items' => [//通过包括'route'，'icon_class'和'target_blank'，在主用户navbar下拉菜单中包含新路线。
        'Profile' => [
            'route'         => 'voyager.profile',
            'classes'       => 'class-full-of-rum',
            'icon_class'    => 'voyager-person',
        ],
        'Home' => [
            'route'         => '/',
            'icon_class'    => 'voyager-home',
            'target_blank'  => true,
        ],
        'Logout' => [
            'route'      => 'voyager.logout',
            'icon_class' => 'voyager-power',
        ],
    ],
    'widgets' => [//在这里，您可以管理仪表板上的小部件。您可以通过查看tcg/voyager/src/Widgets中的当前窗口小部件来查看示例窗口小部件类
        'TCG\\Voyager\\Widgets\\UserDimmer',
        'TCG\\Voyager\\Widgets\\PostDimmer',
        'TCG\\Voyager\\Widgets\\PageDimmer',
    ],
],
//data_tables  如果您将'responsive'设置为true，则数据表将作出响应。
```

Voyager管理仪表板的默认主要颜色是淡蓝色。您可以通过更改此配置的值来更改该原色。

```
'primary_color' => '#22A7F0',
```



