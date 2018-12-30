# 基本操作方法命令

```
env文件
    重新生成app_key    php artisan key:generate
```

①路由的使用

②csrf表单提交保护

③controllers控制器的操作

所有写好的方法都在这里面

/vendor/laravel/framework/src/Illuminate/Support/helpers.php

[简介](https://laravel-china.org/docs/laravel/5.6/structure/1354#introduction)

* [根目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-root-directory)
  * [`app`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-root-app-directory)
  * [`bootstrap`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-bootstrap-directory)
  * [`config`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-config-directory)
  * [`database`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-database-directory)
  * [`public`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-public-directory)
  * [`resources`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-resources-directory)
  * [`routes`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-routes-directory)
  * [`storage`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-storage-directory)
  * [`tests`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-tests-directory)
  * [`vendor`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-vendor-directory)
* [App 目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-app-directory)
  * [`Broadcasting`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-broadcasting-directory)
  * [`Console`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-console-directory)
  * [`Events`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-events-directory)
  * [`Exceptions`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-exceptions-directory)
  * [`Http`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-http-directory)
  * [`Jobs`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-jobs-directory)
  * [`Listeners`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-listeners-directory)
  * [`Mail`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-mail-directory)
  * [`Notifications`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-notifications-directory)
  * [`Policies`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-policies-directory)
  * [`Providers`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-providers-directory)
  * [`Rules`目录](https://laravel-china.org/docs/laravel/5.6/structure/1354#the-rules-directory)

## 简介

默认的 Laravel 应用结构旨在为不同大小的应用提供一个好的起点。当然，你也可以根据自己的喜好整理应用的目录结构。 Laravel 没有严格地限制任何给定的类的位置，只要它们能够被 Composer 自动加载。

#### 为什么没有模型目录？

当开始使用 Laravel 时，许多开发人员都因缺少`Models`目录而感到困惑。然而，缺少这样的目录是故意的。 我们发现「模型」含糊不清，因为对许多不同的人来说有着各自不同的理解。一些开发者把应用的「模型」称为其所有业务逻辑的总体，而另一些人将「模型」称为与关系数据库交互的类。

因此，我们默认把 Eloquernt 的模型放在`app`目录下，并且允许开发者自行选择放置在何处。

## 根目录

#### `App`目录

`App`目录包含应用程序的核心代码。你应用中几乎所有的类都应该放在这里。稍后我们会更深入地了解这个目录的细节。

#### `Bootstrap`目录

`Bootstrap`目录包含引导框架并配置自动加载的文件。该目录还包含了一个 cache 目录，存放着框架生成的用来提升性能的文件，比如路由和服务缓存文件。

#### `Config`目录

`Config`目录，顾名思义，包含应用程序所有的配置文件。我们鼓励你通读这些文件，以便帮助你熟悉所有可用的选项。

#### `Database`目录

`Database`目录包含数据填充和迁移文件。你还可以把它作为 SQLite 数据库存放目录。

#### Public 目录

`public`目录包含了入口文件`index.php`，它是进入应用程序的所有请求的入口点。此目录还包含了一些你的资源文件（如图片、JavaScript 和 CSS）。

#### Resources 目录

`resource`目录包含了视图和未编译的资源文件（如 LESS、SASS 或 JavaScript）。此目录还包含你所有的语言文件。

#### Routes 目录

`routes`目录包含了应用的所有路由定义，Laravel 默认包含了几个路由文件：`web.php`,`api.php`,`console.php`和`channels.php`。

`web.php`文件包含`RouteServiceProvider`放置在`web`中间件组中的路由，它提供会话状态、CSRF 防护和 cookie 加密。如果你的应用不提供无状态的、RESTful 风格的 API，则所有的路由都应该在`web.php`文件中定义。

`api.php`文件包含`RouteServiceProvider`放置在`api`中间件组中的路由，它提供了频率限制。这些路由都是无状态的，所以通过这些路由进入应用请求旨在通过令牌进行身份认证，并且不能访问会话状态。

`console.php`文件是定义所有基于闭包的控制台命令的地方。每个闭包都被绑定到一个命令实例并且允许和命令行 IO 方法进行简单的交互。尽管这些文件没有定义 HTTP 路由，但它也将基于控制台的入口点（路由）定义到应用程序中。

`channels.php`用来注册你的应用支持的所有的事件广播渠道的地方。

#### Storage 目录

`storage`目录包含编译的 Blade 模板、基于文件的会话和文件缓存、以及框架生成的其他文件。这个目录被细分成`app`、`framework`和`logs`三个子目录。`app`目录可以用来存储应用生成的任何文件。`framework`目录用来存储框架生成的文件和缓存。最后，`logs`目录包含应用的日志文件。

`storage/app/public`可以用来存储用户生成的文件，比如需要公开访问的用户头像。你应该创建一个`public/storage`的软链接指向这个目录。你可以直接通过`php artisan storage:link`命令来创建此链接。

#### Tests 目录

`tests`目录包含自动化测试文件。Laravel 已内置了[PHPUnit](https://phpunit.de/)的测试范例供你参考。每个测试类都应该以`Test`作为后缀。你可以使用`phpunit`或者`php vendor/bin/phpunit`命令来运行测试。

#### Vendor 目录

`vendor`目录包含你的[Composer](https://getcomposer.org/)依赖包。

## App 目录

应用程序的核心代码位于`app`目录内。默认情况下，这个目录位于命名空间`App`下，并由 Composer 按照[PSR-4 自动载入标准](http://www.php-fig.org/psr/psr-4/)来自动加载。

`app`目录包含了各种各样的目录，比如`Console`、`Http`和`Providers`等。其中`Console`和`Http`提供进入应用核心的 API 。HTTP 协议和 CLI 都只是应用交互的机制，实际上并不包含应用逻辑。也就是说，它们只是两种向应用发出命令的方法。`Console`目录里包含了所有的 Artisan 命令，`Http`目录包含了应用的控制器、中间件和请求。

当你通过 Artisan 提供的`make`命令来生成类时，会在`app`中生成各种各样的目录。例如，在执行 Artisan 命令`make:job`来生成任务类之前，`app/Jobs`目录都不会存在。

> {tip}`app`目录里的许多类都可以通过 Artisan 命令来生成。要查看可用的命令，只要在终端里运行`php artisan list make`命令即可。

#### Broadcasting 目录

`Broadcasting`目录包含应用程序的所有广播频道类。 这些类可以通过使用`make:channel`命令来创建。 默认情况下此目录是不存在的，在创建第一个频道类时将为你创建此目录。 要了解有关频道的更多信息，请查阅[事件广播](https://laravel-china.org/docs/laravel/5.6/broadcasting)文档。

#### Console 目录

`Console`目录包含了所有自定义的 Artisan 命令。这些命令可以通过`make:command`来生成。这个目录还包含了控制台内核，可以用来注册你的自定义 Artisan 命令和你定义的[计划任务](https://laravel-china.org/docs/laravel/5.6/scheduling)的地方。

#### Events 目录

`Events`目录默认是不存在的，它会在你运行 Artisan 命令`event:generate`或`make:event`时生成。`Events`目录存放了[事件类](https://laravel-china.org/docs/laravel/5.6/events)。可以使用事件来提醒应用其他部分发生了特定的操作，为应用提供了大量的灵活性和解耦。

#### Exceptions 目录

`Exceptions`目录包含了应用的异常处理器，也是应用抛出异常的好地方。如果想自定义记录或者渲染异常的方式，你就要修改此目录下的 Handler 类。

#### Http 目录

`Http`目录包含了控制器、中间件和表单请求。几乎所有的进入应用的请求的处理逻辑都被放在这里。

#### Jobs 目录

`Jobs`目录默认是不存在的，它会在你运行 Artisan 命令`make:job`时生成。这个目录存放了应用中的[队列任务](https://laravel-china.org/docs/laravel/5.6/queues)。应用的任务可以被推送到队列或者在当前请求的生命周期内同步运行。在当前请求期间同步运行的任务可以看做是一个「命令」，因为它们是[命令模式](https://en.wikipedia.org/wiki/Command_pattern)的实现。

#### Listeners 目录

Listeners 目录默认是不存在的，它会在你运行 Artisan 命令 event:generate 或 make:listener 时生成。Listeners 目录包含了用来处理[事件](https://laravel-china.org/docs/laravel/5.6/events)的类。事件监听器接收事件实例并执行响应该事件被触发的逻辑。例如，`UserRegistered`事件可能由`SendWelcomeEmail`监听器处理。

#### Mail 目录

`Mail`目录默认不存在，它会在你运行 Artisan 命令`make:mail`时生成。`Mail`目录包含应用所有的邮件发送类。邮件对象允许你将构建邮件的逻辑封装在可以使用`Mail::send`方法来发送邮件的地方。

#### Notifications 目录

`Notifications`目录默认不存在，它会在你运行 Artisan 命令`make:notification`时生成。`Notifications`目录包含应用发送的所有「事务性」通知，比如关于在应用中发生的事件的简单通知。Laravel 的通知功能抽象了通知发送，可以通过各种驱动（例如邮件、Slack、短信）发送通知，或是存储在数据库中。

#### Policies 目录

`Policies`目录默认不存在，它会通过运行 Artisan 命令`make:policy`来创建。`Policies`目录包含了应用的授权策略类。策略可以用来决定一个用户是否有权限去操作指定资源。更多详情可以查看[授权文档](https://laravel-china.org/docs/laravel/5.6/authorization)。

#### Providers 目录

`Providers`目录包含了应用的所有[服务提供器](https://laravel-china.org/docs/laravel/5.6/providers)。服务提供器通过在服务容器中绑定服务、注册事件、以及执行其他任务来为即将到来的请求做准备来启动应用。

在一个新的 Laravel 应用里，这个目录已经包含了一些服务提供器。你可以按照需要把自由添加自己的服务提供器到该目录。

#### Rules 目录

`Rules`目录默认不存在，它会在运行 Artisan 命令`make:rule`命令时被创建。`Rules`目录包含应用自定义验证规则对象。这些规则意在将复杂的验证逻辑封装在一个简单的对象中。

