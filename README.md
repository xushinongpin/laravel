# 该使用享元模式的时候使用享元模式【可能多个同时调用，做个享元模式（池容器）对服务器性能有帮助】

# laravel5.6个人学习笔记

[文档地址](https://laravel.isoso.vip/)

开发工具 [https://www.jetbrains.com/phpstorm/download/\#section=windows](https://www.jetbrains.com/phpstorm/download/#section=windows) 注册破解工具： [http://idea.lanyus.com/](http://idea.lanyus.com/)

破解文件放到 \JetBrains\PhpStorm 2018.1.6\lib目录下

window上 [Composer安装](https://getcomposer.org/Composer-Setup.exe)

nodejs的[npm使用](https://nodejs.org/zh-cn/download/)

开发完之后可以使用性能分析工具[ xhprof](http://php.net/manual/zh/book.xhprof.php) 与网页测试分析意见工具 [谷歌的](https://developers.google.com/speed/pagespeed/insights)

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

