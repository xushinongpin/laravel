# laravel5.6个人学习笔记

学无止境

配置文件修改：php.ini 里面 disable\_functions = passthru,...... 中的passthru 去掉

【php artisan serve 提示 （ErrorException  : passthru\(\) has been disabled for security reasons.....）】

#### Apache

      .htaccess

     Options +FollowSymLinks

     RewriteEngine On



     RewriteCond %{REQUEST\_FILENAME} !-d

     RewriteCond %{REQUEST\_FILENAME} !-f

     RewriteRule ^ index.php \[L\]

#### Nginx

     location / {

         try\_files $uri $uri/ /index.php?$query\_string;

     }

