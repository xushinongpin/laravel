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
```



