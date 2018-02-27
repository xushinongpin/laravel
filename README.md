# laravel5.6个人学习笔记

学无止境

配置文件修改：php.ini 里面 disable\_functions = passthru,...... 中的passthru 去掉

【php artisan serve 提示 （ErrorException  : passthru\(\) has been disabled for security reasons.....）】

安装 composer create-project --prefer-dist laravel/laravel blog "5.6.\*" 【  laravel5.6 需要 php 需要7.2或以上 】

#### Apache

```
.htaccess

Options +FollowSymLinks

RewriteEngine On



RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_FILENAME} !-f

RewriteRule ^ index.php [L]
```

#### Nginx

```
location / {

     try_files $uri $uri/ /index.php?$query_string;

 }
```

地址解析要解析到 /public 该目录。该public目录包含文件，该文件是进入应用程序并配置自动加载的所有请求的入口点。

storage目录：权限要分配为777，不然会写缓存日志会失败导致报错 【 修改方法：chmod 777 storage -R 】

