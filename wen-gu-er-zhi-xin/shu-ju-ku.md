.env配置好后

```
php artisan migrate //将表生成到数据库

php artisan
 其他执行参考
  migrate
  migrate:fresh         Drop all tables and re-run all migrations
  migrate:install       Create the migration repository
  migrate:refresh       Reset and re-run all migrations
  migrate:reset         Rollback all database migrations
  migrate:rollback      Rollback the last database migration
  migrate:status        Show the status of each migration
```

make:migration 【 生成表框架， database/migrations 里面 】

```
Schema::create ......  创建表

Schema::table  ......  更新表
```



