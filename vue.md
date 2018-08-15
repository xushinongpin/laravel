使用前先安装

```
npm install
```

启动

```
npm run dev   //每次更改Vue组件时都应该运行该命令
npm run watch  //命令来监视每次修改组件并自动重新编译它们
npm run watch-poll  //当您的文件发生更改时，Webpack不会更新
```

运行Artisan命令来构建应用程序的身份验证和注册

```
php artisan make:auth
```

引入测试

```
@extends('layouts.app')

@section('content')
    <example-component></example-component>
@endsection
```



