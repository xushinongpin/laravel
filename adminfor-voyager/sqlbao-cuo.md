```
1   Doctrine\DBAL\Driver\PDOException::("SQLSTATE[42000]: Syntax error or access violation: 1059 Identifier name 'fack_translations_table_name_column_name_foreign_key_locale_unique' is too l
ong")
      G:\product\huarengame\vendor\doctrine\dbal\lib\Doctrine\DBAL\Driver\PDOStatement.php:119

  2   PDOException::("SQLSTATE[42000]: Syntax error or access violation: 1059 Identifier name 'fack_translations_table_name_column_name_foreign_key_locale_unique' is too long")
      G:\product\huarengame\vendor\doctrine\dbal\lib\Doctrine\DBAL\Driver\PDOStatement.php:117

```

快速解决 方法： 不要加表前缀

