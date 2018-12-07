主要操作命令等

```
composer require tcg/voyager
 .env
  APP_URL=http://localhost
  DB_HOST=localhost
  DB_DATABASE=homestead
  DB_USERNAME=homestead
  DB_PASSWORD=secret
安装
  php artisan voyager:install 【php artisan voyager:install --with-dummy 需要有模拟数据使用这个】

默认账号密码：
  email: admin@admin.com
  password: password
  
php artisan voyager:admin your@email.com【php artisan voyager:admin your@email.com --create】

发布资产
  php artisan vendor:publish --provider=VoyagerServiceProvider
  php artisan vendor:publish --provider=ImageServiceProviderLaravel5
```

①先创建laravel程序

```
composer create-project --prefer-dist laravel/laravel blog
```

②执行命令创建包含包

```
$ composer require tcg/voyager
```

③创建好数据库后修改配置文件

```
.env
 APP_URL=http://localhost
DB_HOST=localhost
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret
```

注意：如果您使用Laravel 5.4进行安装，则需要手动添加服务提供程序。否则，如果您使用的是5.5版本，那么会自动发生包自动发现。

```
To add the Voyager Service Provider open up your application config/app.php file and add TCG\Voyager\VoyagerServiceProvider::class, in the providers array like so:

config/app.php
 <?php

'providers' => [
    // Laravel Framework Service Providers...
    //...

    // Package Service Providers
    TCG\Voyager\VoyagerServiceProvider::class,
    // ...

    // Application Service Providers
    // ...
],
```

④

1、安装没有虚拟数据的

```
php artisan voyager:install
```

2、安装有虚拟数据的

```
php artisan voyager:install --with-dummy
```

报错

```
exec() has been disabled for security reasons
解决方法： 去掉php.ini里面disable_functions的exec
disable_functions = popen,passthru,exec,system,chroot,chgrp,chown,shell_exec,ini_alter,ini_alter,ini_restore,dl,openlog,syslog,readlink,symlink,popepassthru
```

访问不了就添加伪静态

```
location / {
     try_files $uri $uri/ /index.php?$query_string;
 }
```

⑤

访问后台地址：/admin

```
装了虚拟数据的登陆账号密码：
email: admin@admin.com
password: password
```

如果您没有与虚拟用户同行，您可能希望将管理员权限分配给现有用户。 这可以通过运行以下命令轻松完成：

```
php artisan voyager:admin your@email.com
```

如果你想创建一个新的管理员用户，你可以传递--create标志，如下所示：

```
php artisan voyager:admin your@email.com --create
```

您应该做的第一件事是发布Voyager附带的资产

```
php artisan vendor:publish --provider=VoyagerServiceProvider
php artisan vendor:publish --provider=ImageServiceProviderLaravel5
```



