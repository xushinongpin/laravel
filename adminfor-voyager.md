先创建laravel程序

```
composer create-project --prefer-dist laravel/laravel blog
```

执行命令创建包含包

```
$ composer require tcg/voyager
```

创建好数据库后修改配置文件

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



