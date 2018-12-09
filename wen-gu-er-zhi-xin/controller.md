生成控制器的两种方法

```
  php artisan make:controller TestController
或者
  php artisan make:controller TestController -r 【生成各个方法】

查看相关参数
  php artisan make:controller -h
  Description:
    Create a new controller class
  
  Usage:
    make:controller [options] [--] <name>
  
  Arguments:
    name                   The name of the class
  
  Options:
    -m, --model[=MODEL]    Generate a resource controller for the given model.
    -r, --resource         Generate a resource controller class.
    -i, --invokable        Generate a single method, invokable controller class.
    -p, --parent[=PARENT]  Generate a nested resource controller class.
        --api              Exclude the create and edit methods from the controller.
    -h, --help             Display this help message
    -q, --quiet            Do not output any message
    -V, --version          Display this application version
        --ansi             Force ANSI output
        --no-ansi          Disable ANSI output
    -n, --no-interaction   Do not ask any interactive question
        --env[=ENV]        The environment the command should run under
    -v|vv|vvv, --verbose   Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```



