文档地址 [https://voyager.readme.io/docs/menus](https://voyager.readme.io/docs/menus)

创建并配置菜单后，您可以在应用程序中轻松实现该菜单。假设我们有一个名为main的菜单。在任何视图文件的内部，我们现在可以通过使用以下代码输出菜单

```
menu('main');
```

这将输出你的菜单在一个无风格的无序列表中。如果您使用引导程序来设置您的Web应用程序风格，则可以将第二个参数传递给菜单显示方法，告诉它您想要使用引导程序样式来设置菜单风格，如下所示：

```
menu('main', 'bootstrap');
```



