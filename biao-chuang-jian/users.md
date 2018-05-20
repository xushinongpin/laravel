```
$table->increments('id');
$table->string('name');
$table->string('email')->unique();
$table->string('password');
$table->string('wechat_nickname');
$table->string('wechat_token');
$table->string('wechat_avatar');
$table->string('wechat_superior');
$table->rememberToken();
$table->timestamps();
```



