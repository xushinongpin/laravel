路由直接输出值的两种方法

```
Route::get('/', function () {
    $tasks = [
        'i',
        'l',
        'o',
        'v',
        'e'
    ];
    return view('welcome')->withTasks($tasks)->withFoo('foo')->withScript( '<script>alert(1)</script>');
    return view('welcome',[
        'tasks' => $tasks,
        'foo' => request('title'),
        'script' => '<script>alert(1)</script>',
    ]);
});
```



