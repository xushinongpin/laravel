首先必须引入：

```
Illuminate\Http\Request
```

您也可以使用all、input或query方法以数组形式检索所有输入数据：

```
all方法：
$request->all()

query方法：
$request->query()

input方法：
$request->input()
```

无论HTTP谓词如何，input 可用于检索用户输入：必须传参数否则返回null，比如 /a/b?name=test

```
$request->input('name')
```

第一个参数没有将返回默认值，比如 /a/b?name=test

```
input试玩写法
$request->input('name',"I'm spare tire")

query的写法
$request->query('name',"I'm spare tire")
```

处理包含数组输入的表单时，请使用“点”符号访问数组：

```
$name = $request->input('products.0.name');

$names = $request->input('products.*.name');
```



