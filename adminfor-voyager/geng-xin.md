修改composer.json

```
"tcg/voyager": "1.1" 改为 "tcg/voyager": "1.1.*"
```

下载数据库迁移文件 [https://github.com/the-control-group/voyager/tree/1.1/migrations](https://github.com/the-control-group/voyager/tree/1.1/migrations) ， 然后执行迁移更新操作

```
php artisan migrate
```

多角色

```
获取用户的主要角色
$user->role->name // Name of primary role

获取所有额外的角色
$user->roles() // gets all extra roles relationship
$user->roles()->get() // gets all extra as a collection

获得所有角色，包括主角和额外角色
$user->roles_all() // collection of all roles
```



