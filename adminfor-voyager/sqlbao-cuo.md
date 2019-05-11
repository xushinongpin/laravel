```
1   Doctrine\DBAL\Driver\PDOException::("SQLSTATE[42000]: Syntax error or access violation: 1059 Identifier name 'fack_translations_table_name_column_name_foreign_key_locale_unique' is too l
ong")
      G:\product\huarengame\vendor\doctrine\dbal\lib\Doctrine\DBAL\Driver\PDOStatement.php:119

  2   PDOException::("SQLSTATE[42000]: Syntax error or access violation: 1059 Identifier name 'fack_translations_table_name_column_name_foreign_key_locale_unique' is too long")
      G:\product\huarengame\vendor\doctrine\dbal\lib\Doctrine\DBAL\Driver\PDOStatement.php:117
```

部分解决方法一： 快速解决 方法： 不要加表前缀

部分解决方法二：

    SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key len
    gth is 1000 bytes (SQL: alter table `users` add unique `users_email_unique`(`email`))

    处理
    app/Providers/AppServiceProvider.php:25
    use Illuminate\Support\Facades\Schema;

    public function boot()
    {
        Schema::defaultStringLength(191);
    }

解决方案三【 主要解决方案 】

\[mysqld\] 下 添加 

```
default-storage-engine=InnoDB
```



