```
$table->increments('id');
$table->string('name');
$table->string('email')->unique();
$table->string('password');
$table->string('wechat_nickname'); //用于存储微信呢称
$table->string('wechat_token'); //用于存储微信标识
$table->string('wechat_avatar');//用于存储微信头像
$table->integer('wechat_superior');//用于存储微信上级会员
$table->rememberToken();
$table->timestamps();
```



