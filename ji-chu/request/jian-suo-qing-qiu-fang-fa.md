method 方法将返回请求的HTTP动词。您可以使用isMethod方法来验证HTTP谓词是否与给定的字符串匹配：

```

    public function c(Request $request){
        $method = $request->method();
        if ($request->isMethod('post')) {
            dd('is post method request');
        }
        dd('is get method request');
    }
```



