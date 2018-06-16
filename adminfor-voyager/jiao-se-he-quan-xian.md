Voyager开箱即带有角色和权限。每个用户都有一个拥有一组权限的角色。

在仪表板内部，您可以选择添加，编辑或删除当前的角色。另外，当您单击编辑特定角色时，您可以指定BREAD权限。

1.0版本中的新功能，我们已将Voyager的授权系统更改为更符合Laravel！这意味着您可以通过以下方式检查权限：

```
// via user object
$canViewPost = $user->can('read', $post);
$canViewPost = Auth::user()->can('read', $post);

// via controller
$canViewPost = $this->authorize('read', $post);
```

您也可以选择使用Voyager外观并将权限作为字符串传递：

```
$canBrowsePost = Voyager::can('browse_posts');
$canViewPost = Voyager::can('read_posts');
$canEditPost = Voyager::can('edit_posts');
$canAddPost = Voyager::can('add_posts');
$canDeletePost = Voyager::can('delete_posts');
```

无论用户是否具有该特定权限，每个检查的值都会返回一个布尔值。但是，如果用户没有特定权限，您可能希望抛出禁止的异常。这可以使用canOrFail方法完成：

```
Voyager::canOrFail('browse_admin');
```

开箱即用，您可以默认使用一些权限：

* `browse_database`: 用户是否可以浏览Voyager数据库菜单部分。
* `browse_admin`: 用户是否可以浏览Voyager管理面板。

* `browse_bread`: 用户是否可以浏览Voyager BREAD菜单部分。
* `browse_media`: 用户是否可以浏览Voyager媒体部分。
* `browse_menu`: 用户是否可以浏览Voyager菜单部分。
* `browse_settings`: 用户是否可以浏览Voyager设置部分。
* `read_settings`: 用户是否可以查看或查看特定设置。
* `edit_settings`: 用户是否可以编辑特定设置。
* `add_settings`: 用户是否可以添加新设置。
* `delete_settings`: 用户是否可以删除特定的设置。



