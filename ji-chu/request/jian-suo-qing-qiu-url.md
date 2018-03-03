url方法将返回没有查询字符串的URL，而fullUrl方法包含查询字符串

```

    public function c(Request $request){
        $url = $request->fullUrl();
        dump($url);
        $url = $request->url();
        dd($url);
    }
```

访问路径如果是 /a/b?key=1

fullUrl将打印出带有传来的参数 /a/b?key=1

url 将只打印到传来的路径 /a/b

