修改composer.json

```
"tcg/voyager": "1.1" 改为 "tcg/voyager": "1.1.*"
```

下载数据库迁移文件 [https://github.com/the-control-group/voyager/tree/1.1/migrations](https://github.com/the-control-group/voyager/tree/1.1/migrations) ， 然后执行迁移更新操作

```
php artisan migrate
```



