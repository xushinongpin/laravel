第一步： 先注册服务

```
AppServiceProvider

public function register()
{
    //覆盖DataRow为例子
    Voyager::useModel('DataRow',\App\Models\DataRow::class);
}
```





[参考地址](https://docs.laravelvoyager.com/customization/overriding-files)

