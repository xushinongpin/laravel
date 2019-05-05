# 前端模板

```
1. 被替换位置   @yield('title', '默认数据')
2. 引入文件方法 @include('layouts._header')
3. 引入框架vue的js/css方法 {{ mix('js/app.js') }} / {{ mix('css/app.css') }}
4. 引入主框架   @extends('layouts.app')
5. 替换位置数据 @section('title', '首页') ... @section('content') ... @stop //最终需要一个结束stop即可
6. 判断是否已登录 【 未登录@guest ...未登录显示东西 ... @else ...已登录东西 ... @endguest 】
7. 遍历 @foreach($aas as $aa)  {{ $aa->bb }}  @endforeach
```

# 路由

```
1. 路由末尾记得添加 ->name('xxx'); 这样有有利于固定地址 模板调用 {{ route('xxx') }}
2. 权限 ->middleware('verified'); 必须邮箱验证
3. auth 必须登录权限
```



