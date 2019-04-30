

## Laravel 有着怎样的版本计划？

| 版本 | 发布日期 | 版本类型 | 维护周期 |
| :--- | :--- | :--- | :--- |
| Laravel 5.1 | 2015 年 6 月 | LTS 长久支持 | Bug 修复 2017 年 6 月份，安全修复 2018 年 6 月份 |
| Laravel 5.2 | 2015 年 12 月 | 一般发行 | 提供 6 个月的 Bug 修复支持，一年的安全修复支持 |
| Laravel 5.3 | 2016 年 8 月 | 一般发行 | 提供 6 个月的 Bug 修复支持，一年的安全修复支持 |
| Laravel 5.4 | 2017 年 1 月 | 一般发行 | 提供 6 个月的 Bug 修复支持，一年的安全修复支持 |
| Laravel 5.5 | 2017 年 8 月 | LTS 长久支持 | Bug 修复 2019 年 8 月份，安全修复 2020 年 8 月份 |
| Laravel 5.6 | 2018 年 2 月 | 一般发行 | 提供 6 个月的 Bug 修复支持，一年的安全修复支持 |
| Laravel 5.7 | 2018 年 8 月 | 一般发行 | 提供 6 个月的 Bug 修复支持，一年的安全修复支持 |

# 该使用享元模式的时候使用享元模式【可能多个同时调用，做个享元模式（池容器）对服务器性能有帮助】

eg:

```
<?php
/**
 * php享元模式
 * copyright (c) http://blog.csdn.net/CleverCode
 *
 */
//外部变化
class User
{
    public $name;
    public function __construct($name)
    {
        $this->name = $name;
    }
    public function getName()
    {
        return $this->name;
    }
}

abstract class WebSite
{
    abstract function myUse(User $user);
}

//具体的网站
class ConWebSite extends WebSite
{
    private $name;
    public function __construct($name)
    {
        $this->name = $name;
    }

    public function getName()
    {
        return $this->name;
    }

    function myUse(User $user)
    {
        echo "网站:".$this->name." 用户:".$user->getName()."<br/>";
    }

}

//工厂
class WebSiteFactory
{
    private $hash = array();
    public function getWebSite($key)
    {
        if(false == isset($this->hash[$key]))
        {
            $this->hash[$key] = new ConWebSite($key);
            echo "来一次<br/>";
        }
        return $this->hash[$key];
    }
}

class Client
{
    public static function main($argv)
    {
        $webSiteFactory = new WebSiteFactory();

        $boke = $webSiteFactory->getWebSite('博客');
        $boke->myUse(new User('张三'));
        $weiBo = $webSiteFactory->getWebSite('微博');
        $weiBo->myUse(new User('王五'));
        $boke2 = $webSiteFactory->getWebSite('新浪');
        $boke2->myUse(new User('李四'));
        $boke2 = $webSiteFactory->getWebSite('新浪');
        $boke2->myUse(new User('六六'));
        $boke2 = $webSiteFactory->getWebSite('新浪');
        $boke2->myUse(new User('七七'));
    }
}
Client::main($argv);
```

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



Laravel 文件夹结构简介

| 文件夹名称 | 简介 |
| :--- | :--- |
| app | 应用程序的业务逻辑代码存放文件夹 |
| app/Console | 存放自定义 Artisan 命令文件 |
| app/Http/Controllers | 存放控制器文件 |
| app/Http/Middleware | 存放「中间件」文件 |
| bootstrap | 框架启动与自动加载设置相关的文件 |
| composer.json | 应用依赖的扩展包 |
| composer.lock | 扩展包列表，确保这个应用的副本使用相同版本的扩展包 |
| config | 应用程序的配置文件 |
| database | 数据库操作相关文件（数据库迁移和数据填充） |
| node\_modules | 存放 NPM 依赖模块 |
| package.json | 应用所需的 NPM 包配置文件 |
| phpunit.xml | 测试工具 PHPUnit 的配置文件 |
| public | 前端控制器和资源相关文件（图片、JavaScript、CSS） |
| readme.md | 项目介绍说明文件 |
| resources | 应用资源 |
| resources/js | 未编译的 JavaScript 代码 |
| resources/sass | 未编译的 SASS 代码 （将会编译为 CSS ） |
| resources/lang | 多语言文件 |
| resources/views | 视图文件 |
| routes/api.php | 用于定义 API 类型的路由 |
| routes/channels.php | 事件转播注册信息 |
| routes/console.php | 用于定义 Artisan 命令 |
| routes/web.php | 用于定义 Web 类型的路由（重点，大部分情况下本书会用到） |
| server.php | 使用 PHP 内置服务器时的 URL 重写（类似于 Apache 的 "mod\_rewrite" ） |
| storage | 编译后的视图、基于会话、文件缓存和其它框架生成的文件 |
| storage/app | 目录可用于存储应用程序使用的任何文件 |
| storage/framework | 目录被用于保存框架生成的文件及缓存 |
| storage/logs | 应用程序的日志文件 |
| tests | 应用测试相关文件 |
| vendor | Composer 依赖模块 |
| webpack.mix.js | Laravel 的前端工作流配置文件 |
| yarn.lock | Yarn 依赖版本锁定文件 |
| .gitignore | 被 Git 所忽略的文件 |
| .env | 环境变量配置文件 |



