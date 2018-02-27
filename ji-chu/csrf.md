##### 方法一：用 @csrf 将会自动生成 input隐藏表单提交csrf

```
<form method="POST" action="/profile">
    @csrf
    ...
</form>
```

##### 方法二：

```
html的请求标头
<meta name="csrf-token" content="{{ csrf_token() }}">

jQuery的获取方法
$.ajaxSetup({
    headers: {
        'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
    }
});
```

### 表单提交需要的csrf验证，如果在某情况下不需要csrf的验证，那么就需要另外的授权了

```
打开 /app/Http/Middleware/VerifyCsrfToken.php 添加到 $except，
比如：


    protected $except = [
        'a',
        'b',
    ];
```

  


